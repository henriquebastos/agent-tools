# agent-tools

Agent tooling packages - pi extensions, agent skills, and more.

## Packages

### Pi Extensions

| Package | Description | Install |
|---------|-------------|---------|
| [@walterra/pi-charts](./packages/pi-charts) | Vega-Lite chart extension for pi | `pi install npm:@walterra/pi-charts` |
| [@walterra/pi-graphviz](./packages/pi-graphviz) | Graphviz DOT diagram extension for pi | `pi install npm:@walterra/pi-graphviz` |

### Agent Skills

Universal agent skills compatible with Cursor, Claude Code, Codex, Pi, and other agents following the [Agent Skills specification](https://agentskills.io/).

| Skill | Description |
|-------|-------------|
| [searxng-search](./packages/searxng-search) | Web search via SearXNG - no API keys, no rate limits |

## Install Skills

### From GitHub

```bash
# Using npx skills (Vercel)
npx skills add walterra/agent-tools --skill searxng-search

# Using add-skill
npx add-skill walterra/agent-tools --skill searxng-search

# Using ai-agent-skills
npx ai-agent-skills install walterra/agent-tools

# Install to specific agents
npx skills add walterra/agent-tools --skill searxng-search -a cursor -a claude-code
```

After installing, run setup in the skill directory:

```bash
cd ~/.cursor/skills/searxng-search && npm install
```

### Manual Installation

```bash
git clone https://github.com/walterra/agent-tools.git
cp -r agent-tools/packages/searxng-search ~/.cursor/skills/
cd ~/.cursor/skills/searxng-search && npm install
```

## Skill Directories by Agent

| Agent | Global Path |
|-------|-------------|
| **Cursor** | `~/.cursor/skills/` |
| **Claude Code** | `~/.claude/skills/` |
| **Codex** | `~/.codex/skills/` |
| **Pi** | `~/.pi/agent/skills/` |
| **Copilot** | `~/.copilot/skills/` |

## Package Naming Convention

| Package | Target | Distribution |
|---------|--------|--------------|
| `@walterra/pi-*` | pi-coding-agent | Published to npm |
| Skills | Cursor, Claude Code, Codex, Pi, etc. | GitHub only (not published to npm) |

## Development

```bash
# Install dependencies
pnpm install

# Build all packages
pnpm build
```

## License

MIT
