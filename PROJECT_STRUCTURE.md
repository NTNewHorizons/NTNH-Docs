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

### Directory Layout

```
NTNH/
├── config/                  # Mod configuration files
│   ├── ftbquests/           # Quest book data (chapters, tasks, rewards)
│   ├── crafttweaker/        # ZenScript recipe overrides and additions
│   └── ...                  # Per-mod config files
├── mods/                    # Mod JARs (not committed; managed by the pack manifest)
├── resources/               # Assets: textures, sounds, pack icon
│   └── minecraft/
│       └── lang/            # en_US strings (source for translation pipeline)
├── scripts/                 # CraftTweaker scripts
└── manifest.json            # Mod list and versions
```

> ⚠️ The `resources/.../lang/` folder contains **only English source strings**. All other language files live in `NTNH-Translations` and are injected back into `config/` nightly by the automation pipeline. Do not add non-English `.lang` files to this repo manually.

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

---

## File Naming Conventions

- Documentation files: `SCREAMING_SNAKE_CASE.md`
- ZenScript files: `descriptive_name.zs` (lowercase, underscores)
- Config files: follow the mod's own naming convention - don't rename them
- Quest files: follow FTB Quests' generated naming - don't rename them

---

## What Goes Where: Quick Reference

| I want to… | I should edit… |
|---|---|
| Add or change a recipe | `scripts/` in `NTNH` |
| Add or change a quest | `config/ftbquests/` in `NTNH` |
| Change a mod config | `config/<modname>/` in `NTNH` |
| Add English text for a new feature | `resources/.../lang/en_US.lang` in `NTNH` |
| Fix a translation | Crowdin - never edit `NTNH-Translations` directly |
| Document something for developers | This repo (`NTNH-Docs`) |
