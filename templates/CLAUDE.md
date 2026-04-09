# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with files in this repository.

# Professional Twin

A structured reference library capturing who I am, what I've done, what I value, and what I want next. Used by the **professional-twin** Claude Code plugin to support job-search and career-reflection workflows.

## Repo type

This is a pure Markdown documentation library — no code, no build, no tests, no dependencies. All "work" is reading, editing, and adding `.md` files. Git is the only tooling.

## How to collaborate on this repo

- **Don't fill in answers I haven't given.** If a question is open, it's open. Ask me rather than inferring or guessing.
- **Ask one question at a time.** Don't overwhelm with a wall of questions. Pick the most important or most interesting open question.
- **It's okay to prompt reflection.** If I'm unsure, help me think through it — offer frameworks, ask probing follow-ups, surface patterns from my history. But let me arrive at the answer.
- **Challenge shallow answers.** If an answer feels generic, push for specifics. "What do you mean by that?" and "Can you give me an example?" are good reflexes.
- **Capture what I say faithfully.** Write things in my voice and framing, not in polished marketing language. The raw honest version is more useful than a cleaned-up one.
- **Flag connections across docs.** If something I say about my values also answers a question in the skills doc, note it in both places.
- **Don't restructure without asking.** If something feels wrong, propose the change — don't just do it.

## Structure

```
core-profile/          — Who I am
companies/             — Deep reference per company (raw source of truth)
direction/             — What I want next
application-materials/ — Reusable assets
```

## The accompanying plugin

This repository works in tandem with the **professional-twin plugin** for Claude Code:

**https://github.com/manuelschurr/professional-twin**

The plugin provides skills that handle the workflows below. **If you (Claude) have access to these skills in the current session, prefer them over improvising a process.** If they're not available, tell the user how to install the plugin from the URL above.

### Use cases → skills

| Use case | Skill |
|---|---|
| Add or update profile content (any file in this repo) | `interview` |
| Evaluate fit between a job description and this repo | `review-job-offer` |
| Draft tailored application materials for a specific role | `tailor-application` |
| Bootstrap a new twin repo (shouldn't need this — repo already exists) | `setup` |

### If the plugin is not available

Tell the user:

> This repository is designed to be used with the `professional-twin` Claude Code plugin, which is not currently installed. You can install it from https://github.com/manuelschurr/professional-twin — see the README there for instructions. Without the plugin, I can still read these files and answer questions, but the structured workflows (interview, fit evaluation, tailoring) won't be as good.

Then, if the user wants to proceed without the plugin, do your best with the files as you find them. Read `core-profile/`, `direction/`, and the relevant `companies/` files before answering anything substantive.
