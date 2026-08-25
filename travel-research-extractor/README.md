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
8. Produce a concise reader-facing result by default, with canonical geographic JSON available on request.
9. Link every source by its original filename and optionally show the exact original excerpt beside the extracted result.

## First use

If no configuration is supplied or clearly available, the skill uses the agent's native selectable clarification tool for one question at a time. When no such tool is available, it offers the complete recommended configuration once; only users who choose customization enter the numbered question-by-question flow. Choices apply to the current batch unless the user explicitly asks to save them.

Configuration is never claimed to be saved unless it is actually persisted to an authorized location.

## Recommended defaults

- Country → City/Region → Place
- recommendations, transport, best time, duration, route, warnings/tips, tickets
- balanced consolidation
- separate preservation of conflicting opinions
- mandatory conflict preservation, internal coverage checking, and structured source relationships
- clickable original filenames with original-text comparison
- reader-facing Markdown; JSON only when requested
- coverage and missing categories checked internally but hidden by default
- output language matching the user's extraction request

Reader-facing output may use location, information-type, or a custom presentation. It shows only useful extracted information, not empty categories or internal coverage tables. JSON always retains one stable geographic structure and can represent destination-wide facts as well as places.

## Reliability and scope

The skill uses only supplied sources. Missing or uncertain information is reported rather than invented, inferred, or filled using web search.

It extracts and organizes research only. It does not create itineraries, optimize or schedule routes, retrieve live travel information, make bookings, or maintain a travel database.
