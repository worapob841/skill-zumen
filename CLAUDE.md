# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

This repo is a **single Claude Code skill**, `zumen` — the only entry (so far) under `agents-skill-catalog/`. It is **prompt/content engineering, not application code**: every file is Markdown that an *agent reads and executes* at runtime. There is no source code, package manifest, or build/test/lint tooling, and it is not a git repo.

The `zumen` skill plans projects: it interviews the user one question at a time, co-designs an architecture, phases the work, writes a `plans/` doc bundle, and then **stops before any implementation**. Working here means *maintaining the skill's instructions and output templates* — not running them.

> **Two different CLAUDE.md files are in play.** *This* one guides editing the skill. The skill's own text repeatedly says to "conform to the host repo's CLAUDE.md" — that refers to a *different* CLAUDE.md in whatever project the skill is later run inside. Don't conflate them; nothing in this repo should bake in another project's specifics.

## Structure and how the pieces relate

Three layers; understanding the skill means seeing how they feed each other:

| File(s) | Role |
|---|---|
| `SKILL.md` | The **driver**. Frontmatter (`name` / `description`) is the activation trigger; the body defines a 6-stage flow (Stage 0 detect → 1 grill → 2 architecture → 3 phasing → 4 write → 5 review → 6 hard-gate) plus a `digraph` that mirrors it. |
| `references/interview-checklist.md` | The **decision tree** the Stage-1 grill walks, branch by branch (A problem/users → K success/phasing), dependencies-first. |
| `templates/*.md` | The **pinned output shapes**. Stage 4 *copies* these and fills them — structure is never free-handed from memory. |

Data flow: `SKILL.md` orchestrates → the checklist drives the interview → the templates become the output bundle:

- `templates/product.md` → `plans/product.md` (who / why / what)
- `templates/architecture.md` → `plans/architecture.md` (how)
- `templates/task.md` → `plans/task.md` (phases + S/M/L subtasks)
- `templates/decision-record.md` → `plans/decisions/YYYY-MM-DD-<topic>.md` (the interview; append-only)
- `templates/interview-scratchpad.md` → `plans/.zumen-<topic>-scratch.md` (resumability checkpoint; *not* part of the deliverable)

**Key non-obvious point:** the relative links *inside* the templates (`./architecture.md`, `../task.md`, `decisions/…`) describe the topology of the **generated `plans/` bundle**, not this repo. They are correct as written and resolve once a template is copied into `plans/`. Don't "fix" them to point at this repo's `templates/`.

## Invariants any edit must preserve

These span multiple files and are *why* the skill works — break one and behavior silently degrades:

- **Domain-neutral.** Templates and references carry no project's specifics (no hard-coded domain terms, stacks, or house rules). The skill adapts to a host repo at runtime; it must ship generic.
- **The HARD-GATE is absolute.** `zumen` ends at approved docs — it never writes code, scaffolds, migrates, installs deps, or invokes an implementation skill (`SKILL.md` Stage 6). Loosening this changes the skill's contract.
- **CREATE vs EXTEND, and append-only decisions.** EXTEND updates the three standing docs surgically, **continues** phase numbering (never renumbers), and **always appends a new** dated decision record (never overwrites one). A superseded decision gets a `Supersedes:` line + a `~~struck~~ **Resolved (date):**` amendment — not deletion.
- **One question per turn** in the grill; **every question leads with a recommended answer + a one-line why**.
- **Copy templates; don't free-hand structure.** To change a doc's shape, edit the *template*, not the prose that tells the agent to reconstruct it.
- **Real date, every time** — filenames and citations depend on it; never a guessed date.

## Cross-file coupling — keep these in sync when editing

The same contracts are intentionally restated in several places. Touch one, audit the rest:

- The **4-doc bundle definition** appears in `SKILL.md`'s "What it produces" table, the "Conversation → doc mapping" table, Stage 4, and `interview-scratchpad.md`. Adding/removing a doc means updating all of them *plus* the matching `templates/` file.
- The **stage list and the `digraph`** in `SKILL.md` must stay consistent with each other.
- `SKILL.md` **hardcodes paths** to every `templates/*.md`, to `references/interview-checklist.md`, and to sibling skills (e.g. `../grill-me/SKILL.md`, assuming the standard `.claude/skills/<name>/` install layout). Renaming or moving a file requires grep-updating `SKILL.md`.

## Conventions

- `{{double-brace}}` = fill-in placeholder in templates; Stage 5 scans for any leftover `{{…}}` or `TODO` before the bundle is considered done.
- Decision-record option tables: exactly **one `⭐`** marks the recommended option.
- Complexity legend: **S = ≤1 day · M = 2–4 days · L = 5+ days** (per subtask in `task.md`).
- Default output dir is `plans/`; respect an established alternative (`docs/`, `design/`) if a host repo already uses one.

## "Building" and validating

Nothing to build or run. The closest thing to a test is the skill's own Stage-5 self-review applied to *your* edits: scan for leftover `{{…}}` / `TODO`, confirm every cross-reference resolves, and verify the stage list, the `digraph`, and the doc-mapping tables still agree. After renaming any file, grep `SKILL.md` for stale paths.
