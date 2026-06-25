# {{Project name}} — System Architecture

**Status:** {{e.g. Draft v1 (pre-implementation), drafted {{YYYY-MM-DD}} via /zumen}}
**Owner:** {{team / person}}
{{**Source design:** {{design link, e.g. Figma fileKey}} — keep this line only if a design reference exists}}

## 1. Product summary

> See [`product.md`](./product.md) for the full who/why/what. Brief summary below.

{{2–4 sentences: the product in technical-summary form — what it is and the shape of the system.}}

## 2. Tech stack

| Layer | Choice | Why |
|---|---|---|
| {{Runtime}} | **{{choice}}** | {{justification — tie back to a requirement}} |
| {{Framework}} | **{{choice}}** | {{why}} |
| {{Datastore}} | **{{choice}}** | {{why}} |
| {{… add the rows that apply: styling, ORM, auth, validation, background jobs, object storage, search, payments, hosting/infra, CI/CD, testing}} | **{{choice}}** | {{why}} |

### Why {{the most contested choice}} over alternatives
{{Short justification for the 1–2 genuinely-contested choices. Each of these maps to a QN in the decision record.}}

## 3. System architecture

### High-level component diagram

```
{{ASCII diagram: users → entrypoint → app/services → datastores. Only draw boxes that actually exist.}}
```

### Process / service inventory

| Service | Location | Responsibility | Scaling |
|---|---|---|---|
| {{service}} | {{repo / path}} | {{what it owns}} | {{how it scales}} |

### Repository layout

```
{{directory / package tree and what each holds. For a monorepo, note which workspace this work targets.}}
```

## 4. Domain model

{{The core entities and their relationships — a schema sketch in whatever fits the stack (Prisma model / SQL DDL / type defs) + the key invariants that must always hold.}}

## 5. API / interface design

{{The internal and any public interfaces. Endpoints or actions, the auth on each, request/response shapes for the load-bearing ones. Mark "N/A — {{reason}}" if there is no API surface.}}

## 6. Authentication & authorization

{{Who authenticates and how; roles; where enforcement lives. "N/A — {{reason}}" if not applicable.}}

## 7. Storage

{{Object/file storage, caching, anything beyond the primary datastore. "N/A — {{reason}}" if not applicable.}}

<!--
Add, rename, or drop sections to fit the project (a CLI needs no auth section; a data pipeline
needs an ingestion/lineage section). Every heading either gets real content or an explicit
"N/A — <reason>". No empty headings, no {{placeholders}} left behind after Stage 4.
In an existing repo, REUSE the established stack — only the genuinely-new axes the feature forces
get a fresh decision; don't re-litigate settled choices.
If the host repo's CLAUDE.md declares house rules (money type, i18n, naming), conform to them here.
-->
