---
name: shipley-bd-orchestrator
description: Routes BD and capture requests across Shipley gate skills, 1102tools govcon skills from govcon-skills, and workspace productivity skills by loading module-help.csv first and then selecting the smallest useful set of modules for the task.
---

# Shipley BD Orchestrator

## Purpose

Act as the master meta-skill for this workspace.

Use `module-help.csv` as the routing table, then coordinate the right combination of:

- Shipley Gates 1 to 5
- 1102tools govcon skills from `../govcon-skills/skills/`
- Productivity skills for analysis, planning, and synthesis

## Required first step

Read `module-help.csv` before selecting other modules.

Use the CSV to determine:

- likely skill matches by `trigger_keywords`
- whether the request is a Shipley gate question, a govcon skill question, or a productivity task
- the preferred `phase_gate`
- relative `priority`

## Routing rules

1. If the user is asking for opportunity qualification, route first to Gate 1 logic aligned to Capture Guide p.87.
2. If the user is asking for a decision review or gate posture, apply Capture Guide p.72 framing.
3. If the task is about win themes, differentiation, or pursuit posture, elevate win-strategy thinking from Capture Guide p.149.
4. If the task is about review readiness, issue finding, or review comments, incorporate Color Team Review discipline from Capture Guide p.43.
5. If the task is about proposal narrative shaping, storyboard logic, or message architecture, incorporate Proposal Guide p.263 storyboard thinking.
6. Prefer the govcon skills from `../govcon-skills/skills/` for federal data retrieval, market research, SOW/PWS construction, vendor intelligence, award review, and IGCE building.
7. Use workspace productivity skills only for synthesis, planning, meeting support, ideation, and note capture.
8. Do not use more modules than needed. Prefer the smallest defensible set.

## Default orchestration sequence

1. Read `module-help.csv`.
2. Identify the user's phase, gate, and desired output.
3. Select one lead module and only the supporting modules required.
4. Separate evidence retrieval from synthesis.
5. Return a decision-ready output with explicit confidence and gaps.

## Preferred routing patterns

### Qualification and early capture

- Start with Gate 1 qualification.
- Pull `market-research-builder`, `vendor-intelligence`, `usaspending-api`, or `sam-gov-api` only if needed.
- Use `executive-assistant` or `idea-capturer` only for packaging and capture notes.

### Requirements and pricing development

- Start with `sow-pws-builder` when scope definition is the real task.
- Route to the correct IGCE builder only after the scope is stable.
- Add `pricing-to-win` for competitive pricing posture.

### Executive and review workflows

- Use the Shipley gate module as the anchor.
- Add `color-team-reviews`, `executive-assistant`, or `call-plan-developer` as support modules.

## Output contract

Return:

- selected modules
- why they were chosen
- the recommended execution order
- any dependencies or missing inputs
- explicit Signal, Inference, Evidence, Action, confidence, and PRIME gaps when the task requires synthesis
