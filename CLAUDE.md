# Claude Code Skills Library

This is a Claude Code Skills repository for sharing reusable prompt templates.

## Project Structure

- `skills/` - Contains all skill definitions, each in its own folder with a `skill.md` file
- `templates/` - Contains templates for creating new skills
- `README.md` - Project documentation

## Guidelines for This Repository

### When Creating Skills

1. Each skill must have its own folder under `skills/`
2. The main skill file must be named `skill.md`
3. Include YAML frontmatter with `description` and `trigger` fields
4. Write clear, actionable instructions
5. Include example use cases when helpful

### Naming Conventions

- Skill folder names: lowercase, hyphen-separated (e.g., `code-review`, `git-commit`)
- Keep names concise but descriptive
- Avoid generic names like `helper` or `util`

### Quality Standards

- Skills should be self-contained and reusable
- Avoid hardcoded paths or project-specific references
- Include error handling guidance where appropriate
- Test skills before adding to the repository

## Language

- Documentation: English preferred, Chinese acceptable
- Skill content: Match the target audience's language preference
