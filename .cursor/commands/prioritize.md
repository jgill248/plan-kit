---
description: Prioritize features/initiatives based on constraints, goals, and validation scores; write to plan/priorities.md.
---

The user input to you can be provided directly by the agent or as a command argument - you MUST consider it before proceeding with the prompt (if not empty).

User input:

$ARGUMENTS

Goal: Produce a ranked backlog that balances impact, effort, and constraints using validation scores and any additional inputs.

Writes: plan/priorities.md (create if missing; overwrite section content while preserving frontmatter)

Gates:
- Require plan/validation.md with scores. If missing, instruct user to run /validate first.

Execution steps:
1. Load plan/validation.md; collect WeightedScore and notes per idea.
2. If provided in $ARGUMENTS, accept constraints (e.g., quarter capacity, critical dependencies) and objectives (e.g., activation, retention).
3. Compute priority using a simple model (e.g., Score / Effort or RICE) while honoring constraints and dependencies.
4. Write plan/priorities.md with:
   - Frontmatter preserved
   - ## Method & Inputs
   - ## Ranked Backlog (table: Rank | Item | Score | Effort | Confidence | Notes)
   - ## Now / Next / Later
   - ## Risks & Dependencies
5. Report completion with path and the top 5 items. Suggest next command: /roadmap.

Behavior rules:
- Explicitly state assumptions (effort, confidence) when not provided.
- Keep ranking deterministic given the same inputs.

Context: $ARGUMENTS


