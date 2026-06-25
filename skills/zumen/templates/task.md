# {{Project name}} — Execution Plan

**Cadence:** {{team size + pace, e.g. "solo, ~6 weeks" or "small team (3–5 full-stack), ~24 weeks"}}.
**Format:** each phase has a goal, deliverables, subtasks (checkboxes), dependencies, complexity (S/M/L per subtask).
**Complexity legend:** S = ≤1 day · M = 2–4 days · L = 5+ days.

> {{Sequencing note — which phases are strictly sequential, which can run in parallel, and what threads through nearly every phase (auth, infra, i18n, …).}}

---

## Phase 0 — {{Title}} ({{timeline, e.g. Weeks 1–2}})
**Goal:** {{one-sentence outcome}}.
**Deliverables:** {{concrete, verifiable end-states — what runs / renders / passes when this phase is done}}.
**Dependencies:** none.

- [ ] {{Subtask}} — **{{S|M|L}}**
- [ ] {{Subtask}} — **{{S|M|L}}** _({{optional annotation: scope note, decision-record ref, blocked-by}})_

## Phase 1 — {{Title}} ({{timeline}})
**Goal:** {{one-sentence outcome}}.
**Deliverables:** {{…}}.
**Dependencies:** Phase 0.

- [ ] {{Subtask}} — **{{S|M|L}}**
- [ ] {{Subtask}} — **{{S|M|L}}**

<!--
Add phases until every deliverable implied by product.md's scope is covered.
Sequence by dependency: foundation → data model → core flows → integrations → polish → hardening.
Each subtask carries an S/M/L rating. Annotate in _(italics in parens)_ when there's scope nuance,
a decision-record citation, or a blocked-by note — mirror the existing repo's annotation style.
EXTEND mode: continue numbering from the highest existing phase; never renumber existing phases.
If the host repo's CLAUDE.md enforces a cross-cutting rule (e.g. "update en.json + th.json on any
UI string"), add the corresponding subtask to every phase it applies to.
-->
