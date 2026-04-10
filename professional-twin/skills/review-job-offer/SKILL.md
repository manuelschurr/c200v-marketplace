---
name: review-job-offer
description: Use when the user provides a job description (pasted text, file path, or URL) and wants to evaluate fit against their professional twin repository. Outputs a structured fit assessment, then optionally hands off to the tailor-application skill.
---

# Review Job Offer

## Overview

Given a job description, evaluate how well it fits the user's professional twin repository. Surface dealbreakers immediately. Then map matches, gaps, red flags, and give a clear recommendation.

This skill is **read-only** — it does not modify any file in the twin repo.

## When to use

- The user pastes a job description and asks "is this a fit?", "should I apply?", or similar.
- The user provides a job description with no question — assume they want a fit assessment.
- The user mentions a specific role they're considering and wants a structured evaluation.

## Pre-flight check

Before doing anything else, verify the cwd is a twin repo. Check for:

- A `CLAUDE.md` referencing professional-twin
- A `core-profile/` directory
- A `direction/` directory

If any of these are missing, bail out:

> This doesn't look like a professional twin repository. `cd` into your twin repo before invoking `review-job-offer`, or run `setup` to create one.

## Checklist

Complete in order. Do not skip steps.

1. **Read the job description.** If the user pasted text, work with that. If they gave a file path, read it. If they gave a URL, ask the user to paste the content (do not try to fetch unless they explicitly tell you to).
2. **Read the full twin repo.** Read every `.md` file in `core-profile/`, `direction/`, `companies/`, and `application-materials/`. You need the complete picture to evaluate fit — relevant evidence may live in unexpected files.
3. **Dealbreaker check.** If ANY dealbreaker from `direction/target-roles-and-criteria.md` is hit, surface it immediately at the top of the response. Ask whether to continue with the rest of the evaluation. Do not bury this — dealbreakers are the most important output.
4. **Compose the assessment.** Use the format below.
5. **Offer the handoff.** Ask the user if they want to draft tailored application materials. If yes, dispatch `tailor-application` as a subagent with the JD and the fit assessment as context.

## Output format

Structure the assessment in this order:

```markdown
## Fit Assessment: [Role title at Company]

### Dealbreakers
> Either "None hit." or a clear list of which dealbreakers are triggered.

### Overall fit
> One of: **Strong fit** / **Moderate fit** / **Weak fit** / **Dealbreaker — do not apply**.
> One sentence justifying the verdict.

### What matches
> Bulleted list. Each bullet pairs a JD requirement with concrete evidence from the twin repo. Cite the source file.
> Example: "Building product orgs from scratch — Strategy Compass (`companies/strategy-compass.md`): built PM and design functions from zero, hired and coached the team."

### Gaps
> Bulleted list. For each gap, note how significant it is — is it disqualifying, is it learnable on the job, is it bridgeable from adjacent experience?

### Red flags or unknowns
> Anything in the JD that's a yellow flag — vague language, suspicious comp omissions, unclear reporting lines, anti-patterns the user has called out in their direction docs.

### Recommendation
> One of: **Apply**, **Skip**, **Apply if [condition]**, **Need more info before deciding**.
> One paragraph explaining.
```

## Tone

- Be direct and specific. Do not hedge.
- Cite evidence — every match and gap should reference a file in the twin repo.
- Do not invent skills or experience the repo doesn't claim. If the user might have something but it's not in the repo, flag it as "not captured yet — verify with user."
- Do not be optimistic for the sake of optimism. The point of this skill is to save the user from wasting time on bad-fit applications.

## Final step — handoff to tailor-application

After presenting the assessment, ask:

> Want me to draft tailored application materials for this role?

If the user says yes:
- Dispatch `tailor-application` as a subagent (use the Agent tool with subagent_type=general-purpose and prompt the subagent to use the `tailor-application` skill).
- Pass the job description and the fit assessment as context.
- Let the subagent run independently — it will return with drafted materials.

If the user says no, end the session.

## What this skill does NOT do

- It does NOT write any files in the twin repo. Read-only.
- It does NOT draft application materials inline. That's `tailor-application`'s job.
- It does NOT fetch URLs unless the user explicitly tells you to.
- It does NOT make up experience the user doesn't have.
