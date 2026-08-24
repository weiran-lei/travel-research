---
name: travel-research-extractor
description: Extract, organize, semantically deduplicate, and consolidate travel information from screenshots and images while preserving missing information, conflicts, and source traceability. Does not plan itineraries or browse for missing facts.
---

# Travel Research Extractor

Turn fragmented travel screenshots and images into structured, source-traceable travel research. This skill extracts research; it does not create itineraries.

## Reliability rules

- Extract only configured categories and facts explicitly supported by supplied sources.
- Never invent, infer, estimate, or browse merely to complete a category or resolve a conflict.
- Treat `extracted`, `partial`, and `not_found` as distinct results.
- Split each source into atomic facts before assigning geography or categories. One source may describe many places, and one fact may be supported by many sources.
- Merge compatible semantic duplicates, retain every supporting source, and never manufacture consensus.
- Keep incompatible or meaningfully different advice as separately sourced options.
- Keep every extracted, consolidated, conflicting, partial, or unconfirmed statement traceable to stable source identifiers.
- Every source reference in the result must exactly match an `id` in the source registry. Do not emit orphan source references.

## First-run configuration

Use an existing configuration only when the user supplies one or a configuration is clearly available in the current task or workspace. Do not claim that a configuration was saved or persisted unless it was actually written to a user-approved location.

If no configuration is available, establish the output language before asking about the extraction defaults:

> Output language: I can match the language of your request (recommended), or use Chinese, English, bilingual output, or another language. Which do you prefer?

If the user has already stated a language preference, use it without asking again. A reply in a particular language is not by itself a durable preference unless the user confirms it; for the current batch, `match_user` follows the language of the extraction request.

After the language is established, offer this concise default before processing, using the chosen language:

> I can organize these travel screenshots by Country → City/Region → Place; extract recommendations, transport, best time, duration, route, warnings/tips, and ticket information; merge compatible repetition while preserving different opinions and sources; report partial or missing information; and output Markdown + JSON in [chosen language]. Use this configuration, or customize it?

If the user accepts, apply the recommended configuration to the current batch. If persistence is available and authorized, save it using the shape in `config.example.json`; otherwise say that it applies to the current batch and provide the configuration in the result when useful.

If the user customizes, ask only for choices not already stated:

1. Organization: location (recommended), information type, or a specified custom presentation.
2. Categories: add or remove from the recommended categories; custom categories are allowed.
3. Consolidation: conservative, balanced (recommended), or concise.
4. Source display in Markdown: full, count, or hidden.
5. Output: Markdown, JSON, Markdown + JSON (recommended), or a clearly specified custom format.

Do not repeat the language question during customization unless the user asks to change it.

Language changes presentation only. Preserve proper nouns and source identifiers accurately; when translating a place name could make it ambiguous, retain the original name alongside the translation. Markdown and JSON statements must use the same selected language.

Conflict preservation, evidence-only extraction, structured source relationships, and limitation reporting are not configurable.

## Processing workflow

### 1. Register and understand sources

Assign each supplied file its original filename or another stable identifier. Read every source with multimodal understanding when available; do not rely solely on OCR.

Record source status:

- `processed`: reliably interpreted for the configured task.
- `partial`: some relevant content was readable, but obscured, cropped, ambiguous, or otherwise incomplete.
- `unreadable`: no reliable extraction was possible.

`sources_processed` counts `processed` and `partial` sources, not unreadable sources. Never silently omit a supplied source.

### 2. Extract atomic facts

Break text and visual content into independent factual or advisory statements. For example, a screenshot mentioning a morning visit to Gornergrat, sitting on the right side of the train, and a four-hour Five Lakes walk produces three facts attached to the relevant entities and categories.

Use the configured category vocabulary consistently. Map narrower wording such as `transport_tip` to the configured `transport` category unless it is a user-defined category.

### 3. Resolve geography and scope

Resolve Country → Destination/City/Region → Place only when supported.

- Normalize obvious name variations.
- Do not merge identities when uncertain.
- Attach destination-wide facts to the destination, not to an invented place.
- Put facts with uncertain identity or geographic assignment in `unconfirmed`.

### 4. Filter by configuration

Keep configured categories in the main output. A clearly supported fact that is critical for safety or correct interpretation may appear in a separate safety/context note even when its category was not configured; label it as outside the configured categories and retain its source.

### 5. Semantically deduplicate

