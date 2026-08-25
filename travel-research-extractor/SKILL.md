---
name: travel-research-extractor
description: Extract and organize travel information from user-supplied screenshots or images, with clickable source filenames and original-text evidence. Use for evidence-based travel-note extraction, not itinerary planning or web research.
---

# Travel Research Extractor

Turn supplied travel screenshots and images into concise, source-traceable research. Extract research only; do not create an itinerary.

## Core rules

- Use only the supplied sources. Do not browse, invent, infer, estimate, or silently complete missing facts.
- Register every supplied file by its original filename and record whether it was processed, partially readable, or unreadable.
- Read images with multimodal understanding rather than OCR alone. Split each source into atomic facts before assigning geography and categories.
- Merge compatible repetition without losing conditions or source relationships. Keep incompatible advice as separately sourced alternatives.
- Keep each extracted statement traceable to the smallest useful original-text excerpt and its source filename.
- Never claim that a preference or configuration was saved unless it was actually persisted with the user's authorization.
- Do not save, copy, or commit supplied images unless the user explicitly requests it.

## Configuration

Use a configuration supplied by the user or clearly available for this task. Otherwise, read and follow [references/onboarding.md](references/onboarding.md). Ask one configuration question at a time.

For an existing version 0.4–0.6 configuration, preserve its choices and apply these version 0.7 presentation defaults unless the user chooses otherwise:

- clickable original filenames;
- original-text comparison;
- reader-facing Markdown only;
- coverage and missing categories hidden.

## Processing

1. Register all sources using their original filenames as stable IDs.
2. Mark each source `processed`, `partial`, or `unreadable`; explain limitations for the latter two.
3. Extract atomic, explicitly supported facts in the configured categories.
4. Resolve Country → Destination/City/Region → Place only when supported. Keep uncertain identity or geography in an unconfirmed section.
5. Compare facts only within the same entity and category. Merge compatible facts according to the selected consolidation level while retaining meaningful qualifiers and every supporting source.
6. Preserve incompatible advice as alternatives. Do not choose a winner unless asked.
7. Internally check every configured category for extracted, partial, or missing information. This check is a quality-control mechanism, not default user-facing content.
8. Produce only the requested output format.

## Reader-facing output

For Markdown or ordinary reading output, read and follow [references/reader-output.md](references/reader-output.md).

Default behavior:

- Write direct travel facts instead of repeatedly saying “the screenshot says” or “the source suggests.”
- Preserve subjectivity when it matters, such as “the author preferred…” or “the author waited about 20 minutes.”
- Display every source using its full original filename as a clickable local-file link when a usable path is available.
- Pair each conclusion with the smallest sufficient original excerpt so the user can compare what was written with what was extracted.
- Present reader-facing evidence in this order: structured information, `原文`, clickable source. Do not add HTML disclosure tags or a second explanation of what was extracted.
- Do not display JSON, coverage tables, empty categories, or lists of missing categories unless the user requests them.
- Surface a source limitation only when cropping, obscurity, ambiguity, or unreadability affects interpretation.

## Structured output

Only when the user requests JSON, read and follow `output-schema.json`. JSON remains canonical geographic data even if the reader-facing presentation uses another organization.

Every JSON source reference must exactly match an ID in the source registry. Do not use empty strings for missing values. Coverage remains mandatory in JSON because it supports validation, even when hidden from the reading output.

## Scope

This skill extracts, organizes, deduplicates, consolidates, and traces supplied travel research. It does not plan days, optimize routes, retrieve live schedules or prices, browse to fill gaps, make bookings, or maintain a travel database.
