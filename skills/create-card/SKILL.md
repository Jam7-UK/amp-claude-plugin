---
name: create-card
description: Brief new marketing work into AMP by creating a governed card, such as a LinkedIn post, blog, campaign asset or SEO and competitor research. Use when the user wants AMP to produce something, not just answer a question.
---

# Create an AMP card

1. If the user is unsure what AMP can produce, call `list_skill_guides` (optionally with a `boardSlug`) and, for the chosen skill, `get_skill_guide` to see what it produces, which Brain documents ground it, the expected outputs, the quality checklist and which board and card type run it.
2. Immediately before creating, call `get_card_create_options` (optionally with a `boardSlug`). It returns the live boards, stages, card types, parent rules, writable custom fields and the `catalogueRevision`.
3. Build the request from that catalogue only: `boardSlug`, `cardTypeKey`, `title`, and where useful `summary`, `description` (the brief), `priority`, `tags`, a confirmed `dueAt` deadline, `customFields` using the opaque choice values returned (show users the choice titles), and parent fields if the card type requires them. Choose a new `idempotencyKey` for this request and pass the `catalogueRevision`.
4. Call `create_card` without a `confirmationToken`. This changes nothing and returns a preview. Show the preview to the user in plain words.
5. Only after the user clearly agrees, call `create_card` again with the same arguments plus the returned `confirmationToken`. Report the new card number and link.

Rules:

- Never invent boards, card types, stages or field values; use only what `get_card_create_options` returned. If nothing fits, say so.
- Do not set a deadline the user has not confirmed.
- For search or competitor research, pick an available SEO research card type and describe the business question. AMP's assigned agent runs the research asynchronously; follow progress with `get_card` and `read_card_artifact`.
- If a retry is needed after a network error, reuse the same `idempotencyKey` so no duplicate card is created.
