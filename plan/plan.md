---
title: High-level plan for NX monorepo with React, NestJS, and PostgreSQL
created: 2025-09-26
---


This repository will be organized as an NX workspace under `src/` and will contain a React frontend, a NestJS backend API, and a PostgreSQL database coordinated via `docker-compose.yml` at the repository root. The plan is split into several concise companion documents (architecture, features, database, devops) that capture the details for each area while keeping `plan.md` a high-level overview.

Goals

- Establish a maintainable monorepo using NX
- Deliver a production-ready default project layout for frontend, backend, and database
- Provide reproducible local development via Docker Compose
- Enforce TDD and CI checks by default

Milestones (high-level)

- M1: Workspace scaffolding (NX workspace, src layout, root tooling)
- M2: API + DB baseline (NestJS app, migrations, db container)
- M3: Frontend baseline (React app, example page, API integration)
- M4: Tests & CI (unit, integration, contract tests, Dockerized test DB)
- M5: Polish & docs (quickstart, environment docs, observability)

Deliverables

- `plan/architecture.md` — NX workspace layout and rationale
- `plan/features.md` — feature list, user stories, and acceptance criteria
- `plan/database.md` — schema overview, migration strategy, and seeds
- `plan/devops.md` — `docker-compose` definitions, env conventions, CI notes
- `docker-compose.yml` (repo root) — Postgres service and helper tooling

Constraints & Assumptions

- Development platform: Node 18+ (LTS), Docker for local development
- Primary languages: TypeScript for frontend and backend
- Database: PostgreSQL 15+
- The `src/` directory will contain all source code and NX apps/libs

Next steps

1. Review and approve high-level plan
2. Generate NX workspace and create `apps/frontend`, `apps/api`, `libs/`

3. Wire up docker-compose and initial migration tooling
