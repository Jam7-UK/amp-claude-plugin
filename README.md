# AMP by Jam 7 for Claude

AMP is Jam 7's Agentic Marketing Platform®. This plugin connects Claude to your AMP workspace and adds skills that teach Claude how to use AMP well.

## What it includes

- **Connector:** the AMP remote MCP server at `https://actions.jam7.com/mcp` (`.mcp.json`). You sign in with your AMP account through OAuth and pick one workspace. Claude acts as you, with your AMP role and the permissions you approve on the consent screen.
- **Skills** (`skills/`):
  - `get-started`: check which workspace, role and permissions are connected.
  - `marketing-brain`: answer brand, audience and positioning questions from your approved Marketing Brain, with sources.
  - `board-and-card-status`: board status, finding a card and reading its latest deliverable.
  - `create-card`: brief new work into AMP as a governed card.
  - `review-and-update-cards`: approve or request changes, move, comment on, edit or nudge cards.
  - `ask-amp-agents`: talk to your AMP marketing agents and collect their replies.

## What it sends and stores

The plugin runs no local code, hooks or scripts. Claude talks only to `https://actions.jam7.com/mcp` and to Jam 7's sign-in pages at `https://os.jam7.com`. Tool calls send the request you make (for example a search query, a card brief or a message to an agent) to AMP. AMP returns Marketing Brain excerpts, card details and deliverables, agent replies, and your AMP name, email and workspace name. AMP keeps an audit record of each tool call. See the [AMP Privacy Notice](https://os.jam7.com/privacy) and [Terms of Use](https://os.jam7.com/terms).

Every change to AMP (creating, commenting on, editing, reviewing, moving or nudging a card) shows a preview first and happens only after you confirm. There is no delete tool. AMP agents can research the public web. As part of a marketing deliverable, such as a blog post or social post, they can also create featured and supporting images, which your team reviews and approves in AMP. AMP is not a standalone image generator.

## Requirements

An AMP workspace on a paid plan. Viewers get read-only tools. Disconnect any time from Claude or from AMP Settings.

## Support

Contact Jam 7 at https://jam7.com/contact or compliance@jam7.com.
