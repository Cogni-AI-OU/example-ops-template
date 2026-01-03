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

- Keep line length <=120 characters (see `.markdownlint.yaml`).
- Surround headings and lists with blank lines; fence code blocks with blank lines.
- Avoid trailing spaces; ensure a single trailing newline.

### YAML Guidelines

- yaml[empty-lines]: Avoid too many blank lines (1 > 0).
- yaml[indentation]: Avoid wrong indentation.
- yaml[line-length]: No long lines (max. 120 characters).
- yaml[new-line-at-end-of-file]: Enforce new line character at the end of file.
- yaml[truthy]: Truthy value should be one of [false, true].
- Ensure items are in lexicographical order when possible.
- When embedding code blocks or inline YAML snippets within lists, end with a trailing newline to preserve indentation.

Formatting rules are defined in `.yamllint` (YAML) and `.markdownlint.yaml` (Markdown).

Notes:

- Project utilizes Codespaces with config at `.devcontainer/devcontainer.json` and requirements at `.devcontainer/requirements.txt`.
- GitHub Actions run pre-commit checks (`.pre-commit-config.yaml`).

## Example `pyproject.toml`

```toml
[build-system]
requires = ["hatchling"]
build-backend = "hatchling.build"

[project]
name = "example-ops-utility"
version = "0.1.0"
description = "Utility for interacting with the Example service via API."
readme = "README.md"
license = { file = "LICENSE" }
requires-python = ">=3.11"
dependencies = [
  "requests>=2.32.0",
  "tabulate>=0.9.0",
  "pyyaml>=6.0.1",
]

authors = [
  { name = "Cogni AI Example" },
]

[project.urls]
Homepage = "https://github.com/Cogni-AI-OU/example-ops-template"
Repository = "https://github.com/Cogni-AI-OU/example-ops-template"
```

## Project Structure

TBC

## Common Tasks

TBC
