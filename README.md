# zetapro-data

> **Obsolete.** This repository was the sync store for [Zetapro](https://github.com/amirkhan0725/zetapro)'s original GitHub-based sync (versions 1.0–1.1). Since **v1.2**, Zetapro syncs through a normal sign-in instead, so nothing new depends on it. It's kept as a read-only record of practice history.

## What it is

[Zetapro](https://amirkhan0725.github.io/zetapro/) is a mental-math trainer (a Zetamac-style speed game plus an Optiver-style 80 in 8). Its first sync feature kept every device in step through one file in this repository:

- **`zetapro-data.json.gz`**: a gzipped JSON snapshot of every game played (each problem, answer time and mistakes), the app's settings, and records of deleted games.
- **How it worked:** each device read the file, merged in the games it was missing, and wrote it back through the GitHub API using a personal access token. The commit history therefore doubles as a full version history; that's how a set of accidentally deleted games was recovered.

## Why it's obsolete

GitHub sync worked, but it asked every user to create a GitHub repository and a fine-grained access token on every device, which is too much to ask of anyone but the developer. Zetapro 1.2 replaced it with **account sync**:

- **Sign in with Google or email.** No tokens, no repositories.
- **Per-game, incremental sync** instead of rewriting one big file, and changes appear on other devices within seconds.
- **The same merge rules,** so no device can overwrite another's games, deletions and undo still propagate, and restores still work.

Devices that were already connected to this repository can still read it, which lets them hand their games over to the new account. After that, it isn't used.

## Status

- **Do not edit by hand.** The file is machine-written and compressed.
- Kept **public** as an archive of practice history and as a worked example of the old design.
- It will be **archived (read-only)** once no device uses GitHub sync any more.
