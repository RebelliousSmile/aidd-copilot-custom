---
description: Archive the plan as processed, return to parent branch and clean up
---

# End Plan

## Goal

After a PR/MR has been created on a plan branch, archive the plan file and cleanly return to the parent branch.

## Rules

- Never force-delete a branch with uncommitted changes
- Never push anything
- Always pull after checkout
- Confirm branch deletion with user before executing

## Steps

1. Get current task branch name: `git branch --show-current`
2. Detect parent branch:
   - `git log --oneline --decorate HEAD` to find branch point
   - Fallback: ask user to confirm parent branch name
3. Confirm: display task branch → parent branch, **wait for user validation**
4. Find the plan file: search `aidd_docs/tasks/` for a `.md` file (not `.processed.md`, not `.review.md`) whose content contains `**Branch name**: <current-branch>`
   - If not found: ask user to identify the plan file
5. Rename plan file from `<name>.md` to `<name>.processed.md`
6. Ask user: capture learnings from this plan? If yes, follow `@.github/prompts/07_documentation/learn.prompt.md`
7. Checkout parent: `git checkout <parent>`
8. Pull: `git pull`
9. Ask user: delete plan branch? (local only / local + remote / keep)
   - Local: `git branch -D <plan-branch>`
   - Remote: `git push origin --delete <plan-branch>`
10. Report final state: current branch, last commit, renamed plan file, deleted branches
