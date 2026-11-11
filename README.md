# AMP by Jam 7 for Claude

AMP is Jam 7's Agentic Marketing Platform®. Marketing teams use it to keep their approved brand knowledge in one Marketing Brain, run work as cards on boards, and hand tasks to AMP marketing agents under human review.

This repository is the official AMP plugin for Claude. It connects Claude to your AMP workspace through AMP's remote MCP server, and adds skills that teach Claude how to use AMP well.

- Connector URL: `https://actions.jam7.com/mcp`
- Plugin name: `amp-by-jam7` (version 1.0.0)
- Marketplace name: `jam7`

## Before you start

You need an AMP workspace from Jam 7 on a paid plan, and an AMP user account in that workspace. Viewers get read-only tools. Creating or changing work needs a Member or Admin role, and you choose whether to allow it when you sign in.

## Install

### Claude Code

```text
/plugin marketplace add Jam7-UK/amp-claude-plugin
/plugin install amp-by-jam7@jam7
```

Then run `/mcp`, choose `amp`, and sign in. From a terminal, the same steps are `claude plugin marketplace add Jam7-UK/amp-claude-plugin` and `claude plugin install amp-by-jam7@jam7`.

If you want only the connector without the skills: `claude mcp add --transport http amp https://actions.jam7.com/mcp`.

### Claude (claude.ai, desktop and mobile)

1. Open **Settings → Connectors** and choose **Add custom connector**. (Once AMP is listed in the Claude directory you can connect it from there instead.)
2. Enter the name `AMP by Jam 7` and the URL `https://actions.jam7.com/mcp`.
3. Choose **Connect** and sign in.

On Team and Enterprise plans, an owner may need to add the connector for the organisation first.

## Signing in

AMP uses OAuth 2.0 with PKCE. Claude opens Jam 7's sign-in page at `os.jam7.com`, where you sign in with your AMP account, pick one workspace and approve the permissions Claude may use. Claude never sees your password. Claude then acts as you, with your AMP role, and only in that workspace. You can disconnect at any time from Claude's connector settings or from **AMP Settings → Connected apps**, and access stops straight away.

## What Claude can do

### Read (no changes)

- **Search the Marketing Brain** and **read a Brain document**: answers about your brand, audiences, positioning and messaging, with the sources named.
- **Board status**, **search cards**, **find in-flight cards**, **get a card** and **read a card's deliverable**: see what is in progress, blocked, waiting for review or done.
- **Find AMP references**: find cards and documents that mention something.
- **Card creation options**, **card editing options** and **card review**: the boards, card types, fields and review evidence that writes need.
- **Workspace context** and **connected profile**: which workspace and account are connected.
- **AMP skill guides**: list and read summaries of the skills on your boards.
- **List agents**, **get an agent's reply**, **recover a reply** and **find your conversations**.

### Write (each one asks you first)

Every write tool is marked destructive, so Claude asks before it runs. AMP also shows a preview first and makes the change only after you confirm it. There is no delete tool.

- ✏️ **Create card**: brief new work into AMP as a card.
- ✏️ **Comment on a card**.
- ✏️ **Edit card details**: title, brief, deadline or fields.
- ✏️ **Decide a card review**: approve, or request changes.
- ✏️ **Move a card** to another stage, under the board's rules.
- ✏️ **Nudge** whoever has claimed a card.
- ✏️ **Ask an AMP agent**: starts a real agent run as you. Agents can research the public web.
- ✏️ **Stop an AMP reply** that is still running.

### Images

AMP is not a standalone image generator. As part of a marketing deliverable, such as a blog post or social post, an AMP agent can create featured and supporting images for that deliverable. These are design assets attached to the card, and people in your workspace review and approve them in AMP before they are used. AMP does not generate video or audio.

## Skills

| Skill | Use it to |
| --- | --- |
| `get-started` | Check which workspace, role and permissions are connected |
| `marketing-brain` | Answer brand and audience questions from the approved Marketing Brain, with sources |
| `board-and-card-status` | Get board status, find a card and read its latest deliverable |
| `create-card` | Brief new work into AMP as a card |
| `review-and-update-cards` | Approve or request changes, move, comment on, edit or nudge cards |
| `ask-amp-agents` | Talk to your AMP marketing agents and collect their replies |

## Try it

- "Using AMP, what does our Marketing Brain say about our primary audience? Cite the documents."
- "Give me a status update on my AMP boards. What's blocked or waiting for review?"
- "Ask the AMP content agent for three headline options for the launch blog card."
- "Create an AMP card to draft a LinkedIn post announcing our webinar next Thursday."

## What is sent and stored

The plugin runs no local code, hooks or scripts. Claude talks only to `https://actions.jam7.com/mcp` and to Jam 7's sign-in pages at `https://os.jam7.com`. Each tool call sends AMP what you asked for, such as a search query, a card brief or a message to an agent. AMP returns Marketing Brain excerpts, card details and deliverables, agent replies, and your AMP name, email and workspace name. AMP never receives your Claude conversation or memory, and keeps an audit record of each tool call.

- Privacy Notice: https://os.jam7.com/privacy
- Terms of Use: https://os.jam7.com/terms

## Support and security

- Support: compliance@jam7.com or https://jam7.com/contact
- Security issues: see [SECURITY.md](SECURITY.md)
- Changes: see [CHANGELOG.md](CHANGELOG.md)

## Licence

MIT, copyright Jam 7 Limited. See [LICENSE](LICENSE). The licence covers the files in this repository. It grants no rights to the AMP service, which is governed by the Terms of Use.
