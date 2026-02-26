# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.2.0] - 2026-02-26

### Added

- MCP server integration connecting to the LandingRabbit API (`api.landingrabbit.com`)
- `plugin.json` manifest with MCP server configuration and plugin metadata
- README section documenting MCP server setup and OAuth flow

### Changed

- Moved plugin metadata (author, license, version) from `marketplace.json` into `plugin.json`
- Simplified `marketplace.json` plugin entry to rely on auto-discovery

## [1.1.0] - 2026-02-18

### Added

- `[icon]: ...` field for `collection` + `boxes-icons` items
- `comparison` section guidance for "goodbye / hello" contrasting copy patterns
- Rule: use `stepDecoration: none` when step items already have emoji markers
- Rule: `---` separators only between sections, never inside content blocks
- Rule: keep URLs only inside markdown links, not as standalone lines

### Changed

- `boxes-icons` layout uses dedicated `[icon]` field instead of embedding emoji in eyebrow
- Clarified `steps` vs `comparison` selection for opposing list groups
- Comparison bullet lines use plain text; LandingRabbit renders icons automatically

## [1.0.0] - 2026-02-16

### Added

- A skill for creating a page structure and copy that map cleanly to LandingRabbit-supported sections and content items.

---

[unreleased]: https://github.com/landingrabbit/landingrabbit-skills/compare/v1.2.0...HEAD
[1.2.0]: https://github.com/landingrabbit/landingrabbit-skills/compare/v1.1.0...v1.2.0
[1.1.0]: https://github.com/landingrabbit/landingrabbit-skills/compare/v1.0.0...v1.1.0
[1.0.0]: https://github.com/landingrabbit/landingrabbit-skills/releases/tag/v1.0.0
