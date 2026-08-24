# Travel Research Extractor

Turn supplied travel screenshots and images into structured, source-traceable research.

The skill can:

1. Read batches in which one image contains many facts or places.
2. Organize place-specific and destination-wide information.
3. Extract only configured travel categories.
4. Consolidate compatible repetition without erasing qualifiers.
5. Preserve incompatible opinions with sources attached to each option.
6. Report extracted, partially extracted, and missing categories.
7. Report partially readable or unreadable source images.
8. Produce Markdown and/or canonical geographic JSON.

## First use

If no configuration is supplied or clearly available, the skill first establishes the output language. The recommended setting is `match_user`; Chinese, English, bilingual, and custom-language output are also supported. It then offers concise extraction defaults. The user may accept them for the current batch or customize organization, categories, consolidation, Markdown source display, and output format.

Configuration is never claimed to be saved unless it is actually persisted to an authorized location.

## Recommended defaults

- Country → City/Region → Place
- recommendations, transport, best time, duration, route, warnings/tips, tickets
- balanced consolidation
- separate preservation of conflicting opinions
- mandatory conflict preservation, coverage reporting, and structured source relationships
- full source references
- Markdown + JSON
- output language matching the user's extraction request

Markdown may use location, information-type, or a custom presentation. JSON always retains one stable geographic structure and can represent destination-wide facts as well as places.

## Reliability and scope

The skill uses only supplied sources. Missing or uncertain information is reported rather than invented, inferred, or filled using web search.

It extracts and organizes research only. It does not create itineraries, optimize or schedule routes, retrieve live travel information, make bookings, or maintain a travel database.
