# Contributing

This document covers everything you need to know to get a PR merged into NTNH. Read it fully before opening your first PR.

---

## Before You Start

If you're planning a large feature, a refactor, or anything that touches systems outside your immediate task - **talk to the team first.** Post in `#general` on [Discord](https://discord.gg/wtNVzeE5QB) (don't forget to ping @Bufka2011) or open a discussion on GitHub.

There are no guarantees that a PR gets merged no matter how much work you put into it. Catching a misalignment early saves everyone's time, especially yours.

For refactor PRs specifically: consult the [`@Leads`](https://github.com/orgs/NTNewHorizons/teams/leads) or [`@Admins`](https://github.com/orgs/NTNewHorizons/teams/admins) team before starting work. Unsolicited refactor PRs will almost certainly be rejected.

---

## PR Requirements

- Every PR must be reviewed and approved by **at least one member of [`@Leads`](https://github.com/orgs/NTNewHorizons/teams/leads) or [`@Admins`](https://github.com/orgs/NTNewHorizons/teams/admins)** before merging.
- Your PR description must clearly explain **what you changed** and **why**, and note any side effects or areas it might affect.

---

## How to Open a PR

1. Branch off `updates/upcoming` (or the appropriate `updates/*` branch).
2. Make your changes.
3. Open a PR targeting `updates/upcoming`.
4. Fill in the PR description properly (see above).
5. Wait for an admin to review. Don't merge your own PR.

---

## Keep It Focused

The best PRs do exactly one thing. If your PR adds a new machine, it should only contain changes related to that machine. Don't bundle in unrelated tweaks, config changes, or fixes - open a separate PR for those.

---

## Keep It Clean

**Don't include:**
- Duplicate functions or redundant code
- Unused or half-finished features
- Broken code left for "someone else to fix later"
- Changelog edits (you will cause a merge conflict, every time)

**Do include:**
- Clean, readable code
- Descriptive commit messages (not required, but it helps - though commit messages like "femboy milk" have historically made it through)

---

## Test Your Work

**This is mandatory.** Before opening a PR, you must test your changes:

- ✅ On a **client**
- ✅ On a **server**
- ✅ If your PR includes compatibility code for a specific mod: test the game **with and without** that mod installed

PRs with untested or obviously broken code will be rejected.

---

## Code Standards

*(This section is a placeholder - define project-specific code standards here, e.g. ZenScript formatting conventions, naming patterns for recipe overrides, etc.)*

---

## I Want to Help But Don't Know Where to Start

A few good entry points:

- **Translations** - No Java or modding knowledge required. Head to the [Crowdin project](https://crowdin.com/project/ntnh) and start translating. It's the fastest way to make a real contribution.
- **Upstream contributions** - Fix issues in [NTM](https://github.com/HbmMods/Hbm-s-Nuclear-Tech-GIT) or [NTNH's NTM fork](https://github.com/NTNewHorizons/Hbm-s-Nuclear-Tech-GIT). Improvements there flow downstream into NTNH.
- **Website** - The [website repo](https://github.com/NTNewHorizons/NTNewHorizons.github.io) is always open to improvements.
- **Suggestions** - Post ideas in the `#suggestions` channel on [Discord](https://discord.gg/wtNVzeE5QB). No shitposts though.
