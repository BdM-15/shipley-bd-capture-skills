---
name: building-award-baselines
description: Builds a structured award baseline from authoritative federal award data, primarily by wrapping upstream 1102tools capabilities. Use when the user needs core award facts, funding, dates, agencies, recipients, or contract context.
---

# Award Baseline

## Purpose

Build a clean award baseline for downstream capture analysis without recreating upstream retrieval logic.

## Default workflow

1. Use the PIID resolver if the identifier is ambiguous.
2. Retrieve award data through the 1102tools foundation.
3. Normalize the results into a stable summary.
4. Flag missing or conflicting fields.

## Output

Return the baseline with core award facts, source notes, confidence, and gaps.

## Additional material

- Examples: `examples/`
- Tests: `tests/`
- References: `references/`
