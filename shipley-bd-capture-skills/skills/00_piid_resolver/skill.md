---
name: resolving-piids
description: Resolves PIIDs and related award identifiers into a canonical record with normalized fields and source confidence. Use when a task starts from a PIID, award number, contract identifier, or ambiguous federal award reference.
---

# PIID Resolver

## Purpose

Resolve a PIID or near-match identifier into one canonical award target before downstream analysis begins.

## Default workflow

1. Normalize the input identifier.
2. Check likely variants and formatting differences.
3. Select the best canonical match.
4. Return the canonical PIID, matched record, confidence, and unresolved gaps.

## Output

Return a concise result with:

- Canonical PIID
- Matched award identifier
- Confidence
- Evidence for the match
- Open questions or PRIME gaps

## Additional material

- Examples: `examples/`
- Tests: `tests/`
- References: `references/`
