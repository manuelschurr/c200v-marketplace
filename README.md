# c200v-marketplace

A personal [Claude Code plugin marketplace](https://docs.claude.com/en/docs/claude-code/plugins) by Manuel Schurr.

This repo is a marketplace — a small collection of Claude Code plugins I use and maintain. Currently it ships one plugin, but the structure is meant to grow.

## Add the marketplace

In Claude Code:

```
/plugin marketplace add manuelschurr/c200v-marketplace
```

Claude Code clones the repo under `~/.claude/plugins/marketplaces/c200v-marketplace`. From there you can install any of the plugins below.

To update later: `/plugin marketplace update c200v-marketplace`.

## Plugins

| Plugin | What it does |
|---|---|
| [`professional-twin`](./professional-twin/README.md) | Build and use a personal repository of your professional self — identity, history, values, direction — so Claude can help you apply for jobs, prep for interviews, and reflect on your career. |

Install any plugin with:

```
/plugin install <plugin-name>@c200v-marketplace
```

e.g. `/plugin install professional-twin@c200v-marketplace`.

See each plugin's own README for what it does, what skills/commands it exposes, and how to use it.

## Local development

If you want to hack on a plugin, clone the repo and add it as a local marketplace:

```bash
git clone https://github.com/manuelschurr/c200v-marketplace.git
```

```
/plugin marketplace add /absolute/path/to/c200v-marketplace
/plugin install <plugin-name>@c200v-marketplace
```

## License

MIT — see [LICENSE](LICENSE).
