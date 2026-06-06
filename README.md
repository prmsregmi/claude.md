# claude.md

My global [Claude Code](https://claude.com/claude-code) configuration: memory instructions, a custom research subagent, a tuned permission set, and the plugins I run.

## Layout

| Path | Purpose |
|------|---------|
| `CLAUDE.md` | Global instructions — response style, coding standards, git and execution rules. Maps to `~/.claude/CLAUDE.md`. |
| `.claude/settings.json` | Permission allow/deny/ask lists, enabled plugins, and extra marketplaces. |
| `.claude/agents/dev-pattern-researcher.md` | Custom subagent that researches current real-world conventions before new features. |

## Using it

**As a project** — clone and open it in Claude Code. `CLAUDE.md`, `.claude/settings.json`, and the agent load automatically while you work in this directory.

**As global config** — copy into your user scope:

```bash
cp CLAUDE.md ~/.claude/CLAUDE.md
cp .claude/agents/dev-pattern-researcher.md ~/.claude/agents/
# merge .claude/settings.json into ~/.claude/settings.json
```

`settings.json` registers the two non-official marketplaces (`extraKnownMarketplaces`) and lists the plugins to enable (`enabledPlugins`), but Claude Code does **not** auto-install them. You are prompted to install when you trust the folder, or install them manually below.

## Plugins

The official marketplace (`claude-plugins-official`) is available by default. Add the other two:

```
/plugin marketplace add ChromeDevTools/chrome-devtools-mcp
/plugin marketplace add openai/codex-plugin-cc
```

Then install:

```
/plugin install superpowers@claude-plugins-official
/plugin install commit-commands@claude-plugins-official
/plugin install context7@claude-plugins-official
/plugin install frontend-design@claude-plugins-official
/plugin install security-guidance@claude-plugins-official
/plugin install pyright-lsp@claude-plugins-official
/plugin install typescript-lsp@claude-plugins-official
/plugin install codex@openai-codex
/plugin install chrome-devtools-mcp@chrome-devtools-plugins
```

| Plugin | What it adds |
|--------|--------------|
| `superpowers` | Skill library and workflow disciplines: brainstorming, TDD, systematic debugging, code review. |
| `codex` | OpenAI Codex review and rescue (`/codex:review`, `/codex:adversarial-review`). |
| `context7` | Up-to-date library and API docs over MCP. |
| `frontend-design` | Production-grade frontend UI generation. |
| `commit-commands` | `/commit`, `/commit-push-pr`, branch cleanup. |
| `security-guidance` | Security review guidance for sensitive changes. |
| `pyright-lsp` | Python LSP navigation (pyright). |
| `typescript-lsp` | TypeScript LSP navigation. |
| `chrome-devtools-mcp` | Browser automation and debugging via Chrome DevTools MCP. |

Marketplace and install commands also work as `claude plugin ...` from the shell.

## Agent

`dev-pattern-researcher` (sonnet) finds and synthesizes dominant, current engineering conventions from sources in the last 12 months before any new feature or architecture decision.

## License

[MIT](LICENSE)
