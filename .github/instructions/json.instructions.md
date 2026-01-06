---
description: 'JSON formatting standards'
applyTo:
  - '**/*.json'
---

# JSON Instructions

## JSON Content Rules

- Use spaces for indentation (2 spaces per level from .editorconfig); avoid tabs.
- End files with a newline (from .editorconfig).
- Use double quotes for all strings and property names (JSON standard).
- Ensure proper comma usage: include commas between elements, but not after the last element in an object or array.
- Use consistent indentation for nested structures.
- Avoid trailing whitespace on lines.
- Keep the JSON structure valid and parseable.

## JSON Structure and Formatting

- **Objects**: Place opening braces on the same line as the property name or at the start of the file.
  Close braces on their own line at the same indentation level as the opening line.
- **Arrays**: For short arrays (single line), place all elements on one line. For longer arrays,
  place each element on its own line with proper indentation.
- **Property Order**: When practical, keep properties in a logical or alphabetical order to improve
  readability and maintainability.
- **Comments**: JSON does not officially support comments. However, some tools (like VS Code settings)
  allow `//` style comments. Use them sparingly and only when the tool explicitly supports them.
  Prefer JSON5 or JSONC formats when extensive comments are needed.
- **Whitespace**: Use consistent spacing around colons (no space before, one space after).

## Validation

- Repository indentation rules come from `.editorconfig` (2 spaces for JSON files).
- Use `pre-commit run check-json -a` or similar JSON validation tools to verify syntax.
- Consider using `jq` for formatting: `jq . file.json` to validate and format JSON files.
- Many editors provide built-in JSON formatting (e.g., VS Code's "Format Document" command).
