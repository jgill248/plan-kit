---
description: Generate per-feature spec stub files for the Spec Kit and write them to plan/spec-feed/*.md.
---

The user input to you can be provided directly by the agent or as a command argument - you MUST consider it before proceeding with the prompt (if not empty).

User input:

$ARGUMENTS

Goal: For roadmap items slated for near-term delivery, create minimal, structured spec stubs ready to be expanded by the Spec Kit.

Writes: plan/spec-feed/[NNN-<slug>.md]

Gates:
- Require plan/roadmap.md with at least one phase containing items. If missing, instruct user to run /roadmap first.

Execution steps:
1. Load plan/roadmap.md; select items in the earliest phase(s) or as limited by $ARGUMENTS (e.g., count=3).
2. For each selected item, create a new file at plan/spec-feed/ using the next sequential number (001, 002, ...), without overwriting existing files.
3. Use this stub template:
   - Frontmatter (title, created)
   - ## Context & Problem
   - ## Goals & Non‑Goals
   - ## User Stories
   - ## Functional Requirements
   - ## Non‑Functional Requirements
   - ## Data & Interfaces (API/Events)
   - ## Acceptance Criteria
   - ## Open Questions
4. Report created file paths and suggest running `/specify` to expand one into a full feature spec.

Behavior rules:
- Non-destructive: never overwrite or delete existing files; only create new ones.
- Use short, consistent headings and placeholders; avoid narrative.

Context: $ARGUMENTS


