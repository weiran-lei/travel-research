# Changelog

## 0.5 — 2026-08-25

- Replaced the blanket first-run confirmation with one configuration question at a time.
- Made reader-facing Markdown the default and JSON an explicit opt-in.
- Added clickable source links that retain complete original filenames.
- Added original-text excerpts beside normalized extracted facts.
- Hid coverage, missing categories, empty sections, and internal metrics from the default reading output.
- Replaced repetitive source-preface wording with direct facts while preserving attribution for opinions and personal experiences.
- Split onboarding and reader-output details into focused references.

## 0.4 — 2026-08-25

- Added language selection at the beginning of first-run configuration.
- Added `match_user` as the recommended language setting.
- Required Markdown and JSON statements to use the same selected language.
- Preserved original place names when translation could be ambiguous.

## 0.3 — 2026-08-24

- Made conflict preservation, coverage reporting, and source relationships mandatory.
- Added multi-source support for unconfirmed statements.
- Defined coverage behavior for conflicts and destination aggregates.
- Required source references to resolve to registered source identifiers.

## 0.2 — 2026-08-24

- Added source processing statuses and limitation reporting.
- Added destination-wide facts to the canonical JSON structure.
- Tightened partial extraction, semantic deduplication, Markdown, and JSON contracts.

## 0.1 — 2026-08-24

- Initial skill draft.
