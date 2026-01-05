# Copilot Instructions for ... Ops

## Project Overview

TBC

## Coding Standards

### Python

- Use **Python 3.11+**.
- Use `uv` script headers for dependency management:

  ```python
  #!/usr/bin/env -S uv run --script
  # /// script
  # requires-python = ">=3.11"
  # dependencies = [
  #     "xero-python",
  #     "PyYAML",
  # ]
  # ///
  ```

- Follow **PEP 8** style guidelines.
- Use `argparse` for CLI argument parsing.
- Handle `BrokenPipeError` for CLI tools that might be piped to `head` or `grep`:

  ```python
  import signal
  signal.signal(signal.SIGPIPE, signal.SIG_DFL)
  ```

### TBC API

- Use the TBC SDK.
- Handle API rate limits and errors gracefully.

## Formatting Guidelines

### Markdown

Follow the Markdown rules in `.github/instructions/markdown.instructions.md`, which mirror the repository markdownlint configuration.

### YAML Guidelines

- empty-lines (yamllint): Limit consecutive blank lines to one.
- indentation (yamllint): Avoid wrong indentation.
- line-length (yamllint): No long lines (max. 120 characters).
- new-line-at-end-of-file (yamllint): Enforce new line character at the end of file.
- truthy (yamllint): Truthy value should be one of [false, true].
- Ensure items are in lexicographical order when possible.
- When embedding code blocks or inline YAML snippets within lists, end with a trailing newline to preserve indentation.

Formatting rules are defined in `.yamllint` (YAML) and `.markdownlint.yaml` (Markdown).

Notes:

- Project utilizes Codespaces with config at `.devcontainer/devcontainer.json` and requirements at `.devcontainer/requirements.txt`.
- GitHub Actions run pre-commit checks (`.pre-commit-config.yaml`).

## Project Structure

TBC

## Common Tasks

TBC
