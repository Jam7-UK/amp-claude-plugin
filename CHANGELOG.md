# Changelog

All notable changes to this plugin are listed here. The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and versions follow [Semantic Versioning](https://semver.org/).

## [1.0.4] - 2026-11-26

### Changed

- The plugin's display name is now "Agentic Marketing Platform® by Jam 7" (was "AMP by Jam 7"). The plugin name `amp-by-jam7` and its install commands are unchanged.

## [1.0.3] - 2026-11-26

### Changed

- The publisher is now named by its legal entity, Jam 7 Limited, in `plugin.json` and the marketplace owner. The directory's name check read "Jam 7" as a look-alike of another publisher.

## [1.0.2] - 2026-11-18

### Fixed

- The `marketing-brain` skill sends Claude to `list_agents` only when the connection offers it. AMP requires agent chat permission for it and does not offer it to viewers.

## [1.0.1] - 2026-11-17

### Fixed

- The `review-and-update-cards` skill now tells Claude to send `cardId`, `expectedVersion` and `editRevision` on every `edit_card` call, as AMP requires.
- The `ask-amp-agents` skill now says an `ask_agent` turn starts as soon as it is sent, with no preview or confirmation step, so Claude sends only requests the user made.
- The `marketing-brain` skill no longer tells Claude to call `search_amp_mentions`. AMP exposes that tool only to an assistant's reference-picker UI, so Claude cannot call it. Loose names are now resolved with `search_cards`, `list_agents` and `search_marketing_brain`.

### Changed

- Licence changed from MIT to a proprietary Jam 7 licence. You may install and use the plugin, unmodified, with AMP; other copying, modification, redistribution or commercial use needs Jam 7's written permission.

## [1.0.0] - 2026-11-11

### Added

- First public release of the AMP by Jam 7 plugin for Claude.
- Connector configuration for the AMP remote MCP server at `https://actions.jam7.com/mcp`, with OAuth sign-in.
- Six skills: `get-started`, `marketing-brain`, `board-and-card-status`, `create-card`, `review-and-update-cards` and `ask-amp-agents`.
- `jam7` marketplace, so the plugin installs with `/plugin marketplace add Jam7-UK/amp-claude-plugin` and `/plugin install amp-by-jam7@jam7`.
