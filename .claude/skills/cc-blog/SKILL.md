---
name: cc-blog
description: Learn from blogs to improve Claude Code usage
disable-model-invocation: false
allowed-tools: WebFetch, Read, Edit
---

# Learn from Blogs to Improve Claude Code Usage

Read the latest articles from blogs defined in `blogs.yaml` and extract/practice content that can improve Claude Code usage.

## Configuration

- `blogs.yaml` - Blogs to monitor (in this skill directory)
- `blogs.example.yaml` - Configuration example

## State Tracking

- `state.schema.json` - JSON Schema definition
- `state.yaml` - Last check state (auto-created, gitignored)
- `state.example.yaml` - Example with schema reference

**Rules:**
- `last_checked` is Unix epoch seconds (UTC)
- Schema comment (`# yaml-language-server: ...`) must be preserved on updates
- Concurrent execution: last write wins (use atomic write: temp file + rename)
- Orphan keys: remove entries from `state.yaml` if blog is deleted from `blogs.yaml`
- Only update state for successfully fetched blogs

**Recovery:**
- If `state.yaml` is corrupted, delete it and run `/cc-blog` again

## Tasks

1. Read `blogs.yaml` to get blog list
2. Read `state.yaml` if exists (first run: treat all as new, create `blogs: {}`)
   - If parse error: warn user and offer to delete and recreate
3. Remove orphan keys from state (blogs not in blogs.yaml)
4. For each blog:
   - Fetch latest articles using WebFetch
   - If fetch fails: report error and skip this blog (do not update state)
   - Compare with `state.yaml.blogs.<name>`:
     - If last_url matches: "No new articles"
     - If last_url differs: mark as [NEW]
5. For NEW articles: Pick up content related to Claude Code / AI usage
6. Extract specific things to try in your environment
7. Propose implementation steps
8. Record in CLAUDE.md or docs/claude-code-routine.md if effective
9. Ask user: "Update state.yaml to mark these as seen?"
10. If yes, update `state.yaml` (atomic write: write to temp file, then rename):
    - Preserve schema comment at top
    - Only update successfully fetched blogs
    - Set last_checked to current Unix epoch
    - Set last_url, last_title, last_published from newest article

## Output Format

```
## Articles Checked

### Status
- laiso: Last check 1738540800 (3 days ago)
- Anthropic Engineering: Last check 1738540800 (3 days ago)

### [laiso]
- [NEW] [Article Title](URL) - 2026-02-01

### [Anthropic Engineering]
- No new articles

### Errors
- (none)

## Content Related to Claude Code Usage

### Key Points
- ...

### Things to Try in Your Environment
- ...

### Implementation Steps
1. ...
2. ...

## Actions

- [ ] Try now: ...
- [ ] Add to CLAUDE.md: ...
- [ ] Consider later: ...

---
Update state.yaml to mark as seen? (y/n)
```

## Notes

- If article is unrelated to Claude Code/AI usage, report "No related articles"
- Don't force application
- Only propose things that seem actually effective
