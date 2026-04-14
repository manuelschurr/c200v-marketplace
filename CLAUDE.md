# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A Claude Code plugin marketplace: [`manuelschurr/c200v-marketplace`](https://github.com/manuelschurr/c200v-marketplace). It is a catalog — it does not contain plugin source code. Each plugin lives in its own standalone repository and is referenced by URL from `.claude-plugin/marketplace.json`.

## Plugins in this catalog

- **[`professional-twin`](https://github.com/manuelschurr/professional-twin)** — build and use a personal repository of your professional self (identity, history, values, direction) to help with job applications, interviews, and career reflection.
- **[`tutor`](https://github.com/manuelschurr/tutor)** — a personal adaptive learning plugin. Create a custom course on any topic and study it through guided, expert-tutor-style sessions inside Claude Code.

## What lives here vs. in the plugin repos

```
c200v-marketplace/
├── .claude-plugin/marketplace.json   ← the catalog: plugin list, URLs, versions
├── README.md
└── CLAUDE.md                          ← this file
```

**Everything about a specific plugin** — its commands, skills, agents, templates, scripts, tests, and its own `CLAUDE.md` — lives in that plugin's own repo. Edit the plugin there, not here.

## Adding or updating plugins

1. **Add a new plugin to the catalog:** append a new entry to the `plugins` array in `.claude-plugin/marketplace.json`. Each entry needs:
   - `name` — the plugin's short name
   - `source` — an object `{ "source": "url", "url": "https://github.com/<owner>/<repo>.git" }` (optionally with `"ref": "<branch>"` to pin to a non-default branch)
   - `description` — a 1–3 sentence user-facing description
   - `version` — the plugin's current version, matching what's in its own `plugin.json`
   - `strict: true` — enforces version/source match on install

2. **Bump a plugin's version entry:** when a plugin releases a new version (its own `plugin.json` was bumped), update the corresponding `version` field in `marketplace.json` here.

3. **Bump the catalog version** (`metadata.version`) whenever the `plugins` array changes — plugin added, removed, version entry bumped, or source URL changed. This is how Claude Code decides to re-pull the catalog on refresh.

## Conventions

- **Two version numbers to maintain, in different repos:**
  - A plugin's own version lives in its repo's `.claude-plugin/plugin.json`. Bumped on every change to the plugin's own skills, commands, agents, scripts, or templates.
  - This catalog's version lives in `.claude-plugin/marketplace.json` (`metadata.version`). Bumped when the catalog itself changes.
- **`strict: true`** is set on every plugin entry. Keep it that way unless there's a specific reason to loosen version/source enforcement.
- **Don't add new plugins to the catalog without creating the corresponding repo first.** Empty URL entries will break `/plugin install`.

## Previous structure (historical note)

Before [version 2.0.0 of the catalog], this repo contained `professional-twin/` and `tutor/` as subdirectories with their source code in place, using relative `./<plugin>` sources in `marketplace.json`. In v2.0.0 the plugin source code was extracted into standalone repositories and the catalog switched to URL sources. The plugin commit histories were preserved via `git subtree split` into the new repos.
