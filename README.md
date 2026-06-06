# claude.md

> My global [Claude Code](https://claude.com/claude-code) setup — instructions, a research agent, tuned permissions, and the plugins I actually run.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
![Claude Code](https://img.shields.io/badge/Claude_Code-config-orange)
![Plugins](https://img.shields.io/badge/plugins-9-blue)

## What's inside

| Path | What |
|------|------|
| `CLAUDE.md` | Global instructions — style, coding rules, git workflow. |
| `.claude/settings.json` | Permissions + enabled plugins + marketplaces. |
| `.claude/agents/dev-pattern-researcher.md` | Subagent that checks current real-world conventions *before* you build. |

## Use it

Open the folder in Claude Code (auto-loads here), or copy into your user scope:

```bash
cp CLAUDE.md ~/.claude/CLAUDE.md
cp .claude/agents/*.md ~/.claude/agents/
# then merge .claude/settings.json into ~/.claude/settings.json
```

> `settings.json` *lists* the plugins, it doesn't install them. Claude Code prompts you on trust — or just run the commands below.

## Plugins

The official marketplace ships by default. Add the two extras, then install:

```
/plugin marketplace add ChromeDevTools/chrome-devtools-mcp
/plugin marketplace add openai/codex-plugin-cc

/plugin install superpowers@claude-plugins-official
/plugin install codex@openai-codex
/plugin install context7@claude-plugins-official
/plugin install commit-commands@claude-plugins-official
/plugin install frontend-design@claude-plugins-official
/plugin install security-guidance@claude-plugins-official
/plugin install pyright-lsp@claude-plugins-official
/plugin install typescript-lsp@claude-plugins-official
/plugin install chrome-devtools-mcp@chrome-devtools-plugins
```

The four I lean on every day:

| Plugin | Why it earns its slot |
|--------|-----------------------|
| `superpowers` | Skills + disciplines: brainstorming, TDD, debugging, reviews. |
| `codex` | A grumpy second reviewer (`/codex:review`, `/codex:adversarial-review`). |
| `context7` | Live library/API docs, so I stop hallucinating APIs from memory. |
| `commit-commands` | `/commit`, `/commit-push-pr`, branch cleanup. |

The rest pull their weight only when the work calls for it: `pyright-lsp` / `typescript-lsp` for Python/TS navigation, `frontend-design` for UI, `chrome-devtools-mcp` for browser debugging, `security-guidance` for the scary changes.

## The agent

`dev-pattern-researcher` digs up what practitioners *actually* do right now (sources < 12 months old) and hands back a recommendation — not a pile of links.

## License

[MIT](LICENSE) — take it, remix it, no warranty.
