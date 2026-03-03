# Project Hierarchy

This document explains who's who in NTNH, what each role means in practice, and how decisions flow through the team.

---

## Role Overview

```
[@Admins] - full rights, final say
    └── [@Leads] - full rights, consult admins on major decisions
            └── [@Devs] - read access org-wide, changes via PR
            └── [@Devs-PT] - same as Devs, part-time
                    └── Contributors (community) - fork + PR only
```

---

## GitHub Teams

The org has four teams on GitHub: [`@Admins`](https://github.com/orgs/NTNewHorizons/teams/admins), [`@Leads`](https://github.com/orgs/NTNewHorizons/teams/leads), [`@Devs`](https://github.com/orgs/NTNewHorizons/teams/devs), [`@Devs-PT`](https://github.com/orgs/NTNewHorizons/teams/devs-pt).

---

## Roles in Detail

### 👑 Admins - *Bufka2011, BufkaSecond*

> **GitHub team:** [`@Admins`](https://github.com/orgs/NTNewHorizons/teams/admins)  
> **Repository access:** Full rights across all repositories.  
> **Ruleset bypass:** Exempt - rulesets are not evaluated for Admins at all.

- **Bufka2011** owns the project and has the final say on everything - technical, organizational, or otherwise.
- **BufkaSecond** is Bufka2011's secondary GitHub account and carries the same authority.
- Admins can approve and merge any PR, make org-level changes, manage secrets and CI, and override any decision.
- If there's a conflict or stalemate anywhere in the team, it escalates here.

---

### 🔷 Leads - *xekitan (Java Lead), Hi-Verse (Project Lead)*

> **GitHub team:** [`@Leads`](https://github.com/orgs/NTNewHorizons/teams/leads)  
> **Repository access:** Full rights across all repositories.  
> **Ruleset bypass:** Always allow - rulesets are evaluated but Leads are prompted to bypass when needed.

- Leads have full repository rights and share day-to-day governance of the project with admins.
- They can approve and merge PRs, push directly to development branches, and make significant technical calls.
- For major or wide-impact decisions (architectural changes, large feature additions, refactors), Leads should **consult with Admins** before acting.
- Each Lead has a specific domain of authority:

| Person | Focus |
|---|---|
| **xekitan** | Java Lead - final word on all Java-side code, JVM tooling, and NTM fork changes |
| **Hi-Verse** | Project Lead - overall direction, modpack design, feature scope |

---

### 🔨 Devs - *Rerserder*

> **GitHub team:** [`@Devs`](https://github.com/orgs/NTNewHorizons/teams/devs)  
> **Repository access:** Read access across all repositories. Changes require a PR.

- Active, regular developers who are consistently involved in the project.
- Cannot push directly to any branch - all changes go through a PR and must be reviewed by a **Lead or Admin**.
- Expected to be consistently active and familiar with the full project scope.

---

### 🔩 Devs-PT - *gamma63*

> **GitHub team:** [`@Devs-PT`](https://github.com/orgs/NTNewHorizons/teams/devs-pt)  
> **Repository access:** Same as `@Devs` - read access org-wide, changes via PR.

- Part-time developers who contribute on an irregular or reduced schedule.
- Functionally the same as `@Devs` in terms of permissions; the distinction is purely organizational to reflect availability.
- Subject to the same PR and contribution standards as everyone else.

---

### 🤝 Contributors - *Community*

- Anyone outside the org who wants to contribute.
- No repository access - contributions are made by forking and opening a PR.
- PRs follow the same review process as everyone else (see [CONTRIBUTING.md](./CONTRIBUTING.md)).
- Consistent, high-quality contributions can lead to an invitation to join `@Devs-PT`.

---

## How Decisions Are Made

| Decision | Who decides |
|---|---|
| Merge a normal PR | Any Lead or Admin approval |
| Reject a PR permanently | Any Lead or Admin, with a reason given |
| Refactor or architectural change | Leads + Admins consensus |
| Major feature or scope change | Leads consult Admins; Admins have final say |
| Org-level GitHub settings / CI changes | Admins only |
| Adding or removing a team member | Admins only |
| Final say on anything | Bufka2011 |

---

## A Note on Communication

Roles exist to keep things organized, not to create gatekeeping. If you have a good idea, say it. If something is broken, report it. The hierarchy is a decision-making structure, not a social ranking.

The best place to raise questions or proposals is the `#help` channel on [Discord](https://discord.gg/wtNVzeE5QB).