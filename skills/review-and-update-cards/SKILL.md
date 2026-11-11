---
name: review-and-update-cards
description: Act on existing AMP cards with preview and confirmation: review work and approve or request changes, move a card to another stage, comment, edit a card's brief or fields, or nudge stalled work. Use when the user wants to change a card rather than just read it.
---

# Review and update cards

Every write here is confirmed first. The first call changes nothing and returns a preview. Show the preview, and only after the user agrees, repeat the exact same arguments plus the returned `confirmationToken`. Nothing is deleted; there is no delete tool, so never claim to delete a card.

Review a card

1. Call `get_card_review` with the `cardId` to read the work awaiting review, the previous version, quality evidence and review history. Summarise it for the user.
2. Call `decide_card_review` with `cardId`, `decision` (`approve` or `request_changes`), the `reviewIdentity` from step 1, and a `reason` when requesting changes. Confirm as above.

Move a card

- Call `get_card` for the current version, then `move_card` with `cardId`, `toStage` and `expectedVersion`. Add a `note` with rework instructions only when moving back to an earlier stage. Cards waiting on a review are decided with `decide_card_review`, not moved.

Comment

- Call `comment_on_card` with `cardId` and the `comment` text. The comment is posted as the user.

Edit details

- Call `get_card_edit_options` first for the current values, `expectedVersion` and `editRevision`. Then call `edit_card` with only the fields to change; `customFields` is a patch, and null clears an optional field. Show the before and after values from the preview. Editing can supersede a pending review, so tell the user. It cannot change ownership, stage or card documents.

Nudge stalled work

- Call `find_cards` to get the exact in-flight card id and version, then `nudge_card` with `cardId` and `expectedVersion`. A nudge wakes the stage's assigned agent sooner; it never assigns, completes or moves the card. Use `allowAdminReenable` only if the user is a workspace admin and explicitly asks.

Rules:

- If a version conflict is returned, re-read the card and show the user what changed before trying again.
- Approving, requesting changes and moving cards change live work. Make the consequence clear in the preview you show.
