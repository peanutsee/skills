# Contributing to AI Agent Skills

Thank you for your interest in contributing! We want to build the most useful library of AI agent skills together.

## How to Add a New Skill

1. **Fork the repository** (or create a new branch if you have access).
2. **Create a new directory** for your skill (e.g., `my-new-skill`).
3. **Copy the template** from `skill-template/SKILL.md` into your new directory.
4. **Fill out the template** with your skill's details.
5. **Ensure consistency**:
   - Use clear, actionable instructions.
   - Include "Use this skill when" and "Do not use this skill when" sections.
   - Define specific "Capabilities" and "Behavioral Traits".
6. **Submit a Pull Request** with a clear description of what your skill does.

## Skill Format Requirements

All skills must be contained in a `SKILL.md` file within their own directory. The file should start with YAML frontmatter:

```yaml
---
name: your-skill-name
description: A short, concise description of the skill.
metadata:
  model: inherit
---
```

Follow the structure provided in the [skill-template](file:///Users/peanutsee/Desktop/projects/skills/skill-template/SKILL.md).

## Pull Request Process

- Ensure your branch is up to date with `main`.
- Provide a clear title and description for your PR.
- Wait for a maintainer to review and merge your changes.

## Code of Conduct

By participating in this project, you agree to abide by our [Code of Conduct](file:///Users/peanutsee/Desktop/projects/skills/CODE_OF_CONDUCT.md).
