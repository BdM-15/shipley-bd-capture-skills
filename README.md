# shipley-bd-capture-skills

shipley-bd-capture-skills is an open-source BD and capture intelligence skill library being shaped into a business-specific plugin package for agent frameworks. Its core rule is unchanged: reuse the 1102tools govcon skills wherever they already solve the problem well, and add only thin Shipley-specific layers on top.

## Project Goal

Build a practical BD and capture plugin foundation that combines:

- Local 1102tools govcon skills for retrieval, research, and document-building primitives.
- Shipley Capture Guide and Proposal Guide framing for qualification, decision gates, win strategy, color reviews, pricing to win, and storyboard-driven proposal thinking.
- Thin repo-specific orchestration, synthesis, and formatting layers rather than full reimplementation of existing govcon skill logic.
- A packaging-ready structure that can become an installable plugin for agent frameworks in the same general category as BMAD, but tailored to this business's BD and capture workflows.

## Target End State

The long-term goal of this repository is not just to hold local skills. It is to become a reusable plugin for agent frameworks that need business-specific BD and capture workflows.

That end state should preserve three layers:

- `govcon-skills/` as the preserved local copy of the 1102tools govcon capabilities.
- `skills/` as the Shipley-specific wrappers, milestone skills, routing logic, and business workflow modules.
- A clean plugin-style structure that can be installed or imported into agent frameworks, similar in spirit to BMAD-style plugin packaging, but focused on this company's capture process, decision gates, and outputs.

The repo should therefore be edited with portability in mind: stable folder conventions, concise skill contracts, explicit routing, and minimal coupling to any single agent runtime.

## Core Philosophy

- Reuse the production-grade skills from 1102tools as the primary data and retrieval layer.
- Keep the local govcon skill set in `govcon-skills/` unchanged unless the task is explicitly about syncing or updating it.
- Add custom skills in `skills/` only where Shipley-specific synthesis, milestone formatting, orchestration, or hardened PIID resolution is required.
- Avoid rebuilding capabilities that 1102tools already provides.
- Keep the library open-source, plain-Markdown, and usable as a future plugin layer across agent or LLM stacks.

## What This Repository Adds

This repository is intended to add thin purpose-built layers for:

- A hardened PIID resolver.
- A synthesis rubric built around Signal, Inference, Evidence, Action, confidence, and PRIME gaps.
- Shipley Capture Guide aligned milestone outputs and decision framing.
- A master orchestrator that chains govcon skills and custom wrappers into a capture workflow.
- The eventual plugin-ready business logic needed to package these workflows cleanly for agent frameworks.

## Skill Layout Standard

This repository follows a folder-per-skill structure consistent with agent skill best practices. Each skill lives in its own directory and includes at minimum:

- `skill.md`
- `examples/`
- `tests/`
- `references/`

Cross-cutting orchestration and productivity modules may live as root-level markdown files in `skills/`, but the local 1102tools govcon skill set belongs under `govcon-skills/` in its preserved repository structure.

## Full Folder Overview

```text
shipley-bd-capture-skills/
├── README.md
├── .github/
│   └── copilot-instructions.md
├── api_tests/
├── examples/
├── references/
├── skills/
│   ├── module-help.csv
│   ├── shipley-bd-orchestrator.md
│   ├── data-analysis.md
│   ├── executive-assistant.md
│   ├── call-plan-developer.md
│   ├── customer-engagement.md
│   ├── brainstorming.md
│   ├── idea-capturer.md
│   ├── color-team-reviews.md
│   ├── pricing-to-win.md
│   ├── 00_piid_resolver/
│   │   ├── skill.md
│   │   ├── examples/
│   │   ├── tests/
│   │   └── references/
│   ├── 01_award_baseline/
│   │   ├── skill.md
│   │   ├── examples/
│   │   ├── tests/
│   │   └── references/
│   ├── 02_entity_competitor/
│   │   ├── skill.md
│   │   ├── examples/
│   │   ├── tests/
│   │   └── references/
│   ├── 03_subaward_flags/
│   │   ├── skill.md
│   │   ├── examples/
│   │   ├── tests/
│   │   └── references/
│   ├── 04_market_agency_customer/
│   │   ├── skill.md
│   │   ├── examples/
│   │   ├── tests/
│   │   └── references/
│   ├── 05_executive_summary/
│   │   ├── skill.md
│   │   ├── examples/
│   │   ├── tests/
│   │   └── references/
│   ├── 06_shipley_orchestrator/
│   │   ├── skill.md
│   │   ├── examples/
│   │   ├── tests/
│   │   └── references/
│   ├── shipley-milestone-0-qualification/
│   │   ├── skill.md
│   │   ├── examples/
│   │   ├── tests/
│   │   └── references/
│   ├── shipley-milestone-1-capture-planning/
│   │   ├── skill.md
│   │   ├── examples/
│   │   ├── tests/
│   │   └── references/
│   ├── shipley-milestone-2-pursuit/
│   │   ├── skill.md
│   │   ├── examples/
│   │   ├── tests/
│   │   └── references/
│   ├── shipley-milestone-3-bid-nobid/
│   │   ├── skill.md
│   │   ├── examples/
│   │   ├── tests/
│   │   └── references/
│   └── shipley-milestone-4-pricing-review/
│       ├── skill.md
│       ├── examples/
│       ├── tests/
│       └── references/
└── govcon-skills/
    ├── README.md
    ├── skills/
    │   ├── market-research-builder/
    │   ├── igce-builder-ffp/
    │   ├── igce-builder-lh-tm/
    │   ├── igce-builder-cr/
    │   ├── vendor-intelligence/
    │   ├── sow-pws-builder/
    │   ├── usaspending-api/
    │   ├── sam-gov-api/
    │   ├── award-review/
    │   └── ... additional govcon skills
```

