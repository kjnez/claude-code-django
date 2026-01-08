# Claude Code Skills

This directory contains project-specific skills that provide Claude with domain knowledge and best practices for this Django codebase.

## Available Skills

| Skill | Description |
|-------|-------------|
| [skill-creator](./skill-creator/SKILL.md) | Guide for creating effective skills that extend Claude's capabilities |
| [django-extensions](./django-extensions/SKILL.md) | Django-extensions management commands for introspection, debugging, and development |
| [systematic-debugging](./systematic-debugging/SKILL.md) | Four-phase debugging methodology with root cause analysis |

## When to Use Each Skill

### skill-creator
Use when you want to create a new skill or update an existing one. This skill provides guidance on:
- Skill structure and anatomy
- Writing effective descriptions and triggers
- Choosing appropriate degrees of freedom
- Bundling resources (scripts, references)

### django-extensions
Use when you need to:
- Explore URL routes, models, or settings
- Debug Django project structure
- Run enhanced shell (shell_plus) with auto-imported models
- Profile server performance
- Compare models to database schema (sqldiff)

### systematic-debugging
Use when you need to:
- Investigate bugs or unexpected behavior
- Fix test failures
- Troubleshoot issues with a methodical approach
- Ensure root cause analysis before applying fixes

## How Skills Work

Skills are automatically invoked when Claude recognizes relevant context. Each skill provides:

- **When to Use** - Trigger conditions
- **Core Patterns** - Best practices and examples
- **Anti-Patterns** - What to avoid
- **Integration** - How skills connect

## Adding New Skills

1. Create directory: `.claude/skills/skill-name/`
2. Add `SKILL.md` (case-sensitive) with YAML frontmatter:
   ```yaml
   ---
   # Required fields
   name: skill-name              # Lowercase, hyphens, max 64 chars
   description: What it does and when to use it. Include trigger keywords.  # Max 1024 chars

   # Optional fields
   allowed-tools: Read, Grep, Glob    # Restrict available tools
   model: claude-sonnet-4-20250514    # Specific model to use
   ---
   ```
3. Include standard sections: When to Use, Core Patterns, Anti-Patterns, Integration
4. Add to this README
5. Add triggers to `.claude/hooks/skill-rules.json`

**Important:** The `description` field is critical—Claude uses semantic matching on it to decide when to apply the skill. Include keywords users would naturally mention.

## Maintenance

- Update skills when patterns change
- Remove outdated information
- Add new patterns as they emerge
- Keep examples current with codebase
