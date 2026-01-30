# Claude Code Improvement Routine

## Daily Checklist

### 1. Consider Configuration Improvements (5 min)

- [ ] Can yesterday's stumbling points be added to CLAUDE.md?
- [ ] Can repetitive tasks be made into custom commands?
- [ ] Are there new project-specific rules?

### 2. Information Gathering → Practice (15-30 min)

- [ ] Check monitored repository updates (`/cc-releases`)
- [ ] Read blog articles and practice (`/cc-blog`)
- [ ] Record in CLAUDE.md if effective

## Configuration

- **Repositories**: `.claude/skills/cc-releases/sources.yaml`
- **Blogs**: `.claude/skills/cc-blog/blogs.yaml`

## Skills List

| Skill | Purpose |
|-------|---------|
| `/cc-releases` | Check repository updates |
| `/cc-blog` | Read blogs and practice |
| `/cc-improve` | Consider CLAUDE.md/command improvements |
| `/cc-status` | Check and review usage status |
| `/cc-projects-improve` | Cross-project usage analysis |
| `/cc-audit` | Audit .claude/ directory |
| `/cc-review-claudemd` | Review conversations to improve CLAUDE.md |

## Records

### Things Tried and Effects

<!-- Record date and content -->

| Date | Content | Effect |
|------|---------|--------|
| 2026-01-31 | `/copy` command for PR descriptions | Convenient - saves time copying from terminal |
| 2026-02-01 | Created settings.local.json with rake/gh permissions | Reduced permission prompts for common commands |
| 2026-02-01 | Added priority markers (★) to Things to Try | Clearer what to focus on next |
