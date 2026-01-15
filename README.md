# Operator Skills

Reusable Claude skills for startup operators and founders.

Skills are instruction sets that tell Claude how to handle specific tasks. Instead of explaining what you need every time, you invoke a skill and Claude knows what to do.

```
/inbox-commander     → Triage your email
/coach               → Think through a problem
/prompt-improver     → Turn rough ideas into effective prompts
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

### Daily Operations

- **inbox-commander** — Email triage and prioritization
- **create-briefing** — Shareable briefing docs (human + AI readable)
- **meeting-sidekick** — Meeting prep and recap *(coming soon)*
- **weekly-pulse** — Metrics review and progress reporting *(coming soon)*

### Thinking Partner

- **coach** — Expert thinking partner for any domain
- **reality-check** — Find gaps in plans before stakeholders do
- **interview** — Extract requirements with non-obvious questions

### Research & Analysis

- **technical-orientation** — Explain technical concepts to non-engineers
- **tool-comparison** — Evaluate tools and vendors systematically *(coming soon)*

### AI Boosts

- **prompt-improver** — Turn rough ideas into effective AI prompts
- **skill-customizer** — Adapt skills to your workflow
- **ralph-loop-creator** — Structured prompts for autonomous AI work
- **sensitive-content-scanner** — Detect PII/secrets before sharing

### Finance Ops

- **credits-inventory** — Find startup credits and perks you're not using
- **monthly-financials** — Bookkeeper export → runway insights *(coming soon)*

### People Ops

- **hiring-helper** — Screen candidates against a proven hiring framework
- **onboarding-plan** — New hire onboarding that doesn't wing it *(coming soon)*

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
