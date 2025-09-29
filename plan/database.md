---
title: Database Schema & Migrations
---


Overview

- PostgreSQL will be used as the primary relational datastore. Migrations will be managed with `knex`, `typeorm`, or `prisma` (recommendation: Prisma for DX and TypeScript-first models).

Entities (initial)

- `users`:

  - id (uuid, PK)

  - email (unique)

  - password_hash

  - display_name

  - avatar_url

  - created_at, updated_at

- `notes`:

  - id (uuid, PK)

  - user_id (FK -> users.id)

  - title

  - body

  - metadata (jsonb)

  - created_at, updated_at

Indexes & Constraints

- Unique index on `users.email`

- FK constraint `notes.user_id` -> `users.id` ON DELETE CASCADE

Migration Strategy

- Use Prisma Migrate or TypeORM migrations committed to version control

- Local development: run `docker-compose up -d` then `npm run migrate` which applies migrations to the Postgres container

- CI: run migrations in a disposable test DB before running integration tests

Seeding

- Provide optional seed scripts for demo users and sample notes

Backups & Production

- Recommend scheduled logical backups (pg_dump) and WAL archiving as a long-term plan
