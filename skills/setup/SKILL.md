---
name: setup
description: Use when bootstrapping a new "professional twin" repository — creates the folder structure and seed files for capturing professional identity, career history, values, and application materials. Run once per twin repo.
---

# Setup — Bootstrap a Professional Twin Repository

## Overview

Create a new twin repository from the plugin's templates. This is a one-time action per repo. After running setup, the user fills in content via the `interview` skill.

## When to use

- The user wants to start a new professional twin repository.
- The user is in (or just created) an empty directory and asks "set this up" or "bootstrap a twin."
- The user mentions they don't yet have a repo and wants to get started.

**Do not run setup if a twin repo already exists in the cwd.** If you see existing files like `core-profile/` or a `CLAUDE.md` referencing professional-twin, abort and tell the user the repo already exists.

## Checklist

Complete in order:

1. **Confirm target directory.** Default to cwd if it's empty (or contains only a `.git` folder). If cwd is non-empty, ask the user for a path or for confirmation.
2. **Confirm intent.** Show the user the list of folders and files about to be created. Get explicit yes before writing.
3. **Copy templates.** Copy every file under the plugin's `templates/` directory into the target.
4. **Initialize git** (if no `.git` exists in the target). Ask first.
5. **Print next steps.** Tell the user what to do next.

## Step 1 — Confirm target directory

Default behavior:
- If `cwd` is empty (or contains only `.git`), use cwd.
- Otherwise, ask the user: "Where should the twin repo go? (Provide an absolute path. The directory should be empty or not yet exist.)"

Validate:
- The directory is empty (or only contains `.git`), OR doesn't exist yet (in which case create it).
- The directory is writable.

## Step 2 — Confirm intent

Show the user a tree of what's about to be created:

```
<target>/
├── CLAUDE.md
├── core-profile/
│   ├── professional-identity.md
│   ├── career-history.md
│   ├── skills-and-competencies.md
│   └── side-projects-and-open-source.md
├── companies/
│   ├── README.md
│   └── _template.md
├── direction/
│   ├── target-roles-and-criteria.md
│   ├── industries-and-domains.md
│   └── values-and-work-style.md
└── application-materials/
    ├── base-cv.md
    ├── writing-samples-and-portfolio.md
    └── common-questions.md
```

Then ask: "Create this in `<target>`? (yes/no)"

Do not proceed without an explicit yes.

## Step 3 — Copy templates

Copy every file under the plugin's `templates/` directory into the target. Preserve directory structure. Do not modify file contents — they are templates as-is.

**Locating the templates directory:** You (Claude) loaded this `SKILL.md` from a known path. The `templates/` directory is at `<plugin-root>/templates/`, where `<plugin-root>` is the parent of `<plugin-root>/skills/setup/SKILL.md`. If you cannot determine that path from context, ask the user: "Where is the professional-twin plugin installed?" and locate `templates/` from there. Do not guess.

After copying, verify every file in the tree above exists. If any are missing, abort and tell the user which ones — do not leave the repo in a half-initialized state.

## Step 4 — Initialize git

If `<target>/.git` does not exist:

> Ask: "Initialize git in this directory? (yes/no)"

If yes:
- Run `git init` in the target.
- Run `git add .` and `git commit -m "initial commit: professional-twin scaffolding"`.

If no, skip — the user can do it manually later.

## Step 5 — Print next steps

Tell the user:

> Done. Your professional twin repository is at `<target>`.
>
> Next steps:
> 1. `cd <target>`
> 2. Run the `interview` skill on `core-profile/professional-identity.md` to start filling things in. (Or ask Claude to "interview me about my professional identity.")
> 3. Work through the files in any order — there is no required sequence. A good rough order is: `core-profile/` → `direction/` → first `companies/<company>.md` file.
>
> The repo is intended to grow over time. You don't have to fill everything in one sitting.

## What setup does NOT do

- It does NOT ask any twin-content questions. That's the `interview` skill's job. Do not ask the user about their career, values, or skills as part of setup.
- It does NOT push to a remote. The user does that themselves if and when they want to.
- It does NOT install the plugin or modify Claude Code configuration. It only creates files in the target directory.
