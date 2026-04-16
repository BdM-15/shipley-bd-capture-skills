---
name: orchestrating-shipley-capture-workflows
description: Orchestrates the sequence of 1102tools govcon skills from govcon-skills and thin Shipley-specific wrappers into one capture workflow. Use when the user wants an end-to-end analysis flow instead of a single point skill.
---

# Shipley Orchestrator

## Purpose

Coordinate the skill chain so the workflow moves from identifiers and data collection to synthesis and milestone outputs.

## Default workflow

1. Start with identifier resolution.
2. Build the factual baseline.
3. Add entity, subaward, and market context as needed.
4. Produce synthesis and milestone outputs.

## Output

Return the ordered results, key dependencies, confidence notes, and missing information that blocks later stages.

## Additional material

- Examples: `examples/`
- Tests: `tests/`
- References: `references/`
