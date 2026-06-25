# {{Project name}} — Product Context

**Status:** {{e.g. v1, drafted {{YYYY-MM-DD}} via /zumen}}.

This document is the canonical "why/who/what" for the project. [`architecture.md`](./architecture.md) covers HOW we build, [`task.md`](./task.md) covers WHEN. Read this first before either.

---

## What is this?

{{One or two paragraphs in plain language: what it does, for whom, the core value. If there are distinct product types or surfaces, a small table earns its place.}}

## Who is this for?

{{The target users. Use a ### subsection per distinct audience. For each: who they are, what they expect, concrete examples. If the request optimizes for more than one side, say how you avoid sacrificing one for the other.}}

### {{Audience A}}
- {{who they are}}
- {{what they expect}}

### {{Audience B}}
- {{who they are}}
- {{what they expect}}

## {{Market — or "Scope" for an internal tool/feature}}

{{For a product: market, geography, positioning, who the competition is. For an internal feature: the scope boundary — which surface it touches, who inside the org it serves, what it explicitly leaves to other systems.}}

## {{Value / Revenue model — KEEP ONLY IF money is in scope; delete otherwise}}

{{How the thing creates or captures value. For a commercial product: pricing, who pays, how money flows. Cite the decision record for any pricing/monetization call.}}

## Differentiator

{{Why this over the alternatives / the status quo. What it does that others don't.}}

## Explicit non-goals (for now)

{{What we are deliberately NOT building — the list that prevents scope creep.}}
- {{non-goal}}
- {{non-goal}}

## Success looks like

{{Concrete, ideally measurable, success criteria. How we'll know it worked.}}

## Decisions this document commits us to

{{The load-bearing product decisions, each with a one-line citation to the decision record.}}
- {{decision}} (decided {{YYYY-MM-DD}} — see [`decisions/{{file}}.md`](./decisions/{{file}}.md) Q{{n}}).

## Open questions to revisit

{{Unresolved questions, plus any assumed defaults from a compressed/skipped interview (list them so they're visible and revisable — never silently invent). Use the amendment pattern when one is resolved:}}
- {{open question}}
- ~~{{resolved question}}~~ **Resolved ({{YYYY-MM-DD}}):** {{resolution}}.
