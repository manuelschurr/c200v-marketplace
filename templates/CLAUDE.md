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
system/                — How to use this library (and the accompanying plugin)
```

## Use Cases

This repo works in tandem with the **professional-twin plugin** (https://github.com/manuelschurr/professional-twin). See `system/instructions.md` for which skills handle which workflows and how to install the plugin if it isn't available.
