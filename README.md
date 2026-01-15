# Operator Skills

Reusable Claude skills for startup operators and founders.

Skills are instruction sets that tell Claude how to handle specific tasks. Instead of explaining what you need every time, you invoke a skill and Claude knows what to do.

```
/inbox-commander     → Triage your email
/coach               → Think through a problem
/prompt-improver     → Turn rough ideas into effective prompts
```

## Install

### Claude Desktop (Recommended)

1. Download the skill you want as a ZIP (or [download all](https://github.com/dazuck/operator-skills/archive/refs/heads/main.zip))
2. Go to **Settings → Capabilities**
3. Upload the ZIP file
4. Toggle on the skills you want

Skills load automatically when relevant. [Learn more about Skills](https://support.claude.com/en/articles/12512180-using-skills-in-claude).

> **Note:** Skills require Claude Pro, Max, Team, or Enterprise.

### Claude Code

```bash
claude mcp add-skill gh:dazuck/operator-skills
```

### Manual (Other AI Tools)

Copy skill folders to your AI tool's custom instructions directory:

```bash
git clone https://github.com/dazuck/operator-skills.git
cp -r operator-skills/skills/* ~/.claude/skills/
```

Works with any tool that supports markdown instruction files.

## Skills

### Daily Operations

- **inbox-commander** — Process email for fast action, clear priority, and always-improving rules
- **create-briefing** — Synthesize session content into variable formats for both human and AI recipients
- **meeting-sidekick** — Prep that actually prepares you, recaps that capture what matters *(coming soon)*
- **weekly-pulse** — Surface the metrics that matter with context your team can act on *(coming soon)*

### Thinking Partner

- **coach** — Learn any domain fast with a radically candid advisor who challenges your thinking
- **reality-check** — Pressure test plans with the skeptical questions your stakeholders will ask
- **interview** — Surface the requirements you'd miss with targeted, non-obvious questions

### Research & Analysis

- **technical-orientation** — Explain repos and technical things with diagrams and synthesis for non-engineers
- **tool-comparison** — Evaluate tools and vendors with structured criteria and clear recommendations *(coming soon)*

### AI Boosts

- **prompt-improver** — Transform vague ideas into prompts that actually get what you want
- **skill-customizer** — Adapt any skill to your tools, terms, and workflow
- **ralph-loop-creator** — Structure autonomous AI work with phases, validation, and clear completion
- **sensitive-content-scanner** — Catch PII, secrets, and private paths before you share

### Finance Ops

- **credits-inventory** — Find the startup credits and perks you're paying for but not using
- **monthly-financials** — Turn bookkeeper exports into runway insights and variance analysis *(coming soon)*

### People Ops

- **hiring-helper** — Screen candidates against a proven framework that spots what resumes miss
- **onboarding-plan** — New hire onboarding with structure, not improvisation *(coming soon)*

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

Questions, comments, and issues welcome. Open an issue or submit a PR.

## License

MIT License

Copyright (c) 2025

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
