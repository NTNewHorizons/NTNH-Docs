# Infrastructure

This document covers the technical backbone of NTNH: repositories, CI/CD pipelines, secrets, and day-to-day development flow. If you're maintaining or debugging the automation, start here.

---

## Repositories

See [PROJECT_STRUCTURE.md](./PROJECT_STRUCTURE.md) for a full breakdown of every repo and what lives where.

---

## Automation Pipelines

The project runs four GitHub Actions workflows. You'll rarely need to touch them, but understanding what they do prevents unnecessary panic.

### 1. Translation Loop *(most important)*

Runs every night, fully automatically. This is what keeps the 20+ language translations in sync with the English source.

```
23:00 UTC   English source strings are extracted from NTNH/updates/upcoming
            and pushed to NTNH-Translations for Crowdin to pick up.

            [Translators work in Crowdin throughout the day]

00:00 UTC   All pending translation PRs are auto-merged into NTNH-Translations.
            A ZIP of all translated language files is published as a GitHub Release.

00:00 UTC   That ZIP is downloaded and unpacked back into
            NTNH/updates/upcoming/config/, then committed automatically.
```

**In plain terms:** English strings flow *out* every night → community translates via Crowdin → translated strings flow *back in* the next morning. You don't manage this - the pipeline handles it.

**If translations seem stale:** Check the Actions tab on both `NTNH` and `NTNH-Translations` for failed runs. Nine times out of ten it's an expired token (see Secrets below).

**If you add a brand new `.lang` file:** It needs to be added to `NTNH-Translations` manually once to enroll it in the pipeline. After that first-time setup, the nightly sync takes over.

---

### 2. Contributor List Updates

Runs daily at midnight. Reads contribution counts from GitHub and Crowdin, then auto-updates the contributor tables in the `.github` org profile and the `NTNH` README. Nothing you need to manage.

---

### 3–4. (Reserved)

Two additional workflows exist. Document them here when their purpose is confirmed.

---

## CI Secrets

If you have org admin access or are debugging a workflow failure, these are the credentials the pipelines depend on:

| Secret name | What it does |
|---|---|
| `UNIVERSAL_FINE` | Org-level GitHub PAT. Lets workflows read and write across multiple repos. Three of the four workflows depend on this. **Expired token = most likely cause of mysterious CI failures. Check this first.** |
| `CROWDIN_PROJECT_ID` | Numeric ID of the Crowdin project. Found in Crowdin project settings. |
| `CROWDIN_PERSONAL_TOKEN` | API token for reading Crowdin contributor data. |

Secrets are stored at the **organization level** in GitHub → Settings → Secrets and Variables → Actions. You need org admin access to view or rotate them.

---

## Day-to-Day Development Flow

1. **Branch off `updates/upcoming`** for your work, or commit directly to it for small changes.
2. **Use `experiments/*`** if you're unsure something works yet. These branches are throwaway.
3. **Don't touch `main`** - it's updated only when a release is cut.
4. **Don't touch `NTNH-Translations`** - Crowdin owns that repo entirely.
5. **Adding new translatable strings?** Put them in the `en_US` source file. They'll be picked up by the nightly sync automatically, as long as the corresponding file already exists in `NTNH-Translations`. New files need a one-time manual enrollment (see above).

---

## Useful Links

| Resource | Link |
|---|---|
| Main repo | https://github.com/NTNewHorizons/NTNH |
| Translations repo | https://github.com/NTNewHorizons/NTNH-Translations |
| Documentation | https://github.com/NTNewHorizons/NTNH-Docs |
| Translation project (Crowdin) | https://crowdin.com/project/ntnh |
| Discord | https://discord.gg/wtNVzeE5QB |
| Website | https://ntnewhorizons.com |
| Pack releases | https://github.com/NTNewHorizons/NTNH/releases |
