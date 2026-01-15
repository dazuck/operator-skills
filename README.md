# Operator Skills

Reusable Claude skills for startup operators and founders.

Skills are instruction sets that tell Claude how to handle specific tasks. Instead of explaining what you need every time, you invoke a skill and Claude knows what to do.

```
/inbox-commander     → Triage your email
/reality-check       → Pressure test a plan
/coach               → Think through a problem
```

## Install

### Option A: Claude Code Plugin (Recommended)

```bash
claude mcp add-skill gh:dazuck/operator-skills
```

### Option B: Manual

```bash
git clone https://github.com/dazuck/operator-skills.git
cp -r operator-skills/skills/* ~/.claude/skills/
```

## Skills

| Skill | What It Does |
|-------|--------------|
| **inbox-commander** | Email triage and prioritization |
| **coach** | Expert thinking partner for any domain |
| **reality-check** | Find gaps in plans before stakeholders do |
| **interview** | Extract requirements with non-obvious questions |
| **create-briefing** | Shareable briefing docs (human + AI readable) |
| **technical-orientation** | Explain technical concepts to non-engineers |
| **prompt-improver** | Turn rough ideas into effective AI prompts |
| **skill-customizer** | Adapt skills to your workflow |
| **ralph-loop-creator** | Structured prompts for autonomous AI work |
| **sensitive-content-scanner** | Detect PII/secrets before sharing |
| **credits-inventory** | Find startup credits and perks you're not using |
| **monthly-financials** | Bookkeeper export → runway insights *(coming soon)* |

## Customization

Skills work out of the box. Some have `[YOUR_*]` placeholders you can fill in.

```bash
# See what's customizable
grep -r "\[YOUR_" ~/.claude/skills/

# Or use the interactive setup
/personalize-skills
```

See [CUSTOMIZATION-GUIDE.md](./CUSTOMIZATION-GUIDE.md) for details.

## Structure

```
skills/
├── coach/
│   ├── SKILL.md           # Main skill
│   └── references/        # Supporting context
└── ...
```

## Contributing

PRs welcome. Keep skills focused, include examples, test before submitting.

## License

MIT
