---
name: Coin runtime isolation
description: Isolation and ownership constraints for hosted Coin bots based on the imported CoinsBot source.
---

Never copy the archive's SQLite database into hosted runtimes. It contained no user rows, but its schema defaulted guild ownership to an upstream account. Initialize a fresh database per bot under its own runtime directory.

Do not persist the manager's current license owner in the Coin guild `owners` list. The bot's runtime buyer configuration already grants that owner privileged commands and updates when a bot is claimed. Keeping this authority out of the database prevents a former license owner from retaining those privileges after transfer; preserve guild owners configured independently by server administrators.

**Why:** hosted instances must not share balances or inherit upstream ownership, and ownership recovery must revoke the former license owner's manager-granted access.

**How to apply:** when changing Coin startup, database initialization, permission checks, or claim/recovery handling, keep per-instance storage and derive the manager owner's access from the current bot record.