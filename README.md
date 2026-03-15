# Claude Code Skills Library

A collection of reusable Claude Code Skills curated by Freeman, designed for sharing, learning, and collaboration.

## What are Skills?

Skills are reusable prompt templates for Claude Code that can be invoked with slash commands (e.g., `/skill-name`). They help automate common workflows and ensure consistent, high-quality outputs.

## Repository Structure

```
MySkills/
├── skills/           # All available skills
│   └── <skill-name>/
│       └── skill.md  # Skill definition file
├── templates/        # Templates for creating new skills
├── CLAUDE.md         # Project configuration
└── README.md
```

## How to Use

### 1. Install a Skill

Copy the skill folder to your Claude Code skills directory:

```bash
# User-level (available in all projects)
cp -r skills/<skill-name> ~/.claude/skills/

# Project-level (available only in current project)
cp -r skills/<skill-name> .claude/skills/
```

### 2. Invoke a Skill

In Claude Code, use the slash command:

```
/<skill-name>
```

## Available Skills

| Skill | Description |
|-------|-------------|
| `example` | A demonstration skill showing the standard format |
| `merge-videos` | Merge multiple video files into one using ffmpeg |

## Creating Your Own Skill

1. Copy the template from `templates/skill-template.md`
2. Create a new folder under `skills/` with your skill name
3. Save your skill as `skill.md` in that folder
4. Test locally before contributing

See [templates/skill-template.md](templates/skill-template.md) for the standard skill format.

## Skill File Format

A skill file (`skill.md`) consists of:

```markdown
---
description: Short description for skill discovery
trigger: When this skill should be invoked
---

# Skill Name

[Detailed instructions for Claude...]
```

## Contributing

Contributions are welcome! Please:

1. Fork this repository
2. Create a new skill following the template
3. Test your skill thoroughly
4. Submit a Pull Request with:
   - Clear description of what the skill does
   - Example use cases
   - Any dependencies or requirements

## License

Apache License 2.0 - See [LICENSE](LICENSE) for details.

## Author

Freeman (David Cai)

## Links

- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Report Issues](https://github.com/anthropics/claude-code/issues)
