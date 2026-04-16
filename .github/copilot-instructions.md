# Copilot Instructions For This Workspace

This repository is an open-source BD and capture intelligence skill library that is intended to become a business-specific plugin for agent frameworks. Prefer small, correct, maintainable changes that preserve the skill system's structure, portability, and validity.

## Core Operating Rules

- Reuse the 1102tools govcon skills wherever they already solve 80 to 90 percent of the problem.
- Treat `govcon-skills/` as the local govcon skill set. Do not modify files there unless the user explicitly asks for that.
- Keep the 1102tools govcon skills in `govcon-skills/`, preserving the copied repository layout.
- Build only thin Shipley-specific layers on top of the govcon capabilities already copied into this repo.
- Avoid recreating data retrieval, vendor intelligence, or market research behaviors that should remain in the copied govcon skills under `govcon-skills/`.
- Keep changes focused. Do not expand a placeholder into a full implementation unless the task calls for it.
- Favor changes that move the repo toward a reusable plugin shape for agent frameworks instead of a one-off local prompt collection.

## Skill File Requirements

Every skill directory under `skills/` must contain:

- `skill.md`
- `examples/`
- `tests/`
- `references/`

Each `skill.md` must remain valid for Claude-style skill loading:

- Include YAML frontmatter at the top.
- Frontmatter must include `name` and `description`.
- `name` must use only lowercase letters, numbers, and hyphens.
- `description` must be specific, non-empty, and written in third person.
- Keep the body concise and practical.
- Use forward slashes in file references, never backslashes.

Use this default shape unless the task requires something more specific:

```md
---
name: example-skill-name
description: Describes what the skill does and when to use it.
---

# Skill Title

## Purpose

## Default workflow

## Output

## Additional material
```

## Claude Skill Best Practices To Preserve

- Optimize for concise instructions, not long explanations.
- Assume the model is already capable. Only include context the skill actually needs.
- Keep `skill.md` as the top-level guide and use progressive disclosure for details.
- Link directly from `skill.md` to supporting files in `examples/`, `tests/`, or `references/`.
- Avoid nested reference chains where one reference file points to another reference file for essential instructions.
- If a reference file grows beyond roughly 100 lines, add a table of contents near the top.
- If a skill becomes large, move detailed workflows, examples, and reference content out of `skill.md` instead of bloating it.
- Prefer one recommended default approach over listing many alternatives.

## Repository-Specific Content Rules

- Preserve the 00 to 06 numbered core skill sequence without gaps.
- If a numbered core skill is added, removed, or renamed, update numbering consistently and sync all affected references.
- Leave Shipley milestone folders aligned to their milestone names unless the user asks otherwise.
- Keep README examples and tree listings synchronized with the actual repository structure.
- When a skill wraps govcon capability from `govcon-skills/`, say so explicitly in the skill content rather than implying this repository owns the full behavior.
- Keep structure and wording compatible with future plugin packaging for agent frameworks, including predictable folders, concise contracts, and minimal runtime-specific assumptions.

## Authoring Guidance For Skill Content

- Separate verified evidence from inference.
- When useful, structure outputs around Signal, Inference, Evidence, Action, confidence, and PRIME gaps.
- Prefer decision-ready outputs over generic summaries.
- Call out missing information explicitly instead of filling gaps with assumptions.
- Use consistent terminology across skills.
- Avoid time-sensitive wording unless the task requires dated historical context.

## Examples, Tests, And Validation

- When implementing or revising a real skill, add concrete examples and test artifacts early.
- Prefer evaluation-driven iteration: identify the failure mode, create a representative example or test, then adjust the skill.
- If a skill introduces scripts or deterministic helpers later, include a validate-fix-repeat workflow.
- After editing skill files, run workspace validation and fix metadata or formatting errors before finishing.

## Editing Hygiene

- Keep Markdown readable and easy to diff.
- Do not introduce Windows-style paths into skill content.
- Do not rename folders casually. Renames should only happen when they improve structure or are required by the task.
- Do not leave placeholder text that makes a skill invalid.
- When changing folder names or skill names, update README references and any affected skill headings in the same change.

## Preferred Defaults For This Repo

- Default to thin wrappers around the govcon skills, not replacements.
- Default to concise instructions, not training manuals.
- Default to one clear workflow, not many optional branches.
- Default to explicit gaps and confidence, not implied certainty.
- Default to updating related docs when structure changes.
- Default to changes that improve reuse in a future business-specific agent-framework plugin.
