---
name: tailor-application
description: Use when the user wants to draft application materials (cover letter, CV emphasis, answers to specific application questions) for a specific job, using their professional twin repository as the source of truth. Commonly chained from review-job-offer.
---

# Tailor Application

## Overview

Draft tailored application materials for a specific job, using the professional twin repository as the source of truth. The output is a working draft the user can edit — not a final, polished submission.

## When to use

- The user has a specific job description and wants help writing application materials.
- This skill was dispatched as a subagent by `review-job-offer`.
- The user explicitly asks "tailor my application for this role."

## Pre-flight check

Before doing anything else, verify the cwd is a twin repo. Check for:

- A `CLAUDE.md` referencing professional-twin
- A `core-profile/` directory
- An `application-materials/` directory

If any are missing, bail out:

> This doesn't look like a professional twin repository. `cd` into your twin repo before invoking `tailor-application`, or run `setup` to create one.

## Checklist

Complete in order:

1. **Locate the job description.** If passed in via subagent context, use that. If invoked standalone, ask the user for the JD (paste, file, or URL — do not auto-fetch).
2. **Locate the fit assessment** (if passed in by `review-job-offer`). If absent, run a brief inline fit check first — read `direction/target-roles-and-criteria.md` and `direction/industries-and-domains.md` and confirm there's no dealbreaker. If there is, surface it and confirm with the user before continuing.
3. **Ask which materials to draft.** See "Materials menu" below.
4. **Read the relevant twin files.** See "Required reading" below.
5. **Draft each requested material.** Present in sections, get user feedback after each.
6. **Iterate.** Apply feedback. Re-present.
7. **Optionally save.** Ask if the user wants the final drafts saved to `applications/<company>-<role>/` in the twin repo. Default is no — only save if asked.

## Materials menu

Ask the user which of these they want:

- **Cover letter** — A drafted cover letter / motivation letter
- **CV emphasis** — Notes on what to emphasize, reorder, or add to the base CV for this specific role (the actual CV file is the user's to edit; this skill produces a tailoring brief)
- **Answers to specific questions** — Drafted answers for application form questions or screening prompts the user mentions
- **All of the above**

## Required reading

Read ALL `.md` files in the twin repo before drafting:

- Everything in `core-profile/` — positioning, career overview, skills, side projects
- Everything in `direction/` — the user's preferences, values, and criteria should inform framing even though they don't appear directly in materials
- Everything in `companies/` — not just "relevant" ones; adjacent experience from unexpected roles is often the strongest differentiator
- Everything in `application-materials/` — base CV, existing answers, writing voice, portfolio

Do not selectively read. The repo is small; the cost of reading everything is lower than the cost of missing a relevant fact.

## Drafting principles

- **Be specific, not generic.** Pull real examples and metrics from the repo. Generic claims ("strong leader," "results-driven") are forbidden — every claim must be backed by something concrete.
- **Match tone to the company.** Startup vs. corporate, German vs. English, formal vs. casual. Read the JD for cues.
- **Don't oversell.** The honest, well-framed version is more compelling than a hyped one.
- **Flag honesty problems.** If the JD asks for something the user doesn't have, do not invent it. Tell the user, in the draft, where the honest answer is "I don't have that, but here's adjacent experience."
- **Reuse existing answers.** If `common-questions.md` has a pre-existing answer that fits the role's question, adapt it rather than starting from scratch.
- **Match the language of the JD.** If the JD is in German, draft in German. If English, English. Ask if unclear.

## Output format

Present each requested material as its own section, with a heading. After each, ask:

> Does this work, or want me to revise [X]?

Don't dump everything at once and ask "what do you think?" — present one material, get feedback, refine, then move to the next.

## Saving (optional)

After all materials are approved by the user, ask:

> Save these drafts to `applications/<company>-<role>/` in the twin repo? (yes/no)

If yes:
- Create `applications/<company>-<role>/` if it doesn't exist
- Save each material as a separate file (`cover-letter.md`, `cv-emphasis.md`, `answers.md`)
- Also save the original JD as `job-description.md` for reference
- Commit if the repo has git

If no, end without writing anything.

## What this skill does NOT do

- It does NOT modify any existing file in `core-profile/`, `direction/`, `companies/`, or `application-materials/`. Those are sources, not outputs.
- It does NOT fetch URLs unless the user tells you to.
- It does NOT invent experience or skills.
- It does NOT submit applications. Drafting only.
