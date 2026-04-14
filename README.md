# c200v-marketplace

A personal [Claude Code plugin marketplace](https://docs.claude.com/en/docs/claude-code/plugins) by Manuel Schurr.

This repo is a catalog — a small collection of Claude Code plugins I use and maintain. The plugin source code lives in standalone repositories; this repo only contains the marketplace metadata (`.claude-plugin/marketplace.json`) that points at them.

## Add the marketplace

In Claude Code:

```
/plugin marketplace add manuelschurr/c200v-marketplace
```

Claude Code clones the catalog under `~/.claude/plugins/marketplaces/c200v-marketplace`. From there you can install any of the plugins below.

To update later: `/plugin marketplace update c200v-marketplace`.

## Plugins

| Plugin | Repository | What it does |
|---|---|---|
| [`professional-twin`](https://github.com/manuelschurr/professional-twin) | `manuelschurr/professional-twin` | Build and use a personal repository of your professional self — identity, history, values, direction — so Claude can help you apply for jobs, prep for interviews, and reflect on your career. |
| [`tutor`](https://github.com/manuelschurr/tutor) | `manuelschurr/tutor` | A personal adaptive learning plugin. Create a custom course on any topic and study it through guided, expert-tutor-style sessions inside Claude Code. |

Install any plugin with:

```
/plugin install <plugin-name>@c200v-marketplace
```

e.g. `/plugin install professional-twin@c200v-marketplace` or `/plugin install tutor@c200v-marketplace`.

See each plugin's own README and `CLAUDE.md` in its repository for what it does, what skills/commands it exposes, and how to use it.

## License

MIT — see [LICENSE](LICENSE).
