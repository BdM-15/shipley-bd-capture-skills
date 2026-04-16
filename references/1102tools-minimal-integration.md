# 1102tools Minimal Integration

## Bottom line

You do not need the full `1102tools/federal-contracting-skills` repository to leverage the available govcon skills.

The minimum reliable unit is not the whole repo. It is the specific govcon skill folders you plan to use, including any companion reference folders they depend on.

## Keep vs omit

Keep these assets if your goal is to use the govcon skills reliably:

- `govcon-skills/skills/<skill-name>/`
- Companion reference skill folders when the main skill says to install or read them
- The copied `README.md` if you want the dependency table in one place

You can safely omit these if you only care about using the skills:

- `.git/`
- `.github/`
- `CODE_OF_CONDUCT.md`
- `CONTRIBUTING.md`
- `SECURITY.md`
- `docs/` images and diagrams
- top-level licensing and community files that are not part of runtime skill usage

## Important rule

Do not flatten the govcon skills into individual markdown files.

Keep each govcon skill as its own folder because some skills depend on companion reference folders and the copied documentation assumes folder-based navigation.

## Recommended minimum upstream set for this workspace

This is the smallest useful govcon skill set if the goal is to support the Shipley wrappers already planned in this repository.

### Core federal data layer

- `usaspending-api/`
- `usaspending-api-reference/`
- `sam-gov-api/`
- `sam-gov-api-reference/`
- `bls-oews-api/`
- `bls-oews-api-reference/`
- `gsa-calc-ceilingrates/`
- `gsa-calc-ceilingrates-reference/`
- `gsa-perdiem-rates/`
- `gsa-perdiem-rates-reference/`

### Core orchestration layer

- `market-research-builder/`
- `vendor-intelligence/`
- `vendor-intelligence-reference/`
- `award-review/`
- `award-review-reference/`
- `sow-pws-builder/`
- `igce-builder-ffp/`
- `igce-builder-lh-tm/`
- `igce-builder-cr/`

### Optional but useful extensions

- `ecfr-api/`
- `ecfr-api-reference/`
- `federalregister-api/`
- `federalregister-api-reference/`
- `regulationsgov-api/`
- `regulationsgov-api-reference/`
- `ot-project-description-builder/`
- `ot-cost-analysis/`
- `grants-builder/`

## Transitive dependency map

Use this when deciding what to retain.

### Market research

- Main skill: `market-research-builder/`
- Must also keep: `usaspending-api/`
- Strongly recommended: `usaspending-api-reference/`

### Vendor due diligence

- Main skill: `vendor-intelligence/`
- Must also keep: `sam-gov-api/`, `usaspending-api/`
- Strongly recommended: `sam-gov-api-reference/`, `vendor-intelligence-reference/`, `usaspending-api-reference/`

### Award review

- Main skill: `award-review/`
- Must also keep: `sam-gov-api/`, `usaspending-api/`
- Strongly recommended: `award-review-reference/`, `sam-gov-api-reference/`, `usaspending-api-reference/`

### SOW or PWS generation

- Main skill: `sow-pws-builder/`
- No upstream API skill required to run the workflow itself
- Downstream handoff often feeds IGCE builders

### IGCE workflows

- Main skills: `igce-builder-ffp/`, `igce-builder-lh-tm/`, `igce-builder-cr/`
- Must also keep: `bls-oews-api/`, `gsa-calc-ceilingrates/`, `gsa-perdiem-rates/`
- Strongly recommended: `bls-oews-api-reference/`, `gsa-calc-ceilingrates-reference/`, `gsa-perdiem-rates-reference/`

## Minimum API keys

Three free keys cover the main govcon skill capabilities used by this repo:

- BLS API key
- `api.data.gov` key
- SAM.gov API key

USASpending does not require a key.

## Lean vendoring options

### Option A: Keep the full copied govcon set

Pros:

- No risk of missing a hidden dependency
- Easier future expansion
- Easier diffing against the original source later

Cons:

- More files than this workspace immediately needs

### Option B: Keep only `skills/` plus the copied `README.md`

Recommended if you want a smaller footprint without being fragile.

Keep:

- `govcon-skills/skills/`
- `govcon-skills/README.md`

Drop the rest if you do not need them.

### Option C: Keep only the transitive minimum set listed above

Recommended only if you want the smallest possible footprint and are willing to maintain the dependency map carefully.

## Best recommendation for this repo

The best practical compromise is Option B.

Keep:

- copied `skills/`
- copied `README.md`

That gives you the full skill surface area and dependency context without carrying the full community and repository scaffolding.

## Safe next step

If you want to slim the workspace, replace the current local copy with this smaller preserved structure:

```text
govcon-skills/
├── README.md
└── skills/
    └── ... govcon skill folders
```

That is enough to leverage the available 1102tools skills for this workspace without missing operational content.
