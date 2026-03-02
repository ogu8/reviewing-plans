# Reviewing Plans Skill

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skill that reviews AI-generated implementation plans before execution — catching scope creep, vague steps, missing verification, and hidden risks before they become problems.

## Why

AI coding agents are great at generating plans. They're also great at generating plans that sound smart but fall apart during execution — vague steps, bundled mega-tasks, missing error handling, no verification, and scope that quietly expands beyond what you asked for.

This skill forces a structured review before you approve. It checks whether a diligent but literal executor can follow the plan step by step and arrive at exactly what you wanted — nothing more, nothing less.

## What It Checks

1. **Problem & Scope** — Is it solving your actual problem? No extras, no hand-waving.
2. **Step Quality** — Each step is specific, atomic, ordered, and verifiable.
3. **Dependencies & Risk** — Correct order, blast radius contained, graceful failure.
4. **Verification** — Concrete checks at each step and end-to-end.
5. **What's Missing** — Error handling, existing tests, edge cases, cleanup.
6. **Exit Criteria** — "Done" is defined and independently verifiable.
7. **Red Flags** — Quick pattern-match for common plan smells.

## Install

```bash
# Clone into your Claude Code skills directory
git clone https://github.com/ogu8/reviewing-plans.git ~/.claude/skills/reviewing-plans
```

Or manually copy `SKILL.md` into `~/.claude/skills/reviewing-plans/`.

## Usage

The skill activates automatically when you:
- Ask Claude Code to review an implementation plan
- Are handed a plan to approve (e.g., from plan mode)
- Ask if a plan is ready to act on

You can also invoke it directly:

```
/reviewing-plans
```

## Red Flags Cheat Sheet

| You see | It means |
|-|-|
| "Refactor/update as needed" | No plan, will improvise |
| "For completeness" / "While we're here" | Scope creep |
| Steps with no verification | Will claim success unchecked |
| New abstractions for one use case | Over-engineering |
| "Should be straightforward" | Hasn't thought it through |
| No mention of existing tests | Will break things silently |
| "We'll handle that later" | Deferring the hard part |
| Plan starts with code changes, not verification | Guessing, not diagnosing |

## License

[MIT](LICENSE)
