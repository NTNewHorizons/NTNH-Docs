# Task Management

NTNH uses **GitHub Projects** (kanban board) to track active work. This document explains how to use it - if you're new to GitHub Projects, read this before touching the board.

---

## Why We Use a Kanban Board

A kanban board gives the whole team visibility into:
- What's actively being worked on (and by whom)
- What's waiting for review
- What's planned but not started yet
- What's done

Without it, work gets duplicated, PRs appear from nowhere, and nobody knows what state anything is in.

---

## The Board

> 📌 **Link to the board:** https://github.com/orgs/NTNewHorizons/projects/2

---

## Columns

| Column | Meaning |
|---|---|
| **Backlog** | Ideas and tasks open for discussion. Items sit here until Leads or Admins reach a final decision on them. |
| **Ready** | Triaged, fully specified, and approved. A holding area for tasks that can be picked up immediately when someone is available. |
| **In Progress** | Someone is actively working on this right now. If you pick up a task, move it here and assign yourself. |
| **Awaiting Review** | Work is done and a PR is open, but formal review hasn't started. Used to signal the task is complete on the contributor's end. |
| **In Review** | A Lead or Admin is actively reviewing the PR. Reviewer should assign themselves to the card. |
| **Done** | Merged and closed. Final log of completed work. |

---

## Column Transitions

### Backlog → Ready

Items start in **Backlog** and stay there until a final decision is made. The discussion happens on the card itself - contributors, Devs, Leads, and Admins can all comment.

**Checklist to move to Ready:**
- [ ] A member of [`@Leads`](https://github.com/orgs/NTNewHorizons/teams/leads) or [`@Admins`](https://github.com/orgs/NTNewHorizons/teams/admins) has stated a final decision in the card comments.
- [ ] The scope is clear and the task is fully specified.
- [ ] If the task is large (a refactor, major feature, etc.) - it has explicit admin sign-off.

If none of the above is met, **keep the conversation going in Backlog**. Do not move items to Ready speculatively.

**Example of what a Backlog discussion looks like:**

A card like *Better World Generation* might list a set of mods to integrate and open questions (compatibility concerns, whether to replace existing mods, untested features). Leads and Admins will respond to each point. Once every open question has a definitive answer and the full scope is agreed upon, the card is ready to be moved.

---

### Ready → In Progress

**Ready** is a staging area - items here are approved and fully specified but not yet started.

**To move to In Progress:**
- Assign yourself (or your team) to the card.
- Move the card to **In Progress**.
- Create your branch and start working (see [CONTRIBUTING.md](./CONTRIBUTING.md)).

Do not move a card to In Progress unless you are actively starting work on it now.

---

### In Progress → Awaiting Review

**To move to Awaiting Review:**
- [ ] The work is complete.
- [ ] A PR has been opened against `updates/upcoming`.
- [ ] The PR link is attached to the card (use `Closes #<issue>` in the PR description, or link manually).

---

### Awaiting Review → In Review

**To move to In Review:**
- A member of [`@Leads`](https://github.com/orgs/NTNewHorizons/teams/leads) or [`@Admins`](https://github.com/orgs/NTNewHorizons/teams/admins) picks up the review.
- The reviewer assigns themselves to the card.
- The reviewer actively reviews the linked PR.

If the reviewer determines the work needs changes, the card goes **back to In Progress** and the contributor is notified.

---

### In Review → Done

**To move to Done:**
- [ ] The PR has been approved and merged.

The card can be moved to Done automatically if GitHub Projects is configured to do so on PR merge, or moved manually.

---

## How to Use the Board: Step by Step

### Adding a new item

1. Add new cards to **Backlog** first - never directly to In Progress or Ready.
2. Give it a clear, short title. (Good: *"Fix dupe bug with Weldtronic output slot"*. Bad: *"Fix stuff"*.)
3. Fill in the card description using the template below.
4. If it requires admin sign-off before work begins (refactor, major feature), flag it in `#general` on Discord before creating the card - or at least leave a comment on the card requesting input.
5. Let the discussion happen. Don't rush it to Ready.

### Picking up a task

1. Find a card in **Ready** (or **Backlog** if it's yours and already approved).
2. Assign yourself to the card.
3. Move it to **In Progress**.
4. Branch off `updates/upcoming` and start working.

### Opening a PR

1. Open a PR to `updates/upcoming`.
2. Link the PR to the card with `Closes #<issue>` in the PR description.
3. Move the card to **Awaiting Review**.

### After merge

Move the card to **Done**, or it will move automatically if that's configured.

---

## Card Template

When creating a new card, use this structure in the description:

```
## What
[One or two sentences: what does this task accomplish?]

## Why
[Why is this needed? What problem does it solve or what value does it add?]

## Scope
[What's included in this task? What's explicitly out of scope?]

## Notes
[Dependencies, risks, related issues, open questions, or anything else relevant.]
```

---

## Rules

- **Don't leave cards unassigned in In Progress.** If you stopped working on something, move it back to Backlog or Ready and unassign yourself.
- **One card per distinct piece of work.** Don't bundle unrelated changes into one card (same rule as PRs).
- **Keep card titles short and descriptive.**
- **Keep the board clean.** Archive Done cards periodically so the board stays readable.
- **Don't skip Backlog.** Even if you're certain something should be done, it goes to Backlog first so Leads and Admins can weigh in.

---

## Questions?

Ask in the `#help` channel on [Discord](https://discord.gg/wtNVzeE5QB).