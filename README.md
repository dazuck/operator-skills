# Operator Skills

Claude skills for startup operators, founders, and first-business-hires.

**Stop prompting. Start doing.**

These skills turn Claude into your operations co-pilot. They're not prompts—they're workflows that understand context, ask the right questions, and produce ready-to-use outputs.

## What's a Skill?

Skills are instruction sets that tell Claude how to handle specific tasks. Instead of explaining what you need every time, you invoke a skill and Claude knows exactly what to do.

```
/inbox-commander          → Triage your email, prioritize what matters
/reality-check            → Pressure test your plan before you commit
/coach                    → Strategic thinking partner when you're stuck
```

## Quick Start

### 1. Install

```bash
# Clone this repo
git clone https://github.com/operator-superpowers/operator-skills.git

# Copy skills to Claude's skills directory
cp -r operator-skills/skills/* ~/.claude/skills/
```

### 2. Personalize

Some skills have placeholders like `[YOUR_NAME]` that you should customize.

```bash
# See what needs customizing
grep -r "\[YOUR_" ~/.claude/skills/

# Or run the personalization skill
/personalize-skills
```

See [CUSTOMIZATION-GUIDE.md](./CUSTOMIZATION-GUIDE.md) for the full list.

### 3. Use

In Claude Code or Claude Desktop:
```
/coach "I'm deciding between two job offers"
/reality-check "My plan to launch in 2 weeks"
/inbox-commander
```

## Available Skills

*Skills will be populated after first sync.*

### Think Better
- **coach** — Strategic thinking partner with radical candor
- **reality-check** — Pressure test plans before committing
- **interview** — Flesh out requirements with smart questions
- **create-briefing** — Dual-audience briefing documents
- **prompt-improver** — Transform rough prompts into optimized instructions
- **technical-orientation** — Explain tech to non-engineers

### Work Faster
- **inbox-commander** — Email triage and prioritization
- **skill-customizer** — Adapt skills to your environment

### Safety
- **sensitive-content-scanner** — Scan for sensitive content before sharing

## Customization

Skills work out of the box, but they're better when personalized.

See [CUSTOMIZATION-GUIDE.md](./CUSTOMIZATION-GUIDE.md) for:
- All placeholders and what they do
- How to quickly personalize everything
- Optional enhancements per skill

## Platform Compatibility

| Platform | Status |
|----------|--------|
| Claude Code | Full support |
| Claude Desktop | Full support |
| Claude Co-work | Skills supported |

## Contributing

PRs welcome. Please:
- Keep skills focused (one job per skill)
- Include examples
- No personal data in examples

## License

MIT License. See [LICENSE](./LICENSE).

## About

Built by operators, for operators. Part of the [Operator Superpowers](https://operatorsuperpowers.com) project.

---

*This repo is synced from private skills using sync-skills-product.*
