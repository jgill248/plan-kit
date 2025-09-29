---
title: Features and User Stories
---


Overview

- This document lists the initial feature set and user stories for the first release. Each story includes a brief acceptance criterion.

Core Features

1. User management

   - As a user, I can register an account, log in, and log out.

   - Acceptance: Users can create an account and authenticate; JWT tokens issued by API.

2. Profile management

   - As a user, I can update my profile information and upload an avatar.

   - Acceptance: Changes persist in DB; avatar upload stores file reference.

3. Simple resource CRUD (e.g., Notes)

   - As a user, I can create, read, update, and delete notes tied to my account.

   - Acceptance: Notes are scoped to user and accessible via API and frontend.

4. Authorization rules

   - As the system, only the owner can modify their resources.

   - Acceptance: API returns 403 for unauthorized modifications.

Non-Functional Requirements

- Performance: p95 API latency < 200ms under baseline test load

- Security: Passwords hashed with bcrypt; JWTs signed with RS256

- Observability: Request logs and basic metrics (requests/sec, error rate)

Edge Cases

- Rate limits for create endpoints

- Handling partial failures during file upload


Roadmap & Prioritization

- Phase 1: Auth + User CRUD + DB schema

- Phase 2: Notes CRUD + UI integration

- Phase 3: Polish, tests, and deployment
