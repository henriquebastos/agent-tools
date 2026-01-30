# git-commit

Agent skill for committing staged files with precise, well-crafted commit messages.

**Handles pre-commit hook failures, auto-fixes lint/format issues, and safely re-stages only the originally staged files.**

Compatible with [Cursor](https://cursor.com), [Claude Code](https://claude.ai), [Codex](https://openai.com), [Pi](https://github.com/mariozechner/pi-coding-agent), and other agents following the [Agent Skills specification](https://agentskills.io/).

## What it does

1. Identifies staged files (source of truth for the entire workflow)
2. Analyzes the actual diff to craft an accurate commit message (max 60 chars)
3. Commits the staged files
4. If pre-commit hooks fail: auto-fixes with project tooling, re-stages **only** the original files, and retries

## Installation

### From GitHub (Recommended)

```bash
# Using npx skills (Vercel)
npx skills add walterra/agent-tools --skill git-commit

# Install to specific agents only
npx skills add walterra/agent-tools --skill git-commit -a cursor -a claude-code
```

### Manual Installation

```bash
git clone https://github.com/walterra/agent-tools.git
cp -r agent-tools/packages/git-commit ~/.cursor/skills/
```

No `npm install` needed — this is a pure markdown skill with no dependencies.

## Skill Directories by Agent

| Agent | Path |
|-------|------|
| **Cursor** | `~/.cursor/skills/git-commit/` |
| **Claude Code** | `~/.claude/skills/git-commit/` |
| **Codex** | `~/.codex/skills/git-commit/` |
| **Pi** | `~/.pi/agent/skills/git-commit/` |
| **Copilot** | `~/.copilot/skills/git-commit/` |

## Usage

Just ask the agent to commit:

```
commit
```

The agent will identify staged files, analyze the diff, and commit with an accurate message.

## Key behaviors

- **Accurate messages**: Analyzes `git diff --cached` to describe what actually changed — no generic "add files"
- **Respects project conventions**: Uses conventional commits only if the project already does
- **Safe re-staging**: After pre-commit hook failures, only re-stages the originally staged files — never `git add .`
- **No attribution noise**: No "generated with" or "co-authored-by" in messages

## License

MIT
