---
name: board-and-card-status
description: Report what is moving on AMP boards, find a card, and read its latest deliverable. Use for stand-ups, status checks, "what needs my review", or "show me the draft for X".
---

# Board and card status

1. Board overview: call `get_board_status` without `boardSlug` to list the boards the user can read, or with a `boardSlug` for active cards per stage, each card's work state (working, waiting, paused, needs attention) and reviews waiting on the user.
2. Find a card: call `search_cards` with a short `query` (title words or card number). Use `boardSlug`, `cardTypeKey`, `includeArchived` or `includeTerminal` only when the user asks for them. For in-flight work only, `find_cards` returns the current card id and version.
3. Open a card: call `get_card` with the exact `cardId` for its metadata and artifact summaries.
4. Read the deliverable: call `read_card_artifact` with the `cardId`; pass a `section` or a retained `version` when the user wants a specific part or an earlier version.

How to answer:

- Lead with what needs attention: reviews waiting on the user, then cards that are paused or need attention, then work in progress.
- Use the card number and title users see in AMP, and include the AMP link when one is returned.
- Quote deliverable text faithfully. If content is truncated or missing, say so rather than guessing.
- These tools are read-only. To change a card, use the create-card or review-and-update-cards workflow.
