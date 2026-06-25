# Changelog

All notable changes to **Idexal Code** are recorded here. The format follows
[Keep a Changelog](https://keepachangelog.com/); versions follow [SemVer](https://semver.org/).
A friendly version lives at **https://idexal.github.io/idexal-code/changelog.html**.

## [Unreleased]

## [1.4.0] — 2026-06-25

### Added
- **Memory as a self-building knowledge graph** — agent memory now also reads a folder of
  interconnected `.idexal/memory/*.md` notes (`[[wikilinks]]`). Your project's knowledge
  builds itself into a browsable graph (open it in Obsidian), syncs through git, and is
  recalled into every agent. Self-hosted, open, no subscriptions. See
  `docs/memory-knowledge-graph.md`.
- **Crawl4AI integration guide** — connect the free, self-hosted
  [Crawl4AI](https://github.com/unclecode/crawl4ai) web crawler as an MCP server for clean
  web → Markdown/JSON scraping (JS/SPA pages, structured extraction, RAG ingestion). No
  Python in Idexal — it's a remote MCP server. See `docs/integrations/crawl4ai.md`.

## [1.3.0] — 2026-06-25

### Added
- **Scheduled loops (GitHub Actions)** — a `loop` workflow runs idexal on a schedule to
  do a recurring task (e.g. a daily triage) with no human prompting, completing loop
  engineering's autonomous-loop primitive. Safe by default: a no-op until you add the
  `IDEXAL_API_KEY` secret. Also a copy-paste template for any repo.
- **`verify` skill (maker/checker)** — a bundled skill for independent, adversarial
  verification: confirm a result is actually correct by *executing* checks, not by reading.
  The "checker" the loop's verify step leans on; distilled from the result-verifier role.
- **More bundled skills** — `security-review` (red-team find + blue-team confirm) and
  `codebase-exploration`, distilled from the idexal/skills roles. Seven defaults now.
- **`/loop` command** — `/loop <goal>` runs a goal through the verified-loop discipline
  (it pulls in the `loop` + `verify` skills). A third loop trigger alongside Mission
  Control's Loop mode and the scheduled Actions loop.

## [1.2.0] — 2026-06-25

### Added
- **Bundled default skills** — every agent now ships with a curated starter set
  (`tdd`, `code-review`, `systematic-debugging`, `loop`) through a new embedded-skill
  source, with no config and no network. Project skills in `.idexal/skills/` override them by name.
- **Loop engineering** — the bundled `loop` skill gives agents a verified-loop discipline
  (discover → record state → implement → verify → gate), built on agent memory (state) and
  skills. You design the loop once instead of prompting every micro-step.
- **Mission Control — Loop mode** — run a goal as an autonomous verified loop. The runner
  drives one session, re-prompting it to keep working and self-checking until the agent
  reports "LOOP DONE" or the iteration cap is reached; progress and state persist in memory.

## [1.1.0] — 2026-06-25

### Added
- **Agent memory** — durable, per-project memory injected into every agent and every
  model, every turn, so the assistant remembers the project and your working style and
  never forgets.
  - A `memory` tool agents call to save durable facts, persisted in the app's local
    SQLite database.
  - Recall ranks semantically (cosine similarity) when embeddings are present, and
    falls back to keyword then recency — so it always works.
  - Hand-authored `.idexal/memory.md` (and a global `memory.md`) are injected too, and
    you can edit them directly, like `AGENTS.md`.

### Fixed
- Repaired the public-API namespace (`Idexal`), which the rebrand had turned into an
  invalid identifier.

## [1.0.6] — 2026-06-25

### Added
- **Mission Control — parallel task launcher**: fan one goal out to N agents at once and
  compare their results live on the board.

## [1.0.5] — 2026-06-25

### Changed
- Home glow-up: a welcome tagline, an aurora glow, and a warmer empty state.

## [1.0.4] — 2026-06-25

### Added
- **Mission Control**: a live board of every agent and session in the project (`⌘⇧M`).

## [1.0.3] — 2026-06-25

### Fixed
- Desktop installer finish-launch error (removed the Start-menu subfolder mismatch).

## [1.0.2] — 2026-06-25

### Added
- Advanced, branded Windows installer — wizard, license step, custom install directory,
  and shortcuts.

## [0.2.0] — 2026-06-25

### Changed
- **Radical rebrand: opencode → Idexal Code.** Zero "opencode" residue. The Idexal
  gateway (`api.idexal.com`) is the default provider with automatic model discovery, and
  unused providers were removed.

## [0.1.0 – 0.1.5] — 2026-06-24 → 2026-06-25

### Added
- First Idexal builds: official logos and app icons, the brand theme (blue + cyan), and
  the CLI + desktop release pipeline that publishes to both repositories.

[Unreleased]: https://github.com/idexal/code/compare/v1.4.0...HEAD
[1.4.0]: https://github.com/idexal/code/releases/tag/v1.4.0
[1.3.0]: https://github.com/idexal/code/releases/tag/v1.3.0
[1.2.0]: https://github.com/idexal/code/releases/tag/v1.2.0
[1.1.0]: https://github.com/idexal/code/releases/tag/v1.1.0
[1.0.6]: https://github.com/idexal/code/releases/tag/v1.0.6
[1.0.5]: https://github.com/idexal/code/releases/tag/v1.0.5
[1.0.4]: https://github.com/idexal/code/releases/tag/v1.0.4
[1.0.3]: https://github.com/idexal/code/releases/tag/v1.0.3
[1.0.2]: https://github.com/idexal/code/releases/tag/v1.0.2
[0.2.0]: https://github.com/idexal/code/releases/tag/v0.2.0
