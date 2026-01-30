---
name: cc-audit
description: Audit .claude/ directory and suggest improvements based on latest best practices for skills and commands
disable-model-invocation: false
allowed-tools: Read, Glob, Grep, WebFetch, Edit, Write, Bash(mkdir *)
---

# Claude Code Configuration Audit

Investigate the current project's `.claude/` directory and suggest improvements based on skills/commands best practices.

## Steps

### 1. Current State Investigation

Investigate the following:

- `.claude/` directory structure
- Files in `.claude/commands/` (legacy format)
- Skills in `.claude/skills/` (recommended format)
- Frontmatter and content of each file

### 2. Check Latest Best Practices

Refer to official documentation:
- https://code.claude.com/docs/en/skills

### 3. Identify Improvements

Check from the following perspectives:

| Check Item | Description |
|------------|-------------|
| commands → skills migration | Should `.claude/commands/*.md` be migrated to `.claude/skills/*/SKILL.md`? |
| frontmatter optimization | Is `description` appropriate? Is `disable-model-invocation` needed? |
| context: fork usage | Should heavy processing run in fork? |
| allowed-tools setting | Should required tools be explicitly specified? |
| description length | Is description under 1024 characters? |
| SKILL.md length | Is it under 500 lines? |
| supporting file separation | Should long reference docs be in separate files? |

### 4. Output Improvement Proposals

```
## Improvement Proposals

### 1. [Proposal Title]
- Current: ...
- After: ...
- Reason: ...

### 2. [Proposal Title]
...
```

### 5. Get Approval and Apply

Get user confirmation, then apply changes if approved.
Proceed one at a time, confirming each step.
