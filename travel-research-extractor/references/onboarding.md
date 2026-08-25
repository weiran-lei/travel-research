# First-run configuration

Ask one question at a time. Wait for the answer before asking the next question. Use genuine interactive choices when the host supports them; otherwise present a short numbered list.

Do not ask about a choice the user has already made. A language used in casual conversation is not a durable preference, but `match_user` may use the language of the current extraction request for this batch.

## 1. Output language

Offer:

1. Chinese
2. English
3. Bilingual, with Chinese and English paired
4. Match the current extraction request
5. Another specified language

## 2. Organization

Offer:

1. Location: Country → City/Region → Place (recommended)
2. Information type
3. A custom organization

JSON, when explicitly requested, always retains the canonical geographic organization.

## 3. Categories

Offer:

1. Recommended: recommendation, transport, best time, duration, route, warnings/tips, and tickets
2. Customize categories

If customized, ask only what to add or remove.

## 4. Similar and repeated information

Use user-facing language rather than the internal term `consolidation`:

1. Balanced (recommended): merge equivalent advice and retain important differences
2. Conservative: preserve more wording and nuance separately
3. Concise: merge compatible overlap more aggressively

Conflicts, conditions, exceptions, direction, timing, quantity, and uncertainty are never erased.

## 5. Sources and evidence

Offer:

1. Clickable original filename + original-text comparison (recommended)
2. Clickable original filename only
3. Original filename as plain text

Always keep internal source relationships even if the user chooses not to display original excerpts. Do not offer anonymous source numbering or hidden sources by default.

## 6. Output format

Offer:

1. Reader-facing output (recommended)
2. Reader-facing output + JSON
3. JSON only

Explain JSON only if needed: it is intended for downstream tools and is not necessary for ordinary reading.

## Confirmation

After all choices are complete, show one compact configuration summary and begin extraction. Do not ask for a second blanket confirmation unless a choice remains ambiguous.

Apply choices to the current batch. If the user asks to remember them, request or use authorization to persist a configuration shaped like `config.example.json`. A later user may ask to show, change, reset, or reuse saved settings in natural language.