## Quick Start

1. Clone this repository.
2. Review [.github/copilot-instructions.md](.github/copilot-instructions.md) before editing skill content.
3. Review the vendored `govcon-skills/` snapshot before building wrappers so you reuse govcon skills instead of recreating them.
4. Keep folder-based Shipley skills under `skills/<skill-name>/skill.md` as the repo-specific layers.
5. Use `skills/shipley-bd-orchestrator.md` and `skills/module-help.csv` as the routing layer for multi-skill workflows.

## Refresh 1102tools Snapshot

This repository keeps a lean local copy of the 1102tools govcon skill set in the top-level `govcon-skills/` folder. It intentionally keeps only the 1102tools `README.md` and `skills/` tree.

```powershell
Set-Location c:\GitHub
Set-Location c:\GitHub\shipley-bd-capture-skills
Remove-Item .\govcon-skills -Recurse -Force
git clone https://github.com/1102tools/federal-contracting-skills .\govcon-skills
```

After the refresh completes:

- Remove any non-skill files you do not want to carry beyond `README.md` and `skills/`.
- Keep Shipley-specific wrappers in the numbered and milestone folders.
- Do not rewrite govcon skill logic inside `govcon-skills/` unless the task is explicitly about syncing or patching the local copy.

If you want a leaner setup, you do not need the full original repository to use the skills. See `references/1102tools-minimal-integration.md` for the minimal footprint, required companion skills, and safe omissions.

## Working Model

- `govcon-skills/` holds a lean local copy of the govcon skills consisting of the 1102tools `README.md` and `skills/` tree, and should remain unchanged unless the task is explicitly about updating that local copy.
- `skills/01_award_baseline`, `skills/02_entity_competitor`, and `skills/04_market_agency_customer` are expected to be thin wrappers around 1102tools capabilities rather than replacements.
- `skills/00_piid_resolver` is reserved for the hardened PIID resolver.
- `skills/05_executive_summary` is reserved for synthesis and Shipley executive summary formatting.
- `skills/06_shipley_orchestrator` is reserved for end-to-end orchestration across vendor and custom skills.
- `skills/shipley-bd-orchestrator.md` is the root-level meta-skill that reads `skills/module-help.csv` and routes work across Shipley gates, `govcon-skills/skills/` govcon modules, and productivity modules.
- Documentation and structure changes should move the repo toward an installable business-specific plugin for agent frameworks, not toward a one-off local prompt collection.

## Shipley Guide Anchors

Use these reference anchors throughout the workspace when relevant:

- Capture Guide p.72 for Decision Gate Reviews.
- Capture Guide p.87 for Opportunity Qualification.
- Capture Guide p.43 for Color Team Reviews.
- Capture Guide p.149 for Win Strategy.
- Proposal Guide p.263 for Storyboards.

## Current Status

- The repository contains a lean local copy of the `1102tools/federal-contracting-skills` skill set in `govcon-skills/`.
- Shipley-specific wrappers live in the numbered and milestone folders under `skills/`.
- Productivity and routing modules live as root-level files under `skills/`.
- Detailed repo-specific skill content will continue to be implemented iteratively.
- The current repository is still in the skill-library stage, but the intended end state is a business-specific plugin package for agent frameworks.

## References

- 1102tools federal-contracting-skills: https://github.com/1102tools/federal-contracting-skills
- Shipley Capture Guide, Fifth Edition
- Shipley Proposal Guide
