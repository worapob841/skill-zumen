# Decision record — {{topic}} ({{YYYY-MM-DD}})

**Format:** zumen interview (`/zumen`). One question at a time, each with a recommended option; the user picked.
**Scope:** {{what this record decides + who owns it · greenfield or existing-repo · which phase(s) it scopes}}.

<!-- EXTEND mode, if this overturns an earlier call, add:
**Supersedes:** [`decisions/{{old-file}}.md`](./{{old-file}}.md) Q{{n}} — {{what changed and why}}. -->

---

## Q1 — {{question}}

**Why asked:** {{the rationale — what was ambiguous or load-bearing, with evidence from code/docs where relevant (cite file:line in existing-repo mode)}}.

| Option | Trade-off |
|---|---|
| **{{recommended option}}** ⭐ | {{trade-off}} |
| {{alternative}} | {{trade-off}} |
| {{alternative}} | {{trade-off}} |

**Selected: {{chosen option}}** — {{reasoning + the consequences this commits us to}}.

## Q2 — {{question}}

**Why asked:** {{…}}.

| Option | Trade-off |
|---|---|
| **{{recommended}}** ⭐ | {{trade-off}} |
| {{alternative}} | {{trade-off}} |

**Selected: {{choice}}** — {{reasoning}}.

<!--
One QN block per decision that had REAL alternatives — from BOTH the requirements grill (Stage 1)
and the architecture pass (Stage 2). Exactly one ⭐ per table (the recommended option). A decision
with no genuine alternative isn't a QN — state it as a fact in architecture.md instead.
-->

---

## Where the decisions landed

- [`task.md`](../task.md) — {{phases/subtasks these decisions created or changed}}
- [`architecture.md`](../architecture.md) — {{sections}}
- [`product.md`](../product.md) — {{sections}}
- {{Code — file paths that implement these decisions (existing-repo mode only)}}
- This record is the canonical "why" for {{topic}}.
