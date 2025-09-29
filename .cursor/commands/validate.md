---
description: Apply feasibility, desirability, and viability scoring to ideation output and write results to plan/validation.md.
---

The user input to you can be provided directly by the agent or as a command argument - you MUST consider it before proceeding with the prompt (if not empty).

User input:

$ARGUMENTS

Goal: Evaluate ideas from plan/ideation.md with a clear rubric and produce a scoring table to inform prioritization.

Writes: plan/validation.md (create if missing; overwrite section content while preserving frontmatter)

Gates:
- Require plan/ideation.md with at least one idea. If missing or empty, abort and instruct user to run /ideate first.

Execution steps:
1. Load plan/ideation.md; extract idea titles and briefs.
2. Establish a rubric (default weights unless overridden via $ARGUMENTS):
   - Feasibility (F): 1–5 — technical complexity, team capability
   - Desirability (D): 1–5 — user value, demand evidence
   - Viability (V): 1–5 — business impact, cost/revenue balance
   - Optional weights: wF=1, wD=1, wV=1 (override via arguments like "wF=2 wD=1 wV=1")
3. Score each idea with F/D/V and compute WeightedScore = (F*wF + D*wD + V*wV).
4. Write plan/validation.md with:
   - Frontmatter preserved
   - ## Rubric & Weights
   - ## Scores (table: Idea | F | D | V | WeightedScore | Notes)
   - ## Top Findings & Risks
   - ## Decision Gate
5. Report completion with path and top 3 ideas by score. Suggest next command: /prioritize.

Behavior rules:
- Be consistent and transparent; provide short justification notes per idea.
- Do not change ideation content; validation is an overlay.

Context: $ARGUMENTS


