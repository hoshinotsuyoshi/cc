# CLAUDE.md

This repository is a collection of files for Claude Code usage optimization.

## Project Structure

- `.claude/skills/` - Claude Code skills (distributed via symlink)
- `docs/` - Documentation and operational notes

## Rules

- Be careful when changing configuration files (don't break existing behavior)
- When adding new configurations, follow existing style

## Claude Code Usage Notes

This section is updated regularly. Record effective tips and settings here.

### Lessons Learned

<!-- Updated by cc-improve command -->

- `/copy` is convenient. Copy to clipboard immediately after creating PR descriptions or documentation (confirmed 2026-01-31)
- `/cc-releases` enables catching up on new features - run weekly to stay updated (confirmed 2026-02-01)
- `/cc-improve` is for retrospective and proposals, `/cc-audit` is for best practice compliance checks - use appropriately (confirmed 2026-02-01)
- CLAUDE.md has 150-200 instruction limit (system prompt uses ~50, leaving ~100-150). Keep it concise - unnecessary instructions reduce overall compliance (confirmed 2026-02-03)
- Skills > MCP for token efficiency: Skills use dozens of tokens vs MCP's tens of thousands. Prefer Skills when CLI tools can achieve the same result (confirmed 2026-02-03)

### Things to Try

<!-- Things found via cc-blog, cc-releases go here -->
<!-- Priority: ★★★=This week, ★★=This month, ★=Someday -->

- [ ] ★★★ `/debug` - Troubleshoot current session issues (v2.1.30)
- [ ] ★★★ `/compact` - Clean up context during long sessions to avoid degradation
- [ ] ★★★ `--from-pr` flag - Resume session linked to PR (`claude --from-pr 123`) for review/fix work (v2.1.27)
- [ ] ★★★ `Ctrl+G` - Edit prompt in external editor (useful for long prompts)
- [ ] ★★★ `#` shortcut - Add instructions to memory on-the-fly during sessions
- [ ] ★★ `Ctrl+B` - Run long commands in background (useful for builds/tests)
- [ ] ★★ Progressive Disclosure pattern - Split large CLAUDE.md into `agent_docs/` directory for complex projects
- [ ] ★ Trail of Bits Security Skills - https://github.com/trailofbits/claude-code-security-skills
- [ ] ★ Context Engineering Kit - Token efficiency techniques (research needed)
