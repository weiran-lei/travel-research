# First-run configuration

Ask one question at a time and wait for the answer before continuing.

## Interaction priority

Use structured, selectable clarification whenever the host exposes it. Resolve the mechanism in this order:

1. Codex: call `request_user_input` when it is available in the current mode.
2. Claude Code: call `AskUserQuestion` with the available options.
3. Other agents: use the host's equivalent structured choice or button tool when available.
4. Only when no structured choice mechanism is callable, present a short numbered list and accept a number.

Do not ask the user to type the full label of a standard choice. Free-form input is only the fallback for `Other`, `Custom`, or a clarification that cannot be represented by the offered options.

Keep each selectable question within the host tool's option limit. If a host allows only two or three choices, put the recommended mainstream choices in the control and let its built-in `Other` option handle the rest.

Do not ask about a choice the user has already made. A language used in casual conversation is not a durable preference, but `match_user` may use the language of the current extraction request for this batch.

## 1. Output language

Offer as selectable choices:

1. Chinese (recommended when the extraction request is Chinese)
2. English
3. Bilingual, with Chinese and English paired
4. Match the current extraction request
5. Another specified language

## 2. Organization

Offer as selectable choices:

1. Location: Country → City/Region → Place (recommended)
2. Information type
3. A custom organization

JSON, when explicitly requested, always retains the canonical geographic organization.

## 3. Categories

Offer as selectable choices:

1. Recommended: recommendation, transport, best time, duration, route, warnings/tips, and tickets
2. Customize categories

If customized, ask only what to add or remove.

## 4. Similar and repeated information

Offer selectable choices using user-facing language rather than the internal term `consolidation`:

1. Balanced (recommended): merge equivalent advice and retain important differences
2. Conservative: preserve more wording and nuance separately
3. Concise: merge compatible overlap more aggressively

Conflicts, conditions, exceptions, direction, timing, quantity, and uncertainty are never erased.

## 5. Sources and evidence

Offer as selectable choices:

1. Clickable original filename + original-text comparison (recommended)
2. Clickable original filename only
3. Original filename as plain text

Always keep internal source relationships even if the user chooses not to display original excerpts. Do not offer anonymous source numbering or hidden sources by default.

## 6. Output format

Offer as selectable choices:

1. Reader-facing output (recommended)
2. Reader-facing output + JSON
3. JSON only

Explain JSON only if needed: it is intended for downstream tools and is not necessary for ordinary reading.

## Confirmation

After all choices are complete, show one compact configuration summary and begin extraction. Do not ask for a second blanket confirmation unless a choice remains ambiguous.

Apply choices to the current batch. If the user asks to remember them, request or use authorization to persist a configuration shaped like `config.example.json`. A later user may ask to show, change, reset, or reuse saved settings in natural language.