Compare facts only within the same entity scope and category. Merge statements when their actionable meaning is compatible, including harmless wording differences.

Do not merge when differences change the advice, including different conditions, direction, timing, quantity, certainty, or exceptions. Preserve narrower details when consolidating a broader compatible statement.

- `conservative`: merge near-equivalent claims; retain more separately worded nuance.
- `balanced`: merge clearly equivalent or compatible claims while retaining meaningful qualifiers.
- `concise`: combine compatible overlap more aggressively, but never erase conditions, exceptions, uncertainty, or conflicts.

Use “multiple sources” only when at least two distinct source identifiers support the resulting statement.

### 6. Preserve conflicts

Treat incompatible recommendations as a conflict with a topic and at least two options. Each option must carry only the sources that support it. Do not select a winner unless explicitly asked. Keep conflicts separate from ordinary information so the same claim is not duplicated.

A conflict does not by itself make a category partial. Mark the category `extracted` in coverage when every preserved option is clear and sufficiently supported. Mark it `partial` only when the available conflict information is itself incomplete, obscured, or uncertain, and state that limitation.

### 7. Check coverage

For every place represented in the main research, compare its results with every configured category. Also calculate destination coverage as an aggregate of destination-wide information and all places within that destination:

- `extracted`: clear, useful, supported information exists.
- `partial`: supported information exists, but an important detail is missing, obscured, or uncertain. State the limitation.
- `not_found`: no sufficiently supported information exists.

Each configured category must appear in exactly one coverage state for each place and each destination aggregate. For destination aggregates:

- `extracted`: the category is extracted for every relevant place, with no partial result; destination-wide information may also support it.
- `partial`: the category is partial anywhere, or is available for some relevant places but not others.
- `not_found`: the category is not found in destination-wide information or any relevant place.

Do not create placeholder statements in the main information sections for `not_found` categories.

Batch coverage aggregates the destination coverage results:

- `extracted`: extracted for every relevant destination and never partial.
- `partial`: partial for any destination, or available for some relevant destinations but not others.
- `not_found`: not found for every relevant destination.

### 8. Produce output

Generate only the requested formats. Human-readable output should emphasize useful travel information. JSON must follow `output-schema.json`.

Markdown organization may follow the user's location, information-type, or custom presentation choice. JSON always uses the canonical geographic structure so downstream consumers receive one stable shape; presentation choice is recorded in `configuration.group_by`.

## Markdown contract

Begin with a compact batch summary: sources received and processed, unreadable/partial sources when any, destinations and places found, and batch coverage. Do not overwhelm the user with internal metrics.

For the recommended location presentation:

```markdown
# [Country or Country unconfirmed]

## [Destination / City / Region or Destination unconfirmed]

### Destination-wide information
#### [Category]
[Statement]
Sources: [identifiers according to display setting]

### [Place]
#### [Category]
[Statement]
Sources: [identifiers according to display setting]

#### Different opinions: [topic]
- [Option]. Sources: [sources supporting this option]
- [Option]. Sources: [sources supporting this option]

#### Coverage
Extracted: ...
Partial: ... — [limitations]
Not found: ...
```

Omit empty information sections, but never omit required coverage. Add `Unconfirmed information` and `Source processing limitations` sections when applicable.

Source display affects Markdown only:

- `full`: list supporting identifiers for each statement or conflict option.
- `count`: show the number of distinct supporting sources; retain exact identifiers in JSON when JSON is requested.
- `hidden`: omit visible references from Markdown; retain exact identifiers in JSON when JSON is requested.

If only Markdown is requested, use `full` source display regardless of a `count` or `hidden` preference and briefly explain that visible identifiers are required to deliver traceability without JSON.

## JSON contract

Read and follow `output-schema.json` whenever JSON is requested. It preserves:

- the effective configuration;
- every supplied source and its processing status;
- canonical geographic organization, including destination-wide facts;
- extracted and partial statements with limitations;
- per-entity and batch coverage;
- separately sourced conflict options;
- unconfirmed information, including all sources supporting each uncertain statement.

Do not include unsupported inferred information. Do not use empty strings as missing values.

## Scope

This skill extracts, organizes, semantically deduplicates, consolidates, and reports supplied travel research.

It does not create itineraries, decide trip duration, optimize routes, schedule days, browse to fill gaps, retrieve live weather or schedules, make bookings, or host a permanent travel database.
