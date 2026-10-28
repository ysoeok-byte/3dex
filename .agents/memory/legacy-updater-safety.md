---
name: Legacy updater safety
description: Why the imported Gestion bot's automatic update command must not be re-enabled as-is.
---

Do not re-enable the imported `updatebot` implementation unchanged. Its updater targeted fixed paths from a different hosting environment, removed bot source directories, copied replacement files, and restarted through PM2.

**Why:** Those paths do not belong to this workspace, and running the old update command could replace or delete bot files outside the project.

**How to apply:** If automatic updates are needed, build a workspace-aware updater with a validated source and a backup or rollback path. Do not restore the old shell command.