# professional-twin

A Claude Code plugin for building and using a personal repository of your professional self.

Your "professional twin" is a structured set of Markdown files capturing who you are, what you've done, what you value, and where you're going. Once it exists, Claude can use it to help you evaluate jobs, draft tailored applications, prepare for interviews, and reflect on direction.

## What it gives you

Four skills:

- **`setup`** — Bootstraps a new twin repo with a folder structure and seeded scaffolding files. Run once per repo.
- **`interview`** — Walks you through filling in (or updating) any twin file via guided dialogue. Asks questions, reframes vague answers, challenges contradictions, then writes the result.
- **`review-job-offer`** — Given a job description, evaluates fit against your twin repo. Highlights matches, gaps, dealbreakers, and red flags. Optionally hands off to `tailor-application`.
- **`tailor-application`** — Drafts tailored application materials (cover letter, CV emphasis, answers to specific questions) using your twin repo as the source of truth.

## Install (local development)

This plugin is currently distributed via local marketplace only. To install:

1. Clone this repo somewhere on your machine:
   ```bash
   git clone https://github.com/manuelschurr/professional-twin.git
   ```
2. Create a local marketplace entry at `~/.claude/plugins/local-marketplace/.claude-plugin/marketplace.json` (or add to your existing one):
   ```json
   {
     "name": "local-dev",
     "owner": { "name": "Your Name" },
     "plugins": [
       {
         "name": "professional-twin",
         "source": "file:///absolute/path/to/professional-twin",
         "description": "Build and use a personal repository of your professional self"
       }
     ]
   }
   ```
3. Register and install in Claude Code:
   ```
   /plugin marketplace add ~/.claude/plugins/local-marketplace
   /plugin install professional-twin@local-dev
   ```

## Usage

1. `cd` into an empty directory where you want your twin repo to live (e.g. `~/career-twin/`).
2. Run the `setup` skill (or `/setup`). It will scaffold the structure.
3. Run the `interview` skill on any of the seeded files to start filling them in. A good starting point: `core-profile/professional-identity.md`.
4. Once you have meaningful content, run `review-job-offer` against any job description.

## Repository structure (what `setup` creates)

```
your-twin-repo/
├── CLAUDE.md                       # tells Claude how to use this repo
├── core-profile/                   # who you are
│   ├── professional-identity.md
│   ├── career-history.md
│   ├── skills-and-competencies.md
│   └── side-projects-and-open-source.md
├── companies/                      # one file per company you've worked at
│   ├── README.md
│   └── _template.md
├── direction/                      # what you want next
│   ├── target-roles-and-criteria.md
│   ├── industries-and-domains.md
│   └── values-and-work-style.md
├── application-materials/          # reusable assets
│   ├── base-cv.md
│   ├── writing-samples-and-portfolio.md
│   └── common-questions.md
└── system/
    └── instructions.md             # pointer doc — tells Claude which skills handle which workflows
```

## License

MIT — see [LICENSE](LICENSE).
