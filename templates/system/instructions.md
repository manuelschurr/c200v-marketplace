# Instructions — How to Use This Library

This file tells Claude (or any agent) what this repository is and how to work with it effectively.

## What this is

This repository is a personal "professional twin" — a structured set of Markdown files capturing the owner's professional identity, career history, skills, values, and direction. It is meant to be read and updated over time.

## The accompanying plugin

This repository works in tandem with the **professional-twin plugin** for Claude Code:

**https://github.com/manuelschurr/professional-twin**

The plugin provides skills that handle the workflows below. **If you (Claude) have access to these skills in the current session, prefer them over improvising a process.** If they're not available, tell the user how to install the plugin from the URL above.

## Use cases → skills

| Use case | Skill |
|---|---|
| Add or update profile content (any file in this repo) | `interview` |
| Evaluate fit between a job description and this repo | `review-job-offer` |
| Draft tailored application materials for a specific role | `tailor-application` |
| Bootstrap a new twin repo (shouldn't need this — repo already exists) | `setup` |

## If the plugin is not available

Tell the user:

> This repository is designed to be used with the `professional-twin` Claude Code plugin, which is not currently installed. You can install it from https://github.com/manuelschurr/professional-twin — see the README there for instructions. Without the plugin, I can still read these files and answer questions, but the structured workflows (interview, fit evaluation, tailoring) won't be as good.

Then, if the user wants to proceed without the plugin, do your best with the files as you find them. Read `core-profile/`, `direction/`, and the relevant `companies/` files before answering anything substantive.

## Repository structure

```
core-profile/          — Who you are
companies/             — Deep reference per company
direction/             — What you want next
application-materials/ — Reusable assets (CV, writing samples, common Q&A)
system/                — How to use this library (this file)
```
