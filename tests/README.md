# Behavioral testing

Test observable extraction behavior rather than exact prose.

## Minimum fixture

Use local synthetic, licensed, or explicitly approved images that collectively contain:

1. Multiple places and atomic facts in one image.
2. Compatible duplicate advice across distinct sources.
3. Two incompatible opinions about the same place and category.
4. A partially obscured fact with a clear limitation.
5. A destination-wide fact that must not be assigned to a fake place.
6. At least one configured category with no supporting evidence.
7. One uncertain place identity for the `unconfirmed` section.

All files under `tests/fixtures/` are local-only and ignored by Git. Do not force-add
test images or other source material to the repository. Only the `.gitkeep` placeholder
is tracked.

## Invariants

- Every supplied source appears in the source registry.
- Every emitted source reference resolves to a registered source identifier.
- Compatible duplicates consolidate without losing supporting sources.
- Conflicting options remain separate and retain option-specific sources.
- Partial statements explain their limitation.
- Every configured category has exactly one coverage state per place and destination aggregate.
- Missing categories are reported without fabricated values.
- Reader-facing output omits coverage, missing categories, empty sections, and JSON unless requested.
- Every visible conclusion uses a full original filename and, when configured, the smallest sufficient original-text excerpt.
- Clickable source labels retain the original filename rather than anonymous numbering.
- Reader-facing output and JSON, when both requested, use the configured language and convey the same facts.
- The result contains no itinerary, web-derived completion, live data, or booking action.

Expected results may be placed in `tests/expected/` after fixtures are approved.
