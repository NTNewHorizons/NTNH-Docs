# Project Structure

This document covers the layout of NTNH's repositories, how branches are organized, and where different types of files live.

---

## Repositories at a Glance

| Repository | Purpose |
|---|---|
| [`NTNewHorizons/NTNH`](https://github.com/NTNewHorizons/NTNH) | The modpack itself - configs, quests, recipes, translations |
| [`NTNewHorizons/NTNH-Translations`](https://github.com/NTNewHorizons/NTNH-Translations) | Localization files, managed entirely by Crowdin automation |
| [`NTNewHorizons/NTNH-Docs`](https://github.com/NTNewHorizons/NTNH-Docs) | This documentation repo |
| [`NTNewHorizons/.github`](https://github.com/NTNewHorizons/.github) | Org profile, contributor lists (auto-updated by CI) |

For Java-side work, see also the upstream repos:
- [`HbmMods/Hbm-s-Nuclear-Tech-GIT`](https://github.com/HbmMods/Hbm-s-Nuclear-Tech-GIT) - NTM upstream
- [`HbmMods/Hbm-s-Nuclear-Tech-GIT`](https://github.com/JameH2/Hbm-s-Nuclear-Tech-GIT) - NTM Space upstream
- [`NTNewHorizons/Hbm-s-Nuclear-Tech-GIT`](https://github.com/NTNewHorizons/Hbm-s-Nuclear-Tech-GIT) - NTNH's NTM fork

---

## Main Repo: `NTNewHorizons/NTNH`

This is where the modpack lives. Everything that ends up in a player's game instance comes from here.

### Branch Conventions

| Branch | Purpose |
|---|---|
| `main` | Latest stable release. **Do not commit here directly.** Updated only when a release is cut. |
| `updates/upcoming` | The next update in active development. **This is where your work goes by default.** |
| `updates/*` | Planned future updates further down the roadmap. Touch only if you're assigned to that update. |
| `experiments/*` | Throwaway testing branches. Anything here can be deleted without notice. |

> **Rule of thumb:** When in doubt, branch off `updates/upcoming`.

---

## Translations Repo: `NTNewHorizons/NTNH-Translations`

Contains translated `.lang` files for 20+ languages.

**⛔ Never edit this repo by hand.** All changes go through [Crowdin](https://crowdin.com/project/ntnh). Manual edits are overwritten by automation within 24 hours.

See [INFRASTRUCTURE.md](./INFRASTRUCTURE.md) for how the translation pipeline works end-to-end.

---

## Docs Repo: `NTNewHorizons/NTNH-Docs`

You're reading it. This repo contains:

```
NTNH-Docs/
├── README.md                # Index / entry point
├── INFRASTRUCTURE.md        # CI, automation, secrets
├── HIERARCHY.md             # Roles and decision-making
├── PROJECT_STRUCTURE.md     # This file
├── TASK_MANAGEMENT.md       # GitHub Projects kanban guide
└── CONTRIBUTING.md          # PR standards and process
```

If you're adding documentation, keep one topic per file. Don't turn `README.md` into a wall of text - link out to the relevant file instead.