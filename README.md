# Operator Skills

Reusable Claude skills for startup operators and founders.

Skills are instruction sets that tell Claude how to handle specific tasks. Instead of explaining what you need every time, you invoke a skill and Claude knows what to do.

```
/coach               → Think through a problem with a radically candid advisor
/investor-audits     → Draft accurate responses to investor audit requests
/contract-review     → Get a risk assessment on any vendor or services contract
```

## Install

### Claude Code

```bash
claude plugin marketplace add dazuck/operator-skills
claude plugin install operator-skills
```

### Claude Desktop

1. Download the skills you want as a ZIP (or [download all](https://github.com/dazuck/operator-skills/archive/refs/heads/main.zip))
2. Go to **Settings → Capabilities** → Upload the ZIP file
3. Toggle on the skills you want

> Skills require Claude Pro, Max, Team, or Enterprise. Skills load automatically when relevant. [Learn more](https://support.claude.com/en/articles/12512180-using-skills-in-claude).

## Skills

### Thinking Partner

- **coach** — Learn any domain fast with a radically candid advisor who challenges your thinking
- **reality-check** — Pressure test plans with the skeptical questions your stakeholders will ask
- **interview** — Surface the requirements you'd miss with targeted, non-obvious questions

### Writing & Communication

- **writeup** — Transform work sessions into publishable content across tweet, thread, or blog formats
- **create-briefing** — Synthesize session content into variable formats for both human and AI recipients
- **technical-orientation** — Explain repos and codebases with diagrams and synthesis for non-engineers

### Claude Workflows

Tools for getting more out of Claude itself.

- **adversarial-verifier** — Deep verification that assumes nothing is correct; hunts hidden errors
- **handoff** — Session wrap-up with verification, docs update, and handoff message
- **show-and-tell** — Prepare a demo artifact from the last 24 hours of work
- **prompt-improver** — Transform vague ideas into prompts that actually get what you want
- **skill-customizer** — Adapt any skill to your tools, terms, and workflow
- **ralph-loop-creator** — Structure autonomous AI work with phases, validation, and clear completion criteria
- **sensitive-content-scanner** — Catch PII, secrets, and private paths before you share
- **personalize-skills** — Configure Operator Skills for your environment on first install

### Startup Ops

- **inbox-commander** — GTD-style email triage with autonomous actions for clear-cut items
- **credits-inventory** — Find the startup credits and perks you're paying for but not using
- **monthly-financials** — Turn your bookkeeper's export into runway insights and variance analysis
- **investor-audits** — Draft accurate responses to investor audit confirmations and portfolio reporting requests
- **contract-review** — Risk assessment on vendor contracts, MSAs, SOWs, and NDAs

### People Ops

- **hiring-helper** — Screen candidates against a proven framework that spots what resumes miss
- **candidate-screening** — AI-powered candidate evaluation from Greenhouse with a high-agency framework

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
