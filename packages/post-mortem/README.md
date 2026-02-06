# post-mortem

Agent skill for analyzing chat sessions to identify successes, failures, and improvement opportunities.

**Generates actionable recommendations for updating project rules and skills to prevent similar issues.**

Compatible with [Cursor](https://cursor.com), [Claude Code](https://claude.ai), [Codex](https://openai.com), [Pi](https://github.com/mariozechner/pi-coding-agent), and other agents following the [Agent Skills specification](https://agentskills.io/).

## What it does

1. Analyzes the current session or a provided chat export
2. Categorizes interactions into successful patterns, failures, and friction points
3. Identifies root causes (missing context, unclear instructions, tool selection issues)
4. Generates specific recommendations for `.cursorrules`, skills, and system prompts
5. Applies approved changes after user confirmation

## Installation

### From GitHub (Recommended)

```bash
# Using npx skills (Vercel)
npx skills add walterra/agent-tools --skill post-mortem

# Install to specific agents only
npx skills add walterra/agent-tools --skill post-mortem -a cursor -a claude-code
```

### Manual Installation

```bash
git clone https://github.com/walterra/agent-tools.git
cp -r agent-tools/packages/post-mortem ~/.cursor/skills/
```

No `npm install` needed — this is a pure markdown skill with no dependencies.

## Skill Directories by Agent

| Agent | Path |
|-------|------|
| **Cursor** | `~/.cursor/skills/post-mortem/` |
| **Claude Code** | `~/.claude/skills/post-mortem/` |
| **Codex** | `~/.codex/skills/post-mortem/` |
| **Pi** | `~/.pi/agent/skills/post-mortem/` |
| **Copilot** | `~/.copilot/skills/post-mortem/` |

## Usage

Analyze the current session:

```
Do a post-mortem on this chat
```

Analyze a chat export:

```
Post-mortem ~/Downloads/chat-export.json - focus on the build process issues
```

## Key behaviors

- **Comprehensive analysis**: Reviews tool usage, decision points, errors, and repeated attempts
- **Root cause identification**: Goes beyond symptoms to find underlying issues
- **Actionable recommendations**: Specific file changes, not vague suggestions
- **User confirmation**: Always asks before modifying any files

## License

MIT
