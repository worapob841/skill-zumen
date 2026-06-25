# zumen

A [Claude Code](https://claude.ai/code) **skill** that turns a fuzzy idea into a crystal-clear, well-architected, phased plan — then writes it out as a `plans/` documentation bundle and **stops before any implementation**.

`zumen` (図面, Japanese for *plan / technical drawing*) interviews you one question at a time to lock requirements, proposes and compares 2–3 architecture approaches with a recommendation, breaks the work into phases with S/M/L complexity ratings, and emits four cross-linked docs:

| Doc | Holds |
|---|---|
| `plans/product.md` | WHO / WHY / WHAT — users, scope, non-goals, success criteria |
| `plans/architecture.md` | HOW — tech-stack table, components, domain model, APIs / auth / storage |
| `plans/task.md` | WHEN — phases with goal / deliverables / dependencies + S/M/L subtasks |
| `plans/decisions/YYYY-MM-DD-<topic>.md` | The interview itself — every recommended question + chosen option + why |

It detects and reuses an existing codebase's stack before asking, works greenfield too, and **extends** an existing `plans/` folder instead of overwriting it.

## Install

Drop the skill into a project (`.claude/skills/`) or your user config (`~/.claude/skills/`).

**Via npx** ([degit](https://github.com/Rich-Harris/degit) — copies the `skills/zumen/` subdir):

```bash
# project-local (this repo / project only)
npx degit worapob841/skill-zumen/skills/zumen .claude/skills/zumen

# or user-global (available in every project)
npx degit worapob841/skill-zumen/skills/zumen ~/.claude/skills/zumen
```

**Manual (git):**

```bash
git clone https://github.com/worapob841/skill-zumen.git
cp -r skill-zumen/skills/zumen ~/.claude/skills/zumen
```

Any installer that copies a GitHub subdirectory works — the part that matters is the destination layout: `.claude/skills/zumen/SKILL.md`. Reload Claude Code afterward so it discovers the skill.

## Use

Invoke explicitly with `/zumen`, or just describe what you want to build — it triggers on *"plan / spec / scope this project"*, *"design the architecture / pick a stack"*, *"break this into phases"*, or *"interview / grill me about requirements"*.

zumen runs a six-stage flow — detect terrain → requirements interview → architecture proposal → phasing → write the bundle → **hard stop** — pausing for your approval at each gate. It plans; it never writes code. Handing off to implementation is a separate, fresh invocation.

## Repository layout

```
skills/
  zumen/
    SKILL.md                  # the skill: triggers + the 6-stage flow
    references/
      interview-checklist.md  # the requirements decision tree the grill walks
    templates/                # output doc shapes — copied, then filled
      product.md  architecture.md  task.md
      decision-record.md  interview-scratchpad.md
CLAUDE.md                     # guidance for *developing* this skill (not shipped in installs)
```

## Developing

See [`CLAUDE.md`](./CLAUDE.md) for the skill's architecture, the invariants any edit must preserve, and the cross-file coupling to keep in sync.
