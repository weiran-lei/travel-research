# Travel Research Extractor

A Codex agent skill that extracts, organizes, semantically deduplicates, and consolidates travel information from supplied screenshots and images while preserving conflicts, missing information, and source traceability.

It does not create itineraries or browse the web to fill gaps.

## Repository layout

```text
travel-research-extractor/  Installable skill package
tests/                      Behavioral-test fixtures and expected results
CHANGELOG.md                Release history
```

## Install in Codex

Clone the repository, then copy the skill directory into your Codex skills directory:

```bash
git clone https://github.com/weiran-lei/travel-research.git
cp -R travel-research/travel-research-extractor ~/.codex/skills/
```

If `CODEX_HOME` is set, copy it to `$CODEX_HOME/skills/` instead. Start a new Codex task after installation and invoke `$travel-research-extractor`.

## Test

Use a small batch containing:

- several places in one screenshot;
- equivalent recommendations with different wording;
- directly conflicting advice;
- partially cropped or obscured text;
- a destination-wide fact;
- a country-wide fact;
- configured categories that are not present.

Expected behavior is documented in [tests/README.md](tests/README.md). Do not commit personal screenshots or source material without permission.

## Current version

`0.8` — optional source locators and country-wide information, with the v0.7 reader-facing behavior preserved.

No license has been selected yet. Copyright remains with the repository owner unless a license is added.
