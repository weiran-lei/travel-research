# Reader-facing output

Optimize for reading and verification rather than exposing internal bookkeeping.

## Opening summary

Begin with a short batch summary containing:

- sources received and successfully interpreted;
- partial or unreadable sources only when any exist;
- destinations and places found.

Do not show knowledge-item counts, coverage states, configuration objects, or other internal metrics by default.

## Organization

Use the selected location, information-type, or custom organization. Under location organization, use only headings that contain useful extracted information:

```markdown
# [Country or Country unconfirmed]

## Country-wide information (only when present)

### [Category]
[Direct, consolidated result]

原文：
> [smallest sufficient verbatim excerpt]

来源：[original-filename.ext]([registered locator])

## [Destination / City / Region]

### [Place or destination-wide topic]

#### [Category]
[Direct, consolidated result]

原文：
> [smallest sufficient verbatim excerpt]

来源：[original-filename.ext]([registered locator])
```

Links must use the source registry's `locator` and retain the full original filename as their label. If no locator is registered, show the full filename as plain text. Never replace filenames with “Image 1” or another anonymous number.

Do not use HTML disclosure or collapsible elements. Do not add a second extraction explanation after the result: the structured result already is the extraction.

## Evidence mapping

- Quote only the smallest excerpt needed to verify the extracted statement; do not transcribe an entire screenshot when a sentence or phrase is sufficient.
- Keep wording faithful. Use an ellipsis only to mark omitted surrounding text, never to join fragments into a new meaning.
- Place each excerpt immediately after the structured information it supports, then show its source link.
- Group compatible facts under one useful topic, followed by their original excerpts and sources; do not create a separate evidence block for every sentence when the same excerpt supports the group.
- If multiple sources support one conclusion, list each clickable filename and give each source its own excerpt when the wording materially differs.
- For facts spanning consecutive cropped screenshots, cite both files and state the cropping limitation once.
- Preserve original spelling in excerpts. Normalize place names, capitalization, units, and categories only in the extracted result.

## Voice

State objective source content directly:

- Prefer: `持 Swiss Pass 或半价卡可享折扣。`
- Avoid: `截图提示持 Swiss Pass 或半价卡可享折扣。`

Attribute experiences and opinions:

- `作者当次排队约 20 分钟。`
- `作者更喜欢这条线路。`

For prices, schedules, operating periods, or other potentially changing facts, give one compact batch-level notice that they reflect the supplied sources and may need current verification. Do not repeat that disclaimer after every statement.

## Conflicts and limitations

Present incompatible advice as clearly labeled alternatives, each with its own source and original excerpt. Do not manufacture consensus or select a winner unless asked.

Show limitations only when they affect interpretation. Use natural language such as:

`原图底部被裁切，后续路线说明可能不完整。`

Do not expose `partial`, `not_found`, coverage tables, empty headings, placeholder statements, or lists of absent categories in the default reading output. If the user asks for completeness or coverage, translate the internal coverage check into a concise human-readable audit.
