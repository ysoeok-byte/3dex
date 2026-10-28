---
name: Cross-platform npm lockfiles
description: Avoiding Replit-private package tarball URLs in deployments built outside Replit.
---

When this project is built outside Replit, check `package-lock.json` for resolved URLs using `package-firewall.replit.internal`. Replace those tarball URLs with their corresponding `https://registry.npmjs.org/` URLs before deploying.

**Why:** Railway cannot resolve Replit's internal package firewall hostname, so `npm install` fails with `ENOTFOUND` even though the packages are public.

**How to apply:** For external build providers, inspect every `resolved` entry in the lockfile, not only the package named in the first error; validate that no private hostname remains and that the corresponding public tarball is reachable.
