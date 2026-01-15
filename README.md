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

### Daily Operations
_The workflows you do every day_

| Skill | What It Does |
|-------|--------------|
| **inbox-commander** | Triage email and process support requests in minutes |

### Strategic Thinking
_Think through problems before acting_

| Skill | What It Does |
|-------|--------------|
| **coach** | Learn any domain fast with an expert thinking partner |
| **reality-check** | Find the gaps in your plan before your stakeholders do |
| **interview** | Flesh out requirements with non-obvious questions |
| **create-briefing** | Create shareable briefing documents (dual-audience: human + AI) |

### Research & Analysis
_Investigate, evaluate, recommend_

| Skill | What It Does |
|-------|--------------|
| **technical-orientation** | Explain technical things to non-engineers quickly |

### AI Boosts
_Advanced hacks that make AI work better_

| Skill | What It Does |
|-------|--------------|
| **prompt-improver** | Turn rough ideas into AI prompts that actually work |
| **skill-customizer** | Adapt any skill to your specific workflow |
| **ralph-loop-creator** | Generate structured prompts for autonomous AI work |
| **sensitive-content-scanner** | Scan files for sensitive content before sharing |

### Role-Specific
_Install if relevant to your responsibilities_

**Finance Ops:**

| Skill | What It Does |
|-------|--------------|
| **credits-inventory** | Find the startup credits you're not using |
| **monthly-financials** | Turn bookkeeper's export into runway insights *(coming soon)* |

## What's the Difference?

**Claude can be your:**
- **Thought partner** — Coach, Reality Check, Interview
- **Tireless assistant** — Inbox Commander
- **Expert researcher** — Technical Orientation
- **AI enhancer** — Prompt Improver, Skill Customizer, Ralph Loop Creator

## Skill Structure

Each skill lives in its own directory:

```
skills/
├── coach/
│   ├── SKILL.md              # Main skill definition
│   └── references/           # Supporting files
│       ├── coaching-modes.md
│       └── mental-models.md
├── inbox-commander/
│   ├── SKILL.md
│   └── references/
│       ├── classification-rules.md
│       └── known-senders.md
└── ...
```

## Customization

Skills work out of the box, but they're better when personalized.

**Quick setup:**
1. Read [CUSTOMIZATION-GUIDE.md](./CUSTOMIZATION-GUIDE.md)
2. Fill in placeholders with your values
3. Add your own context to `references/` files

**Examples of customization:**
- Add your preferred newsletter senders to inbox-commander
- Set your knowledge archive path for coach
- Add your investor relationships to credits-inventory

## Platform Compatibility

These skills work across Claude interfaces:

| Platform | Status |
|----------|--------|
| Claude Code | Full support |
| Claude Desktop | Full support |
| Claude Co-work | Skills supported |
| Claude API | Can load skills programmatically |

## Contributing

Found a bug? Have an improvement? PRs welcome.

Please:
- Keep skills focused (one job per skill)
- Include examples in SKILL.md
- Test before submitting
- No personal data in examples

## License

MIT License. See [LICENSE](./LICENSE).

## About

Built by operators, for operators. Part of the [Operator Superpowers](https://operatorsuperpowers.com) project.

---

*Last synced: 2026-01-15*
*Skills: 12 (11 active + 1 coming soon)*
