---
description: Convert prioritized items into a phased roadmap and write to plan/roadmap.md.
---

The user input to you can be provided directly by the agent or as a command argument - you MUST consider it before proceeding with the prompt (if not empty).

User input:

$ARGUMENTS

Goal: Transform the prioritized backlog into a sequenced set of phases with objectives, deliverables, and gating criteria.

Writes: plan/roadmap.md (create if missing; overwrite section content while preserving frontmatter)

Gates:
- Require plan/priorities.md with a ranked backlog. If missing, instruct user to run /prioritize first.

Execution steps:
1. Load plan/priorities.md; take the ranked items and any dependency notes.
2. Define phases (e.g., Phase 0/1/2) with clear goals and acceptance/gating criteria.
3. Assign items to phases based on dependencies, capacity assumptions, and objectives.
4. Write plan/roadmap.md with:
   - Frontmatter preserved
   - ## Overview
   - ## Phase Plan (Phase 0, Phase 1, Phase 2 ...)
   - ## Milestones & Gating
   - ## Timeline Assumptions
5. Report completion with path and a summary of each phase. Suggest next command: /handoff.

Behavior rules:
- Keep phases outcome-oriented; avoid technical minutiae.
- Ensure each phase has a testable exit criterion.

Context: $ARGUMENTS


