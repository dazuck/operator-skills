---
name: ralph-loop-creator
description: Generate structured prompts for autonomous AI work. Creates PROMPT.md with phases, validation criteria, and completion promise from a rough description or PRD.
argument-hint: <description-or-prd-file> [output-path]
---

# Ralph Loop Creator

## Core Purpose

Transform a rough idea, description, or PRD into a fully structured Ralph Loop prompt ready for execution. This automates the tedious work of structuring phases, validation criteria, and completion promises.

Based on @GeoffreyHuntley's Ralph Wiggum technique, @callam53's workflow guide.

## Operating Philosophy

### What This Skill IS

- **Prompt scaffolder** that creates structured Ralph-ready prompts
- **Phase decomposer** that breaks work into iterative chunks
- **Validation designer** that ensures each phase has clear success criteria
- **Kanban translator** that treats phases like tickets with ACs

### What This Skill IS NOT

- **Interviewer** (use /interview first if requirements are vague)
- **Ralph runner** (use /ralph-loop to actually run it)

## When to Use This Skill

Use AFTER you have clarity on what to build:

```
Rough idea → /interview → /ralph-loop-creator → /ralph-loop
                  ↑              ↑
            (if spec has    (THIS SKILL)
             ambiguities)
```

## Activation Protocol

When invoked with `/ralph-loop-creator <input> [output-path]`:

1. **Parse input**:
   - If file path: read the file (PRD, notes, rough plan)
   - If description: use the provided text

2. **Assess completeness**:
   - Are requirements clear enough to structure?
   - If not: suggest `/interview` first

3. **Gather context**:
   - Read relevant CLAUDE.md for project patterns
   - Check for existing architecture/infrastructure to reference
   - Identify dependencies and constraints

4. **Generate PROMPT.md**:
   - Mission statement + completion promise
   - Context section (what exists, architecture)
   - Scope (in/out)
   - Phases with tasks and validation
   - File structure
   - Environment variables
   - Decision log
   - Success metrics

5. **Output**:
   - Write to specified path (or suggest default)
   - Provide the exact `/ralph-loop` command to run

## PROMPT.md Template

Generate prompts following this structure:

```markdown
# [Feature Name] - Ralph Loop Prompt

## Mission

[1-2 sentence description of what we're building]

**Completion Promise:** When all phases complete and [success criteria], output:

\`\`\`
<promise>[FEATURE_NAME] COMPLETE</promise>
\`\`\`

---

## Context

### What Already Exists

[Relevant existing infrastructure, patterns, files]

| Component | Location | Purpose        |
| --------- | -------- | -------------- |
| [Name]    | [Path]   | [What it does] |

### Architecture Overview

\`\`\`
[ASCII diagram if helpful]
\`\`\`

---

## Scope

### In Scope

- [ ] [Feature/requirement 1]
- [ ] [Feature/requirement 2]

### Out of Scope (Future)

- [Thing explicitly deferred]

---

## Phases

Work through these sequentially. Each phase should result in working, tested code.

### Phase 1: [Foundation/Setup]

**Goal:** [What this phase achieves]

**Tasks:**

1. [Specific task]
2. [Specific task]

**Validation:**

- [ ] [Testable criterion]
- [ ] [Testable criterion]

**Reference:** [Docs/links if relevant]

---

### Phase 2: [Core Feature]

[Same structure]

---

### Phase N: Testing & Documentation

**Goal:** Production-ready with tests and docs.

**Tasks:**

1. Unit tests for [components]
2. Integration tests for [flows]
3. Documentation at [location]

**Validation:**

- [ ] Tests passing
- [ ] Coverage > [X]%
- [ ] Docs complete

---

## Key Files to Create

\`\`\`
[File tree of expected output]
\`\`\`

---

## Environment Variables

\`\`\`bash
[Required env vars with descriptions]
\`\`\`

---

## Decision Log

| Decision | Choice   | Rationale |
| -------- | -------- | --------- |
| [What]   | [Choice] | [Why]     |

---

## Success Metrics

**Functional:**

- [Measurable criterion]

**Quality:**

- [Quality gate]

---

## Notes for Implementation

- [Important gotcha]
- [Pattern to follow]
- [Thing to avoid]

---

## When Complete

Output the completion promise:

\`\`\`
<promise>[FEATURE_NAME] COMPLETE</promise>
\`\`\`
```

## Phase Design Principles

### Good Phases

- **Self-contained**: Can be validated independently
- **Incremental**: Build on previous phases
- **Testable**: Clear pass/fail criteria
- **Sized right**: Not too big (overwhelming) or small (trivial)

### Phase Sequencing

Typical flow:

1. **Foundation** - Setup, dependencies, scaffolding
2. **Core** - Main functionality (may be multiple phases)
3. **Integration** - Wire components together
4. **Polish** - Error handling, edge cases
5. **Testing & Docs** - Always last

### Validation Criteria

Each phase needs checkboxes that are:

- **Binary** - Pass or fail, not subjective
- **Testable** - Can run a command or check to verify
- **Specific** - "Tests pass" not "code works"

```
Good:
- [ ] `npm test` passes with 0 failures
- [ ] Bot joins test meeting within 10 seconds
- [ ] Response latency < 2s measured in logs

Bad:
- [ ] Code is clean
- [ ] Feature works well
- [ ] Good performance
```

## Iteration Estimation

Suggest max iterations based on complexity:

| Phases | Complexity | Suggested Iterations      |
| ------ | ---------- | ------------------------- |
| 2-3    | Simple     | 15-20                     |
| 4-5    | Medium     | 30-40                     |
| 6-8    | Complex    | 50-75                     |
| 8+     | Large      | 100+ (consider splitting) |

## Output Format

After generating PROMPT.md, provide:

```markdown
## Ralph Loop Ready

Created: `[path/to/PROMPT.md]`

**To run:**
\`\`\`
/ralph-loop "$(cat [path/to/PROMPT.md])" --max-iterations [N] --completion-promise "[PROMISE]"
\`\`\`

**Or with file reference:**
\`\`\`
/ralph-loop [path/to/PROMPT.md] --max-iterations [N] --completion-promise "[PROMISE]"
\`\`\`

**Estimated phases:** [N]
**Suggested iterations:** [N]
**Completion promise:** [PROMISE]
```

## Callam's Tips (Embedded)

Include these patterns in generated prompts:

1. **Commit after each step** - Add to phase tasks: "Commit changes with descriptive message"

2. **Code review as phase** - Include review validation:

   ```
   **Validation:**
   - [ ] Code review agent finds no critical issues
   ```

3. **Kanban mindset** - Treat each phase like a ticket with ACs

4. **Brick by brick** - Phases should be small enough to complete in 2-5 iterations each

5. **Testing loop** - Every phase should have runnable validation

## Integration with Your Workflow

This skill generates prompts compatible with your `/ralph-loop` plugin:

```
/ralph-loop-creator "Build a CLI tool that converts markdown to PDF"
→ Creates: ./docs/md-to-pdf/PROMPT.md
→ Suggests: /ralph-loop "$(cat ./docs/md-to-pdf/PROMPT.md)" --max-iterations 30 --completion-promise "MD_TO_PDF_COMPLETE"
```

For complex features, use the full workflow:

```
/interview docs/X/prd.md              # Flesh out requirements
/ralph-loop-creator docs/X/prd.md     # Generate structured prompt
/ralph-loop ...                        # Execute
```
