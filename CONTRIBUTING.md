# Contributing to AntiTokens

Thanks for helping make Claude Code more token-efficient!

## How to Contribute

### Found a Token Waste Pattern?

If you've noticed a behavior where Claude Code wastes tokens that AntiTokens doesn't cover yet:

1. Open an issue describing the pattern with a **before/after** example
2. Better yet: submit a PR adding the rule to `token-optimizer.md`

### PR Guidelines

- Keep rules concrete and actionable — prefer specific scenarios over abstract advice
- Each rule should map to a measurable token savings
- Match the existing format: scenario → correct action, not prose

### Skill File Structure

The skill uses Claude Code's skill format:

```yaml
---
name: token-optimizer
description: One-line summary of what this skill does
metadata:
  type: custom-skill
---
```

Rules are organized under numbered sections. Add new rules under the most relevant section, or create a new section if none fits.

### Testing

After editing the skill:

1. Copy it to `~/.claude/skills/token-optimizer.md`
2. Start a Claude Code session and run `/token-optimizer`
3. Perform a common task and compare token usage

## Code of Conduct

Keep it brief. Keep it useful. Keep it token-efficient.
