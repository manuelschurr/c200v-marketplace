---
name: interview
description: Use when building or updating a file in a professional twin repository. Invoke once per topic file. Interviews the user, reframes and challenges answers, then writes a structured document. This is an interview, not a transcription.
---

# Professional Twin: Guided Interview

## Overview

Help capture professional identity, values, and positions through natural collaborative dialogue.

Start by understanding the current repo context, then ask questions one at a time to explore the topic. Once you understand the user's positions, present the draft in sections and get approval.

Do NOT write or update the file until you have interviewed the user and they have approved the draft. This applies to EVERY topic regardless of perceived simplicity.

## Anti-Pattern: "This Topic Is Straightforward"

Every topic goes through the interview. Even ones that seem obvious. "Straightforward" topics are where unexamined assumptions hide. The interview can be short (a few questions for a narrow topic), but you MUST interview before writing.

## Checklist

You MUST complete these steps in order:

1. **Identify target file.** If the user named one, use it. If they didn't, see "No target file" below.
2. **Explore context** — read the repo's `CLAUDE.md`, related docs, and any material the user points you to.
3. **Review target file** — if the file already has content, read it and identify what's solid, what's thin, what's stale, and what's missing. Don't re-interview ground that's already well-covered.
4. **Ask clarifying questions** — one at a time, understand the user's positions, experiences, and boundaries on this topic.
5. **Present draft** — in sections scaled to their complexity, get user approval after each section.
6. **Challenge pass** — review the draft for vagueness, contradictions, and gaps; ask targeted follow-ups one at a time.
7. **Write the file** — integrate new material into the existing file. Reduce redundancy, reshape structure where needed, and preserve what was already approved. Save the result.

## No target file

If the user invokes the skill without naming a file, do not pick one yourself. Instead:

1. List the files in the repo organized by section (`core-profile/`, `direction/`, `application-materials/`, `companies/`).
2. For each file, give a one-line hint of what it captures (read the top heading and the first paragraph for accurate hints — do not guess).
3. Ask which file the user wants to work on.

If the repo doesn't look like a twin repo (no `core-profile/` folder, no `CLAUDE.md` referencing professional-twin), bail out:

> This doesn't look like a professional twin repository. Run the `setup` skill first to scaffold one, or `cd` into your existing twin repo before invoking `interview`.

## Interview Rules

- **One question per message.** If a topic needs more exploration, break it into multiple questions across multiple messages.
- **Reflect before advancing.** After each answer, play back what you understood in one sentence. Then ask the next question.
- **Be ready to go back.** If a later answer casts doubt on an earlier one, return and clarify. Don't only move forward.
- **Don't accept vague answers.** "I value autonomy" → "What did autonomy look like in your best role vs. your worst?" Probe for specifics, but accept a firm gut feeling if they can't point to a story.
- **Prefer contrastive pairs and scenarios over open-ended questions.** "High comp at a boring company, or 20% less at one you believe in?" beats "How important is mission?"
- **Ask about past behavior, not hypothetical intent.** "When did you last turn something down?" beats "What would make you say no?"
- **Name contradictions without judgment.** "Earlier you said X, but this sounds like Y — which one wins?"
- **Move on when you have:** a clear position (backed by an example or a stated conviction), and an acknowledged tradeoff for each claim.
- **Check pacing.** When you think you have enough on a topic, say so and ask the user whether the coverage feels complete or if there's more to dig into. Don't just keep asking — form your own view on when a topic is sufficiently covered.

## Reframing

When the user gives a generic answer, reframe it as a specific testable claim and ask if it's accurate:

> "So you're saying you'd rather own a smaller scope end-to-end than have influence across a bigger product you don't control — is that right, or does it depend on the team?"

When the user describes a frustration, extract the positive inverse:

> "The flip side is you need X — does that sound right?"

When a position sounds settled but hasn't been stress-tested:

> "What would have to be true for you to flip on that?"

## Presenting the Draft

- Scale each section to its complexity: a few sentences if straightforward, up to 200-300 words if nuanced.
- Ask after each section whether it looks right so far.
- Be ready to go back and clarify if something doesn't make sense.

## Writing Rules

- Write in the user's voice and framing — first person if they speak in first person, third person if they prefer that (ask if unclear).
- Ask for examples, but accept gut feelings as valid. Not everything needs evidence.
- Flag contradictions in an `## Open Questions` section — don't paper over them.
- Tone: direct, specific, opinionated. Decision-support document, not marketing.
- Preserve content the user has already approved in earlier sessions. Reduce redundancy by editing for clarity, not by deleting positions.
