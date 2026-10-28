---
name: AxillonBot local support
description: Product constraints for the hosted-bot support assistant.
---

Users should get help by writing normally in the configured support channel; they should not need a special command. Keep AxillonBot's diagnostic assistant local and do not connect it to an external AI service or API. Before reading per-bot logs or diagnostics, require that the stored owner matches the asking Discord account; never expose another owner's bot data.

**Why:** the user explicitly asked for a message-based support channel, a locally built assistant without external AI, and access limited to bots belonging to the person asking.

**How to apply:** preserve free-text handling in the configured channel, keep bot-specific support owner-scoped, and use local command metadata and diagnostics for future support improvements.
