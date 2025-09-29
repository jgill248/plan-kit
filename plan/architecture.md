---
title: Architecture & Workspace Layout
---
 
Overview

- We will use NX to manage a TypeScript monorepo. The `src/` directory will contain `apps/` and `libs/` following NX conventions. Apps will be:

  - `apps/frontend` — React application (Vite or Next.js depending on SSR needs; default: Vite for simplicity)

  - `apps/api` — NestJS REST API (TypeScript)

Libraries

- `libs/shared` — DTOs, types, and shared utils used by both frontend and backend

- `libs/db` — database access layer, entities, and migration utilities

- `libs/ui` — shared UI components (optional)

Tooling

- Node 18+; TypeScript; ESLint; Prettier; Jest/Playwright

- NX task orchestration for building, serving, linting, and testing

Source layout (top-level)

```text
src/
├── apps/
│   ├── frontend/
│   └── api/
└── libs/
    ├── shared/
    ├── db/
    └── ui/
```

Rationale

- Monorepo enables sharing DTOs and types between frontend and backend reducing duplication and integration errors.


 - NX provides caching, task orchestration, and efficient builds for large workspaces.

CI/CD note

 - CI pipelines should run tests in parallel per app and use NX affected graph to minimize work.

