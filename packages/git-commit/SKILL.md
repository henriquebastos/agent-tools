---
name: git-commit
description: Commit staged files with a precise, well-crafted commit message. Use when the user asks to commit, make a commit, or says "commit". Handles pre-commit hook failures, lint fixes, and safe re-staging.
metadata:
  version: "0.0.1"
  author: walterra
  repository: https://github.com/walterra/agent-tools
---

# Git Commit

Commit currently staged files with an accurate, concise commit message.

## Workflow

### Step 1: Identify staged files

Record the list of staged files. This list is the **source of truth** for the entire workflow.

```bash
git diff --cached --name-only
```

If nothing is staged, inform the user and stop.

### Step 2: Analyze changes and commit

Analyze the actual diff to understand what changed:

```bash
git diff --cached
```

Then commit with a one-liner message:

```bash
git commit -m "<message>"
```

#### Commit message rules

- **Max 60 characters.**
- **Describe what was done accurately.** Analyze the diff — don't default to generic verbs like "add" when files were modified, updated, or refactored.
- **No credit information.** No "generated with", "co-authored-by", or similar.
- **Conventional commits / semantic prefixes** — only use them if the project already uses them (check recent `git log --oneline -10`).

### Step 3: Check for pre-commit hook failures

If the commit succeeded, you're done. If pre-commit hooks failed (linting, type-checking, formatting), continue below.

### Step 3.1: Auto-fix with project tooling

Run the project's own maintenance commands to fix issues automatically:

```bash
# Examples — use whatever the project has
pnpm lint --fix
pnpm format
pnpm tsc:check
npm run lint
```

### Step 3.2: Fix remaining issues manually

If auto-fix didn't resolve everything, fix the remaining issues by hand.

### Step 3.3: Re-stage only the original files

**CRITICAL: Only re-stage files from the list captured in Step 1.**

```bash
git add <file-from-step-1>
```

### Step 3.4: Never stage extra files

- **NEVER** use `git add .` or any bulk staging command.
- If a formatter or linter modified a file that was **not** in the Step 1 list, leave it unstaged.

**Example:** If only `A.ts` was originally staged, but the formatter also modified `B.ts` (which was unstaged), only re-stage `A.ts`. Leave `B.ts` unstaged.

### Step 3.5: Retry the commit

```bash
git commit -m "<message>"
```

Use the same message from Step 2 (or refine it if fixes changed the scope).
