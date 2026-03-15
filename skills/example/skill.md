---
description: Demonstrate the standard skill format with a simple greeting
trigger: When user invokes /example to see a skill demonstration
---

# Example Skill

This is a demonstration skill showing the standard format for Claude Code Skills.

## Instructions

When this skill is invoked:

1. Greet the user and explain that this is an example skill
2. Show the key components of a well-structured skill:
   - YAML frontmatter with description and trigger
   - Clear purpose statement
   - Step-by-step instructions
   - Example usage
3. Suggest next steps for the user

## Response Template

Respond with:

```
Hello! This is the example skill demonstrating the standard format.

A good skill includes:
- Clear description in frontmatter
- Specific trigger conditions
- Detailed instructions
- Consistent output format

To create your own skill:
1. Copy templates/skill-template.md
2. Customize for your use case
3. Save to skills/<your-skill-name>/skill.md
4. Test with /<your-skill-name>
```

## Example Usage

```
/example
```

This will display the demonstration message above.
