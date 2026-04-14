# shipley-bd-capture-skills

> A modular, open-source BD/Capture Intelligence Skill Library for federal contracting professionals.

---

## Overview

**shipley-bd-capture-skills** is a structured collection of reusable AI agent skills designed to accelerate Business Development (BD) and Capture workflows in the federal contracting market. It is built on two authoritative foundations:

1. **[1102tools / federal-contracting-skills](https://github.com/1102tools/federal-contracting-skills)** — production-grade skills that provide structured access to public federal contracting data sources (USASpending.gov, SAM.gov, FPDS, etc.). Skills in `vendor_skills/` are direct copies of that library and are **not modified**.
2. **Shipley Capture Guide (Fifth Edition)** — the gold-standard methodology for capture management, opportunity qualification, win strategy, and proposal development. All custom skills in `skills/` are explicitly aligned to Shipley phases, gates, and decision criteria.

This library is **AI-platform agnostic** — skills are defined in plain Markdown and can be used with any LLM or agent framework (OpenAI, Azure OpenAI, Claude, Copilot, etc.).

---

## Repository Structure

```
shipley-bd-capture-skills/
├── README.md
├── skills/                          # Custom Shipley BD/Capture skills (this library)
│   ├── 00_piid_resolver_skill.md        # Resolves a PIID to a canonical award record
│   ├── 01_award_baseline_skill.md       # Builds a full award baseline from USASpending data
│   ├── 02_solicitation_artifact_skill.md # Retrieves solicitation artifacts from SAM.gov
│   ├── 03_entity_competitor_skill.md    # Profiles incumbent and competitor entities
│   ├── 04_subaward_flags_skill.md       # Identifies subcontracting patterns and flags
│   ├── 05_requirements_scope_skill.md   # Extracts requirements and scope signals
│   ├── 06_market_agency_customer_skill.md # Maps agency spend, NAICS, and customer intel
│   ├── 07_external_enrichment_skill.md  # Enriches with external data (news, FOIA, etc.)
│   ├── 08_executive_summary_skill.md    # Generates an executive capture summary
│   ├── shipley-milestone-0-qualification_skill.md   # Gate 0: Opportunity Qualification
│   ├── shipley-milestone-1-capture-planning_skill.md # Gate 1: Capture Planning
│   ├── shipley-milestone-2-pursuit_skill.md          # Gate 2: Pursuit Decision
│   ├── shipley-milestone-3-bid-nobid_skill.md        # Gate 3: Bid/No-Bid
│   ├── shipley-milestone-4-pricing-review_skill.md   # Gate 4: Price-to-Win Review
│   └── 09_shipley_orchestrator_skill.md # Master orchestrator: runs Shipley gates end-to-end
├── vendor_skills/                   # Unmodified copies of 1102tools/federal-contracting-skills
├── api_tests/                       # HTTP/curl test files for validating API calls
├── examples/                        # Example inputs, outputs, and walkthroughs
└── references/                      # Supporting references (Shipley phases, NAICS tables, etc.)
```

---

## How It Works

### Data & API Layer — `vendor_skills/`

The `vendor_skills/` directory contains an unmodified copy of the
[1102tools/federal-contracting-skills](https://github.com/1102tools/federal-contracting-skills)
library. These skills define how to call public federal data APIs:

| Skill | Data Source |
|---|---|
| Award search & detail | USASpending.gov API |
| Solicitation search | SAM.gov Opportunities API |
| Entity / company lookup | SAM.gov Entity API |
| Subaward data | USASpending.gov Subawards |
| FPDS transaction history | FPDS-NG / USASpending |

> **Do not modify files in `vendor_skills/`.** To update, pull the latest from 1102tools upstream.

### Intelligence Layer — `skills/`

Custom skills in `skills/` are thin, Shipley-aligned wrappers that:

1. Call one or more `vendor_skills` to retrieve raw federal data.
2. Apply Shipley-defined analysis frameworks (SWOT, customer intimacy scoring, win themes, PTW logic, etc.).
3. Return structured, decision-ready intelligence artifacts.

### Orchestration — `09_shipley_orchestrator_skill.md`

The orchestrator skill drives a full Shipley gate review by sequencing skills 00–08
and all milestone gate skills in order, producing a complete Capture Intelligence Package (CIP).

---

## Shipley Gate Alignment

| Skill File | Shipley Phase |
|---|---|
| `shipley-milestone-0-qualification_skill.md` | Pre-Phase: Opportunity Qualification |
| `shipley-milestone-1-capture-planning_skill.md` | Phase 1: Capture Planning |
| `shipley-milestone-2-pursuit_skill.md` | Phase 2: Pursuit |
| `shipley-milestone-3-bid-nobid_skill.md` | Phase 3: Bid/No-Bid Decision |
| `shipley-milestone-4-pricing-review_skill.md` | Phase 4: Price-to-Win / Pricing Review |
| `09_shipley_orchestrator_skill.md` | All phases: End-to-end orchestration |

---

## Getting Started

1. **Clone this repo**
   ```bash
   git clone https://github.com/BdM-15/shipley-bd-capture-skills.git
   cd shipley-bd-capture-skills
   ```

2. **Populate `vendor_skills/`**
   Copy or clone [1102tools/federal-contracting-skills](https://github.com/1102tools/federal-contracting-skills)
   into the `vendor_skills/` directory.

3. **Use a skill**
   Load any `.md` skill file as a system prompt or skill definition in your agent framework.
   Provide a PIID or opportunity ID as input to skill `00_piid_resolver_skill.md` to begin a capture workflow.

---

## Design Principles

- **Open & agnostic** — No vendor lock-in. Plain Markdown skill definitions work with any LLM.
- **Public data only** — All data sources are publicly accessible US government APIs. No proprietary feeds required.
- **Shipley-faithful** — Every capture decision, scoring rubric, and gate criterion is traceable to the Shipley Capture Guide.
- **Composable** — Each skill is independent and can be used standalone or chained through the orchestrator.
- **1102tools upstream first** — The federal data/API layer is owned by 1102tools. This library extends, never forks.

---

## References

- [1102tools/federal-contracting-skills](https://github.com/1102tools/federal-contracting-skills)
- [Shipley Associates Capture Guide, Fifth Edition](https://shipleywins.com)
- [USASpending.gov API Documentation](https://api.usaspending.gov)
- [SAM.gov API Documentation](https://open.gsa.gov/api/sam/)
- [FPDS-NG](https://www.fpds.gov)

---

## License

MIT License — see [LICENSE](LICENSE) for details.

---

## Contributing

Contributions are welcome. Please open an issue or pull request. All new skills must:
- Be traceable to a Shipley phase or gate.
- Call at least one `vendor_skill` (1102tools) for its data layer.
- Include an `## Example` section with a sample input and expected output.
