---
name: get-started
description: Set up and check the AMP by Jam 7 connection. Use right after installing the plugin, or when the user asks which AMP workspace, account or permissions Claude is using.
---

# Get started with AMP

AMP is Jam 7's Agentic Marketing Platform®. This plugin connects Claude to one AMP workspace, acting as the signed-in user with that user's AMP permissions.

1. Call `get_workspace_context` to confirm the connected user, workspace, role and available capabilities (scopes). Tell the user in plain words which workspace and role are in effect.
2. If the user wants their stable identity details, call `get_profile` (opaque id, email and workspace name). Use `get_workspace_context` for role and capabilities.
3. Explain what they can do next, based only on the capabilities returned:
   - Reading: search the Marketing Brain, see board status, open cards and their deliverables.
   - Creating and changing work (only if the scopes allow it): create cards, comment, edit, decide reviews, move cards, nudge work and talk to AMP agents.
4. Offer two or three starter requests, such as "What does our Marketing Brain say about our brand voice?" or "What is moving on our boards this week?"

Rules:

- The workspace and user always come from the connection. Never ask for, or pass, a workspace or user id.
- Viewers get read-only tools. If a write tool is refused, explain that the user's AMP role or the permissions chosen at sign-in do not allow it; they can reconnect and grant the extra permission, or ask a workspace admin.
- Never show tokens or connection secrets.
