---
title: DevOps, Local Development, and CI
---


Docker Compose

- The repository root will contain a `docker-compose.yml` that defines:

  - `postgres` service (image: postgres:15)

  - `pgadmin` or admin tool (optional)

  - `db-migrations` helper service (optional) to run migrations

Environment

- Use `.env` files with safe defaults for local development and reference them in `docker-compose.yml`

- Keep secrets out of the repository; provide a `.env.example` with variables

CI/CD

- Use GitHub Actions (or other) with workflows:

  - `ci.yml`: installs dependencies, runs lint, unit tests, runs migrations against a test DB container, runs integration tests

  - `release.yml`: builds images, tags, and optionally publishes to registry

Testing

- Use a disposable Postgres container in CI for integration tests; run migrations before tests

- Use `nx` affected tests to limit test surface in PRs

Logging & Observability

- Use structured JSON logging from the API

- Provide a basic Prometheus-compatible metrics endpoint (optional)

Local Developer Quickstart

1. Install Node 18+, Docker

2. Copy `.env.example` → `.env`

3. docker-compose up -d

4. npm install

5. nx serve api

6. nx serve frontend