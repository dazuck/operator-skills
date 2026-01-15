# Customization Guide

Make these skills yours in 5 minutes.

## Quick Setup

Most skills work immediately. But they're better when personalized. This guide shows you exactly what to customize.

### Option 1: Interactive Setup (Recommended)

```bash
# Run the personalization skill
/personalize-skills
```

This walks you through each placeholder and updates all files automatically.

### Option 2: Manual Setup

```bash
# See all placeholders
grep -r "\[YOUR_" ~/.claude/skills/

# Edit each file as needed
```

---

## All Placeholders

| Placeholder | Skills | Description | Example |
|-------------|--------|-------------|---------|
| `[YOUR_NAME]` | coach, create-briefing | Your name for outputs | Alex |
| `[YOUR_EMAIL]` | inbox-commander | Your email address | alex@company.com |
| `[YOUR_COMPANY]` | create-briefing | Your company name | Acme Inc |
| `[YOUR_KNOWLEDGE_ARCHIVE]` | coach | Path to personal knowledge base | ~/Documents/knowledge/ |
| `[YOUR_CLOUD_PATH]` | coach | Cloud storage folder (iCloud, Dropbox) | ~/Dropbox/ |
| `[YOUR_RESOURCE_INDEX]` | coach | Index file for your resources | ~/knowledge/index.md |
| `[YOUR_RESOURCE_PATH]` | coach | Path to resource files | ~/knowledge/resources/ |

---

## By Skill

### coach

**Required placeholders:** None (works without customization)

**Optional customization:**

The coach skill can search your personal knowledge archives for relevant context. If you have an Obsidian vault, Notion export, or similar:

```markdown
<!-- In coach/SKILL.md, customize this line: -->
- **Personal knowledge archives** - User's collected learnings at `[YOUR_KNOWLEDGE_ARCHIVE]`
```

**What to set:**
- `[YOUR_KNOWLEDGE_ARCHIVE]` — Path to your knowledge base (e.g., `~/Documents/notes/`)
- `[YOUR_RESOURCE_INDEX]` — Index file if you have one
- `[YOUR_RESOURCE_PATH]` — Where your resources live

**If not set:** Coach uses web search and Claude's built-in knowledge only. Still fully functional.

---

### inbox-commander

**Required placeholders:** None (works without customization)

**Optional customization:**

Add your known senders to `references/known-senders.md` so the skill can prioritize emails from people you care about.

**File:** `~/.claude/skills/inbox-commander/references/known-senders.md`

The file shows the format—replace examples with your own senders:

```markdown
## VIPs
- ceo@company.com — Your CEO
- investor@vc.com — Your lead investor

## Newsletters (Always Read)
- favoritecreator@substack.com
```

**If not set:** All senders treated equally. Skill still works fine.

---

### credits-inventory

**Required:** You must fill in your context for this skill to be useful.

**File:** `~/.claude/skills/credits-inventory/references/your-context-template.md`

Copy this template and fill in your:
- Investor relationships (VCs, accelerators)
- Banking and credit card providers
- Email accounts to search for credits

Without this context, the skill can only search for generic credits programs.

---

### create-briefing

**Optional placeholders:**
- `[YOUR_NAME]` — Your name for document attribution
- `[YOUR_COMPANY]` — Company name for context

**If not set:** Uses generic placeholders, you can fill in manually.

---

### All Other Skills

These skills work out of the box with no customization needed:
- interview
- prompt-improver
- reality-check
- sensitive-content-scanner
- skill-customizer
- technical-orientation
- ralph-loop-creator

---

## Placeholder Format

Placeholders follow this pattern:

```
[YOUR_DESCRIPTIVE_NAME]
```

They're often preceded by a comment explaining what to put there:

```markdown
<!-- CUSTOMIZE: Path to your cloud-synced writing folder (iCloud, Dropbox, etc.) -->
Check `[YOUR_CLOUD_WRITING_PATH]` for drafts.
```

---

## Graceful Degradation

Skills are designed to work even without customization:

| Placeholder | If Not Set |
|-------------|------------|
| `[YOUR_NAME]` | Uses "you" instead |
| `[YOUR_EMAIL]` | Asks when needed |
| `[YOUR_CLOUD_PATH]` | Outputs to conversation instead |
| `[YOUR_KNOWLEDGE_ARCHIVE]` | Uses web + Claude's knowledge only |

You can always add customization later.

---

## Updating After Customization

When you update to a new version of these skills:

1. Your customizations may be overwritten
2. Diff the new version against your current
3. Re-apply your customizations

**Tip:** Keep your custom values in a separate file (e.g., `my-values.md`) so you can quickly re-apply them.

---

## Getting Help

If a placeholder is unclear:

1. Check the comment above it for context
2. Look at the example value provided
3. Check this guide for more detail
4. Open an issue if still stuck

---

*Last synced: 2026-01-15*
*Total placeholders: 7*
