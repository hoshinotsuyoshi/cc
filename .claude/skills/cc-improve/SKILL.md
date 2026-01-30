---
name: cc-improve
description: Improve Claude Code settings and commands
disable-model-invocation: false
allowed-tools: Read, Glob, Grep, Edit
---

# Claude Code Settings and Commands Improvement

Review current Claude Code settings and custom commands, and propose improvements.

## Review Targets

1. **CLAUDE.md** - Review project rules
2. **.claude/commands/** - Improve custom commands
3. **.claude/skills/** - Improve skills
4. **.claude/settings.local.json** - Optimize settings

## Tasks

### 1. Check Current State

- Check current CLAUDE.md content
- Check list and content of custom commands/skills
- Check settings.local.json configuration

### 2. Propose Improvements

Identify improvements from the following perspectives:

- **CLAUDE.md**
  - Are there rules to add?
  - Are there obsolete rules?
  - Organize "Lessons Learned" and "Things to Try"

- **Custom Commands/Skills**
  - Are there unused ones?
  - Should any be merged/split?
  - Should new ones be created?

- **settings.local.json**
  - Are there permissions to add?
  - Are there security concerns to review?

### 3. Retrospective

- Were there any recent stumbling points?
- Were there repetitive tasks?
- Can they be made into rules/automated?

## Output Format

```
## Current State

### CLAUDE.md
- Content summary

### Custom Commands/Skills
- List and purposes

### settings.local.json
- Current settings

## Improvement Proposals

### High Priority
1. ...

### Medium Priority
1. ...

### Low Priority
1. ...

## Specific Actions

- [ ] ...
```
