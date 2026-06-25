# zumen interview checklist — the decision tree

The ordered branch map the grill (Stage 1) walks. **Dependencies first** — a branch that
constrains later branches comes earlier (you can't choose a payment provider before confirming
money is even in scope). **Explore, then ask only what's still open** — skip any branch the
codebase or the user's request already answers, and cite the file when you reuse a settled choice.
Not every project needs every branch; prune ruthlessly (YAGNI).

For each open branch: ask ONE question, lead with a recommended answer + a one-line why, prefer
A/B/C options when the space is small. Log each resolution to the scratchpad.

## A. Problem & users — always first; everything hangs off this
- What is the user actually trying to build? One sentence, in their words.
- Who uses it? (audiences / personas) What does each expect?
- What is the single most important outcome? (the headline success criterion)
- Working project name? (greenfield — doc titles need it)

## B. Scope & non-goals — bound the work before designing it
- What's explicitly IN this slice vs deferred to later?
- What are the non-goals — the tempting things we are deliberately NOT doing?
- Is this really one project, or several independent subsystems? (if several → decompose, zumen the first slice)
- Existing system this replaces or extends? (confirms greenfield vs brownfield)

## C. Shape of the thing — what kind of system
- Surface: web app / HTTP API / CLI / library / long-running service / worker / mobile / data pipeline?
- Interactive UI? If so, is there a design reference (Figma / mockup)?
- Real-time, batch, or request-response?
- Expected scale at launch and ~a year out (rough order of magnitude — drives datastore + infra).

## D. Data — the spine most decisions hang off
- Core entities and how they relate.
- Source(s) of data — user-entered, imported, third-party, generated?
- Persistence shape: relational / document / key-value / blob / search / none?
- Consistency vs availability sensitivity; any reporting / analytics needs.

## E. Money & compliance — only if relevant; GATE before asking detail
- Is money in scope at all? If NO → skip the rest of E.
- Who pays whom, for what, when? (one-time / subscription / per-use / marketplace split)
- Regulatory / privacy constraints (PII, payments licensing, data residency, age-gating)?

## F. Stack (greenfield) OR reuse-check (existing repo)
- Existing repo: what does the code already pin — language, framework, ORM, infra? REUSE it unless
  the feature genuinely forces a new tool; cite the file (e.g. `package.json:23`).
- Greenfield: language + framework + datastore + key libraries. Recommend a coherent default stack
  for the shape (from C) and the team's familiarity; let the user override.
- Hard tech constraints (must run on X, must integrate with Y, team only knows Z)?

## G. Integrations & external services
- Third-party APIs/services this depends on (auth provider, payments, email, storage, LLM, …)?
- Build vs buy for each non-core capability.

## H. Auth & access
- Who authenticates, and how (none / sessions / OAuth / API keys / SSO)?
- Roles & permissions — what can each role do?

## I. Infra & delivery
- Where does it run (local / single VM / container host / serverless / k8s)?
- Deploy story: CI, environments, how a change ships to production.
- Background jobs / queues / scheduled work?

## J. Non-functional
- i18n / localization? If the host repo enforces it (see its CLAUDE.md), conform.
- Observability, error handling, testing expectations.
- Security posture, rate-limiting, abuse surface.

## K. Success & phasing — closes the loop, feeds task.md
- What does v1 / "done" actually include vs fast-follow?
- Natural milestone boundaries — what's the smallest shippable first slice?
- Hard deadlines or sequencing constraints?

---

When no open branch still blocks the architecture pass, **STOP grilling**, summarize the locked
requirement set back to the user, and get an explicit "yes, that's it" before entering Stage 2.
