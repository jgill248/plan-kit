---
description: Generate multiple product ideas from a problem/opportunity statement and write them to plan/ideation.md.
---

The user input to you can be provided directly by the agent or as a command argument - you MUST consider it before proceeding with the prompt (if not empty).

User input:

$ARGUMENTS

Goal: Produce a breadth-first set of concrete product ideas derived from a clear problem/opportunity statement. Each idea should be concise and testable.

Writes: plan/ideation.md (create if missing; append new session if it exists)

Gates:
- If the problem/opportunity statement is empty, abort and request a 1–2 sentence statement (<=50 words).

Execution steps:
1. Parse the problem/opportunity statement from $ARGUMENTS. If empty, stop with an instructional message.
2. Derive constraints and success goals (from existing plan files if present: plan/plan.md, plan/features.md) and note assumptions.
3. Generate 6–12 distinct ideas. For each idea, include:
   - Title
   - Brief (1–2 sentences)
   - Target user/persona
   - Value hypothesis (how it helps the user/business)
   - Key risks/assumptions
   - Candidate metrics (leading indicator)
4. Write to plan/ideation.md using this structure:
   - Frontmatter preserved
   - ## Problem / Opportunity
   - ## Constraints & Goals
   - ## Ideas (with the per‑idea template above)
   - ## Notes & Assumptions
5. Report completion with path and number of ideas. Suggest next command: /validate.

Behavior rules:
- Non-destructive: append new session blocks; do not delete prior content.
- Keep each idea brief and testable; avoid implementation detail.
- Use consistent headings and bullet lists.

Context: $ARGUMENTS


