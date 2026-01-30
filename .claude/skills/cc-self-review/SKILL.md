---
name: cc-self-review
description: Claude Code self-review
disable-model-invocation: false
allowed-tools: Read, Glob, Grep
---

# Claude Code Self-Review

Analyze commands executed in this session and propose improvements.

## Analysis Targets

1. **Commands that required allow this time** → Decide if should be pre-allowed
2. **Repeatedly executed commands** → Candidates for automation

## Execution Steps

### 1. Check Current Session Log

Extract and analyze Bash commands executed this time from the latest JSONL files under `.claude/projects/` in this repository.

### 2. Analysis Perspectives

Propose improvements from the following perspectives:

- **Recommend pre-allow**: Safe and frequently used commands (read operations, lint, etc.)
- **Automation candidates**: Patterns of commands executed multiple times (skills, Rakefile tasks, etc.)

## Output Format

```markdown
## Recommend Pre-Allow

| Command | Reason |
|---------|--------|
| `Bash(command:*)` | reason |

## Automation Candidates

| Pattern | Proposal |
|---------|----------|
| Multiple commands | Create skill or Rake task |
```
