# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A Claude Code plugin marketplace (`manuelschurr/c200v-marketplace`). Currently ships one plugin: `professional-twin`. The marketplace structure allows adding more plugins later — each plugin lives in its own top-level directory.

## Plugin anatomy (applies to every plugin)

Each plugin directory follows this layout:

```
<plugin-name>/
  .claude-plugin/plugin.json  — plugin metadata, version, description
  skills/                     — SKILL.md files (the actual skill logic)
  commands/                   — slash command definitions (thin wrappers that dispatch to skills)
  templates/                  — scaffolding files (if the plugin has a setup step)
  README.md                   — user-facing docs for the plugin
```

## How skills and commands relate

Commands (`commands/*.md`) are thin dispatchers — they name the skill and pass through `$ARGUMENTS`. The real logic lives in `skills/<name>/SKILL.md`. When changing behavior, edit the skill; only touch the command if the dispatch metadata (description, argument handling) changes.

Skills are pure Markdown instructions, not code. They are loaded by Claude Code at runtime and followed as-is. Edit them like documentation — clarity and precision matter more than brevity.

## Conventions

- **Bump the version** in `<plugin>/.claude-plugin/plugin.json` on every change. Users' plugin caches are keyed by version — without a bump, changes won't propagate.
- **Don't add new skills or commands without discussing with the maintainer first.**
- The `templates/` directory under `professional-twin` contains files that are copied verbatim into the user's twin repo by the `setup` skill. Edits to templates affect every new repo going forward, but not existing ones.
- There are two CLAUDE.md files in this repo. This one (repo root) guides Claude when working on the marketplace itself. `professional-twin/templates/CLAUDE.md` is a template that gets copied into the user's twin repo by the `setup` skill — it guides Claude when working inside a twin repo. Edits to one should not bleed into the other.
