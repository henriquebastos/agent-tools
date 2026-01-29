# searxng-search

Agent skill for web search and content extraction via SearXNG metasearch engine.

**No API keys required. No rate limits. Privacy-preserving.**

Compatible with [Cursor](https://cursor.com), [Claude Code](https://claude.ai), [Codex](https://openai.com), [Pi](https://github.com/mariozechner/pi-coding-agent), and other agents following the [Agent Skills specification](https://agentskills.io/).

## Prerequisites

- **SearXNG instance** running locally or accessible via network
- **Node.js 18+**

### Quick SearXNG Setup

```bash
docker run -d -p 8080:8080 searxng/searxng
```

## Installation

### From GitHub (Recommended)

Using any skill installer:

```bash
# Using npx skills (Vercel)
npx skills add walterra/agent-tools --skill searxng-search

# Using add-skill
npx add-skill walterra/agent-tools --skill searxng-search

# Using ai-agent-skills
npx ai-agent-skills install walterra/agent-tools

# Install to specific agents only
npx skills add walterra/agent-tools --skill searxng-search -a cursor -a claude-code
```

Then install dependencies in the skill directory:

```bash
cd ~/.cursor/skills/searxng-search && npm install
# or for Claude Code:
cd ~/.claude/skills/searxng-search && npm install
```

### Manual Installation

```bash
# Clone and copy
git clone https://github.com/walterra/agent-tools.git
cp -r agent-tools/packages/searxng-search ~/.cursor/skills/
cd ~/.cursor/skills/searxng-search && npm install
```

## Skill Directories by Agent

| Agent | Path |
|-------|------|
| **Cursor** | `~/.cursor/skills/searxng-search/` |
| **Claude Code** | `~/.claude/skills/searxng-search/` |
| **Codex** | `~/.codex/skills/searxng-search/` |
| **Pi** | `~/.pi/agent/skills/searxng-search/` |
| **Copilot** | `~/.copilot/skills/searxng-search/` |

## Usage

### Search

```bash
./scripts/search.js "query"                    # Basic search (5 results)
./scripts/search.js "query" -n 10              # More results
./scripts/search.js "query" --content          # Include page content as markdown
./scripts/search.js "query" -n 3 --content     # Combined
```

### Extract Page Content

```bash
./scripts/content.js https://example.com/article
```

## Environment Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `SEARXNG_URL` | `http://localhost:8080` | SearXNG instance URL |

## License

MIT
