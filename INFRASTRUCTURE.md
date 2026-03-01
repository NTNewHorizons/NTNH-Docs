# NTNH Project Infrastructure
**Last update: March 1st 2026**

This document contains critical information about the project's infrastructure. If you are reading this, you are probably going to be maintaining or developing this system.  
My condolences.

---

## What is this project?

**Nuclear Tech: New Horizons (NTNH)** is a hardcore, quest-driven Minecraft 1.7.10 modpack built around HBM's Nuclear Tech Mod. Think GregTech: New Horizons, but NTM-flavored. The project lives on GitHub under the [`NTNewHorizons`](https://github.com/NTNewHorizons) organization, with a community on [Discord](https://discord.gg/wtNVzeE5QB) and a website at [ntnewhorizons.com](https://ntnewhorizons.com).

---

## Who's who

| Person | Role |
|---|---|
| **Bufka2011** | Lead developer. Owns the project. Final say on everything. |
| **BufkaSecond** | Secondary developer (Bufka2011's second account). Effectively the same person. |
| **Hi-Verse** | Main developer |
| **Rerserder** | Main developer |
| **xekitan** | Main developer |
| **rt194646** | Main developer |
| **gamma63** | Main developer |

---

## Key repositories

You don't need to know all the repos. You need to know these:

### [`NTNewHorizons/NTNH`](https://github.com/NTNewHorizons/NTNH) - *The modpack itself*
This is the main repo. Everything that ends up in the player's hands lives here: ZenScript recipe overrides, quest data, mod configs, and translation files.

**Branch structure:**
- `main` - The latest released update. Stable. Do not commit here directly.
- `updates/upcoming` - The next update in progress. This is where most active development happens and where the translation automation targets.
- `updates/*` - Branches for future planned updates further down the roadmap.
- `experiments/*` - Testing and experimental branches. Treat as throwaway.

> When in doubt, your work goes to `updates/upcoming`.

### [`NTNewHorizons/NTNH-Translations`](https://github.com/NTNewHorizons/NTNH-Translations) - *Localization files*
Contains all translated strings for the modpack in 20+ languages, managed through [Crowdin](https://crowdin.com/project/ntnh).

> ⛔ **NEVER edit this repository by hand.** All changes must go through Crowdin. Manual edits will be overwritten by automation within 24 hours and will create conflicts.

### [`NTNewHorizons/NTNH-Docs`](https://github.com/NTNewHorizons/NTNH-Docs) - *Documentation*
Contains the project documentation, Developer Code of Conduct, design files, and other reference material.

> **If you're new, read the Code of Conduct here before touching anything else.**

### [`NTNewHorizons/.github`](https://github.com/NTNewHorizons/.github) - *Org profile*
Contains the organization's GitHub profile page (`profile/README.md`) and branding assets. The contributor lists on the org page are auto-updated here by CI every day. You will rarely need to touch this.

---

## How the automation works

The project runs four GitHub Actions workflows. Most of them you'll never need to touch, but you should understand what's happening so you don't panic when something looks weird.

### The translation loop

This is the most important automation. It runs every day, fully automatically:

```
23:00 UTC   English source strings are extracted from NTNH/updates/upcoming
            and pushed to NTNH-Translations for Crowdin to pick up.

            [Translators work in Crowdin throughout the day]

00:00 UTC   All pending translation PRs are auto-merged into NTNH-Translations.
            A ZIP of all translated language files is published as a GitHub Release.

00:00 UTC   That ZIP is immediately downloaded and unpacked back into
            NTNH/updates/upcoming/config/, committed automatically.
```

In plain terms: English strings flow *out* of the pack every night, get translated by the community through Crowdin, then flow back *in* the next morning. You don't need to manage translations - the pipeline handles it. If translations seem out of date, check the Actions tab on both `NTNH` and `NTNH-Translations` for failed runs.

### Contributor list updates
Runs daily at midnight. Reads contribution counts from GitHub and Crowdin, then auto-updates the contributor tables in the `.github` org profile and the `NTNH` README. Nothing you need to worry about.

---

## Secrets you should know exist

If you're given org admin access or need to debug CI failures, these are the credentials the workflows depend on:

| Secret | What it does |
|---|---|
| `UNIVERSAL_FINE` | An org-level GitHub PAT that lets workflows read and write across multiple repos. Three of the four workflows depend on this. **If CI breaks mysteriously, a expired token is the first thing to check.** |
| `CROWDIN_PROJECT_ID` | The numeric ID of the Crowdin project. Found in Crowdin project settings. |
| `CROWDIN_PERSONAL_TOKEN` | API token for reading Crowdin contributor data. |

---

## Day-to-day development flow

1. **Branch off `updates/upcoming`** for your work, or commit directly to it for small changes.
2. **Use `experiments/*`** if you're not sure something works yet.
3. **Don't touch `main`** - it gets updated when a release is cut.
4. **Don't touch `NTNH-Translations`** - Crowdin owns that repo.
5. When adding new translatable strings, they'll be picked up by the nightly sync automatically - as long as the corresponding `en_US` file already exists in `NTNH-Translations`. If it's a brand new file, it needs to be added to `NTNH-Translations` manually once to enroll it in the pipeline.

---

## Useful links

| Resource | Link |
|---|---|
| Main repo | https://github.com/NTNewHorizons/NTNH |
| Documentation | https://github.com/NTNewHorizons/NTNH-Docs |
| Translation project | https://crowdin.com/project/ntnh |
| Discord | https://discord.gg/wtNVzeE5QB |
| Website | https://ntnewhorizons.com |
| Pack releases | https://github.com/NTNewHorizons/NTNH/releases |

---

*Good luck out there.*
