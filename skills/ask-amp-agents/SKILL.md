---
name: ask-amp-agents
description: Talk to the user's AMP marketing agents from Claude, for example to get headline ideas, a draft or an agent's view on a card, and collect or recover their replies. Use when the user wants an AMP agent, rather than Claude, to do the work.
---

# Ask AMP agents

1. Call `list_agents` to see which AMP agents the user can talk to and what each does. Pick the agent that matches the request, or ask the user if several fit.
2. Call `ask_agent` with the `message`, the `agent` name and, if the request is about one card, its `cardId`. Pass a new `requestId` so a network retry does not start a duplicate paid turn. To continue an earlier conversation, pass its `conversationId` instead of starting a new one.
3. If the reply is not ready, `ask_agent` returns a `replyHandle`. Call `get_agent_reply` with it, respecting the returned poll interval, until the status is completed, failed, cancelled or incomplete.
4. Relay the agent's reply faithfully and say which agent answered. If the reply says the agent is waiting for the user's decision in AMP, tell the user and share the AMP link; do not answer the decision on their behalf.

Recovery and control:

- Lost a response? Call `recover_agent_reply` with the original `requestId`; it does not start a new paid turn.
- Can't find an earlier conversation? `list_agent_conversations` lists the user's recent MCP conversations with reply handles.
- To stop work the user no longer wants, call `cancel_agent_reply` with the `replyHandle`. Completed work is not undone.

Rules:

- Each `ask_agent` call is a real agent turn that uses the workspace's normal usage allowance. Don't send speculative or duplicate messages.
- Agents work with their own AMP tools and may research the public web. When a marketing deliverable needs them, such as a blog post or social post, an agent can also create featured and supporting images for it; those images are attached to the card and reviewed and approved by people in AMP. AMP is not a standalone image generator, so don't use it to make images that aren't part of a marketing deliverable. Tell the user if a reply will take a while, and offer to check back.
- Agents act as the user in AMP; AMP's approvals and permissions still apply.
