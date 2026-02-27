---
name: sync-skills-public
description: Export sanitized skills to a public repo. Scans for sensitive content before export.
---

# Sync Skills to Public Repo

## Core Purpose

Create a sanitized, shareable version of your Claude Code skills. This skill:

1. Scans your skills for sensitive content
2. Creates a clean copy with personal info replaced
3. Verifies the output is safe to share
4. Syncs to your public repo location

## When to Use

- After creating or significantly updating skills
- Before pushing updates to your public skills repo
- When you want to share your skill setup with others
- Periodic sync to keep public repo current

## Invocation

`/sync-skills-public` - Run full sync workflow
`/sync-skills-public --dry-run` - Show what would change without writing
`/sync-skills-public --scan-only` - Just run the sensitive content scan

---

## Configuration

### Required: Create config file

Create `~/.claude/sync-skills-config.md`:

```markdown
# Sync Skills Public Config

## Paths

**Source:** `~/.claude/skills/`
**Destination:** `~/repos/claude-code-skills/` (or your public repo path)

## Sanitization Rules

### Personal Name

- Find: `Danny` (or your name)
- Replace with: `[YOUR_NAME]`

### Personal Paths

| Pattern                                           | Replacement             |
| ------------------------------------------------- | ----------------------- |
| `~/Library/Mobile Documents/com~apple~CloudDocs/` | `~/your-cloud-storage/` |
| `/Users/[your-username]/`                         | `/Users/[username]/`    |
| (add your patterns)                               |                         |

### Private URLs

| Pattern                                      | Replacement         |
| -------------------------------------------- | ------------------- |
| `https://flat-agustinia-3f3.notion.site/...` | `[YOUR_NOTION_URL]` |
| (add your URLs)                              |                     |

## Files to Exclude

Skip these files entirely (don't copy to public):

- `.DS_Store`
- `sensitive-content-context.md`
- `sync-skills-config.md`
- (add others)

## Files to Skip Sanitization

Copy as-is without sanitization (already clean):

- `brainstorming/SKILL.md`
- `code-reviewer/SKILL.md`
- (add others you've verified are clean)

## Post-Export

After successful export:

- [ ] Auto-commit: false (set to true if you want auto-commits)
- [ ] Commit message template: "Sync skills from local - [DATE]"
```

---

## Workflow

### Phase 1: Pre-flight Checks

1. **Load configuration**
   - Read `~/.claude/sync-skills-config.md`
   - Verify source and destination paths exist
   - Load sanitization rules

2. **Check destination repo state**
   - Is it a git repo?
   - Any uncommitted changes? (warn if so)
   - On correct branch?

### Phase 2: Sensitive Content Scan

1. **Invoke sensitive-content-scanner** on `~/.claude/skills/`
2. **Review findings:**
   - CRITICAL: Must be addressed - halt if found
   - HIGH: Will be sanitized per config rules
   - MEDIUM: Will be sanitized per config rules
   - LOW: Report but proceed

3. **Present scan summary:**

   ```
   Scan Results:
   - X files scanned
   - X findings to sanitize
   - X files already clean

   Proceed with sanitization? [y/n]
   ```

### Phase 3: Sanitization

For each file:

1. **Check if in exclude list** → Skip entirely
2. **Check if in skip-sanitization list** → Copy as-is
3. **Otherwise:**
   - Copy file content
   - Apply all sanitization rules from config
   - Track what was changed

**Sanitization report:**

```
Sanitizing: writeup/SKILL.md
  - Line 3: "Danny" → "[YOUR_NAME]" (4 occurrences)
  - Line 25: iCloud path → placeholder
  - Line 31: iCloud path → placeholder

Sanitizing: coach/SKILL.md
  - Line 86: iCloud path → placeholder

Copying unchanged: brainstorming/SKILL.md
Copying unchanged: code-reviewer/SKILL.md
...
```

### Phase 4: Verification Scan

1. **Re-run sensitive-content-scanner** on the OUTPUT directory
2. **Verify clean:**
   - Any CRITICAL findings → HALT, report issue
   - Any HIGH findings → WARN, ask to proceed
   - MEDIUM/LOW → Report, proceed

3. **Show verification result:**

   ```
   Verification scan: PASSED
   - 0 critical issues
   - 0 high issues
   - 2 medium issues (acceptable)

   Ready to write to destination.
   ```

### Phase 5: Write Output

1. **Clear destination** (or sync incrementally)
2. **Write sanitized files**
3. **Generate/update public README.md** (see template below)
4. **Report completion:**

   ```
   Export complete!

   Files written: 24
   Files sanitized: 6
   Files copied unchanged: 18

   Destination: ~/repos/claude-code-skills/
   ```

### Phase 6: Optional Git Operations

If auto-commit enabled in config:

```
Changes staged:
  M skills/writeup/SKILL.md
  M skills/coach/SKILL.md
  A skills/new-skill/SKILL.md

Commit with message: "Sync skills from local - 2025-01-10"? [y/n]
```

If not:

```
To commit these changes:
  cd ~/repos/claude-code-skills
  git add .
  git commit -m "Sync skills from local - 2025-01-10"
  git push
```

---

## Public README Template

Generate/update this in the destination:

```markdown
# Claude Code Skills

A collection of skills for [Claude Code](https://claude.ai/code).

## Installation

Copy the skills you want to `~/.claude/skills/`:

\`\`\`bash

# Clone this repo

git clone https://github.com/[username]/claude-code-skills.git

# Copy all skills

cp -r claude-code-skills/skills/\* ~/.claude/skills/

# Or copy individual skills

cp -r claude-code-skills/skills/brainstorming ~/.claude/skills/
\`\`\`

## Customization

Some skills reference placeholder paths like `[YOUR_PATH]` or `[YOUR_NAME]`.
Search for these and replace with your actual values:

\`\`\`bash
grep -r "\[YOUR" ~/.claude/skills/
\`\`\`

## Available Skills

| Skill | Description |
| ----- | ----------- |

[Auto-generated from skill descriptions]

## Skill Structure

Each skill lives in its own directory:
\`\`\`
skills/
skill-name/
SKILL.md # Main skill definition
references/ # Optional supporting files
\`\`\`

## License

[LICENSE]

---

Exported from local skills on [DATE].
```

---

## Dry Run Mode

With `--dry-run`:

- Runs all phases except Phase 5 (Write Output)
- Shows exactly what would be written/changed
- Useful for previewing before committing to changes

```
DRY RUN - No files will be written

Would sanitize:
  - writeup/SKILL.md (4 replacements)
  - coach/SKILL.md (1 replacement)
  - content-from-briefing/SKILL.md (2 replacements)

Would copy unchanged:
  - brainstorming/SKILL.md
  - code-reviewer/SKILL.md
  [...]

Would generate: README.md
```

---

## Scan Only Mode

With `--scan-only`:

- Just runs the sensitive-content-scanner
- Doesn't create any output
- Useful for checking current state

---

## Troubleshooting

### "Config file not found"

Create `~/.claude/sync-skills-config.md` with required settings.

### "Destination not a git repo"

Initialize the destination as a git repo first, or remove the git checks from config.

### "Verification found CRITICAL issues"

The sanitization rules didn't catch everything. Check the verification report and add missing patterns to your config.

### "Some placeholders not replaced"

Your config is missing sanitization rules for some personal content. Add the patterns to the config.

---

## Quick Reference

| Command                           | What it does                    |
| --------------------------------- | ------------------------------- |
| `/sync-skills-public`             | Full sync workflow              |
| `/sync-skills-public --dry-run`   | Preview without writing         |
| `/sync-skills-public --scan-only` | Just scan for sensitive content |
