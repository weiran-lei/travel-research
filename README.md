# Travel Research Extractor

Turn scattered travel screenshots into structured, source-traceable research you can actually use.

> A Codex skill for extracting routes, transport, tickets, timing, warnings, recommendations, and practical travel details from user-supplied images.

## Why

Useful travel research often ends up buried in screenshots from social media, articles, chats, and photo albums. Saving the image is easy; finding the important detail again—and remembering which screenshot it came from—is not.

Travel Research Extractor turns those screenshots into concise travel notes while keeping every result connected to its original source.

It focuses on the step before itinerary planning:

**Collect → Understand → Structure → Verify**

## What it produces

The default result is organized geographically:

**Country → Destination / Region → Place**

Country-wide guidance—such as rail passes, tax refunds, national transport advice, or general travel rules—can be kept at country level instead of being attached to a made-up destination.

Each result follows the same reader-facing pattern:

```markdown
## Zermatt

### Gornergrat · Transport
Take the mountain railway from Zermatt. A Swiss Pass or Half Fare Card may provide a discount.

Original text:
> The mountain railway ticket can be purchased opposite Zermatt station; Swiss Pass and Half Fare Card holders receive a discount.

Source: IMG_4310.PNG
```

When the host provides a usable file locator, the full original filename becomes a clickable link that opens the source image.

## What makes it useful

- **Understands travel information, not just OCR text** — extracts the detail that matters and assigns it to the right geographic level.
- **Handles batches of screenshots** — one image may contain several places, facts, or categories.
- **Consolidates compatible repetition** — merges equivalent advice without discarding useful conditions or sources.
- **Preserves disagreement** — keeps incompatible opinions as separately sourced alternatives instead of inventing consensus.
- **Keeps the original wording nearby** — shows a small supporting excerpt beside the structured result.
- **Keeps sources recognizable** — original filenames remain stable IDs and visible labels; they are never replaced by anonymous numbering.
- **Stays concise by default** — internal coverage checks, missing categories, and JSON are hidden unless requested.

## How to use it

Attach one or more travel screenshots and invoke the skill:

```text
$travel-research-extractor Extract the travel information from these screenshots.
```

You can also ask in your preferred language:

```text
$travel-research-extractor 提取这些旅行截图中的信息
```

On first use, the skill asks a short series of selectable questions about language, organization, extraction categories, consolidation, source display, and output format. If the host cannot show selectable controls, you can accept the recommended configuration in one reply.

The recommended setup produces concise Markdown in the user's language, includes original-text comparison and source filenames, and keeps coverage and missing-information bookkeeping out of the reading view.

## Install in Codex

Clone this repository and copy the installable skill directory into your Codex skills directory:

```bash
git clone https://github.com/weiran-lei/travel-research.git
cp -R travel-research/travel-research-extractor ~/.codex/skills/
```

If `CODEX_HOME` is set, copy the directory to `$CODEX_HOME/skills/` instead. Start a new Codex task after installation, then invoke `$travel-research-extractor`.

## Reliability and privacy

- The skill uses only the sources supplied by the user.
- It does not browse the web to fill gaps or silently invent missing details.
- Partial, cropped, ambiguous, or unreadable content remains qualified rather than presented as certain.
- Source images are not copied into the skill or repository and are not persisted merely to create clickable links.
- A source path or locator is optional; the original filename remains the source ID when no stable locator is available.

## Deliberate boundaries

This skill extracts, organizes, deduplicates, consolidates, and traces travel research. It does not:

- create or optimize itineraries;
- retrieve live schedules, prices, weather, or availability;
- make bookings;
- maintain a travel database;
- replace verification of time-sensitive information.

## Repository layout

```text
travel-research-extractor/  Installable skill package
tests/                      Behavioral-test specification and local fixture area
CHANGELOG.md                Release history
WORKLOG.md                  Current development and handoff state
```

Behavioral expectations are documented in [tests/README.md](tests/README.md). Personal screenshots and source materials must remain outside Git or under the ignored `tests/fixtures/` directory.

## Current version

`0.8` — optional source locators and country-wide information, with concise structured output, original-text comparison, and source links.

No license has been selected yet. Copyright remains with the repository owner unless a license is added.
