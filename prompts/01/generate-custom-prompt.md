---
description: Generate a new custom prompt for aidd-copilot-custom in the correct format
argument-hint: Description of the new prompt to create (goal, context, steps)
---

# Generate Custom Prompt

## Goal

Generate a new prompt file for `aidd-copilot-custom` in the correct Copilot CLI format, based on the description provided in the prompt.

## Context

### Format reference — existing prompt example

```markdown
@.github/copilot-custom/prompts/08/changelog.md
```

### SDLC Phase Taxonomy

| Phase | Folder |
|---|---|
| Init / setup | `prompts/01/` |
| Context / release | `prompts/02/` |
| Plan / design | `prompts/03/` |
| Code / implement | `prompts/04/` |
| Review | `prompts/05/` |
| Test | `prompts/06/` |
| Docs / diagrams | `prompts/07/` |
| Deploy / VCS | `prompts/08/` |
| Audit / security | `prompts/09/` |
| Debug | `prompts/10/` |

## Rules

- Frontmatter: only `description` and `argument-hint` (if the prompt takes an argument)
- No `$ARGUMENTS` — the argument is passed as free text after the `@file` reference
- References to project files use `@path/from/project/root`
- Steps must be explicit and sequential
- No Claude Code–specific syntax (`$ARGUMENTS`, `name:`, `model:`)
- Keep it minimal: no section if not applicable

## Output format

```markdown
---
description: <action-oriented summary>
argument-hint: <hint> (omit if no argument)
---

# <Title>

## Goal
...

## Context (if needed)
...

## Rules
...

## Steps
...
```

## Steps

1. Analyze the description provided in the prompt — extract goal, context, constraints
2. Determine the best SDLC phase using the taxonomy above
3. Check if a similar prompt already exists in `@.github/copilot-custom/prompts/`
4. Draft the prompt following the output format
5. Show the draft to the user and **wait for approval**
6. Write the file to `prompts/<phase>/<slug>.md` — do NOT move it to the submodule automatically
7. Remind the user to move it to `aidd-copilot-custom/prompts/<phase>/` and push
