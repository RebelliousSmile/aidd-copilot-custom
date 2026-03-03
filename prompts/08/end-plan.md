---
description: Finalize a development task — validate, commit, review and open a draft PR
---

# End Plan

## Goal

Complete the current plan: run validation, commit changes following project conventions, open a draft PR, then clean up the local branch.

## Context

### Commit conventions

```markdown
@aidd_docs/templates/vcs/commit.md
@aidd_docs/memory/vcs.md
```

### PR template

```markdown
@aidd_docs/templates/vcs/pull_request.md
```

## Rules

- Keep commits atomic — split by concern if needed
- Never `--force` push
- Detect base branch from git history, do NOT assume `main` or `master`
- Ask for confirmation before committing and before creating the PR
- Open PR as **draft**

## Steps

1. Run the project test suite — stop and report if failures
2. Check staged and unstaged changes (`git status`, `git diff`)
3. Propose commit split if changes cover multiple concerns — **wait for approval**
4. Commit each part with a message following project conventions
5. Push branch to remote (`git push --force-with-lease`)
6. Detect base branch from recent git history
7. Fill the PR template with current branch changes
8. Show PR title + body — **wait for approval**
9. Create draft PR using `gh pr create --draft`
10. Print PR URL and summary
11. Delete local branch (`git branch -D <branch>`)
