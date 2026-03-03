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

> 📌 **Link to the board:** *(add link here)*

---

## Columns

| Column | Meaning |
|---|---|
| **Backlog** | Ideas and tasks that are approved to be worked on eventually, but no one is actively doing them yet. |
| **In Progress** | Someone is actively working on this right now. If you pick up a task, move it here and assign yourself. |
| **In Review** | A PR has been opened. Waiting for admin review and approval. |
| **Done** | Merged and closed. |

---

## How to Use the Board: Step by Step

### Picking up a task
1. Find a card in **Backlog** that you want to work on.
2. Assign yourself to the card.
3. Move the card to **In Progress**.
4. Create a branch and start working (see [CONTRIBUTING.md](./CONTRIBUTING.md) for branch and PR conventions).

### Opening a PR
1. When your work is ready, open a PR to `updates/upcoming`.
2. Move the card to **In Review**.
3. Link the PR to the card (GitHub does this automatically if you reference the issue number in the PR description with `Closes #123`).

### After merge
1. The card moves to **Done** automatically when the linked PR is merged (if configured), or move it manually.

### Creating a new card
1. Add it to **Backlog** first - not directly to In Progress.
2. Give it a clear, short title.
3. Add a description explaining what needs to be done and why.
4. If it's a large task, break it into smaller cards.
5. If it requires admin sign-off before work begins (e.g., a refactor or a major feature), leave it in Backlog and flag it in Discord first.

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
[Dependencies, risks, related issues, or anything else relevant.]
```

---

## Rules

- **Don't leave cards unassigned in In Progress.** If you stopped working on something, move it back to Backlog and unassign yourself.
- **One card per distinct piece of work.** Don't bundle unrelated changes into one card (same rule as PRs).
- **Keep card titles short and descriptive.** "Fix dupe bug with Weldtronic output slot" is good. "Fix stuff" is not.
- **Keep the board clean.** Archive Done cards periodically so the board stays readable.

---

## Questions?

Ask in the `#help` channel on [Discord](https://discord.gg/wtNVzeE5QB).
