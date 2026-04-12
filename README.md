# Example repo Ops template

[![PR Reviews][pr-reviews-image]][pr-reviews-link]
[![Status][gha-image-check-main]][gha-link-check-main]
[![License][license-image]][license-link]

Template repository for applying Cogni-AI-OU operations standards, reusable workflows,
prompt catalogs, coding instructions, and agent guidance to a project repository,
including Claude and OpenCode automation.

## Getting Started

1. Install the local validation tooling:

   ```bash
   python3 -m pip install pre-commit
   pre-commit install
   python3 -m pip install -r .devcontainer/requirements.txt
   ```

2. Run the repository checks:

   ```bash
   pre-commit run -a
   ```

3. Review the core guidance:
    - [AGENTS.md](AGENTS.md) for repository-wide agent guidance
    - [CLAUDE.md](CLAUDE.md) for Claude-specific guidance
    - [.github/copilot-instructions.md](.github/copilot-instructions.md) for coding standards
    - [.github/agents/README.md](.github/agents/README.md) for installed custom agent profiles
    - [.tours/getting-started.tour](.tours/getting-started.tour) for a guided walkthrough

## Development

- Keep repository standards aligned with
  [.github/prompts/repository-setup.prompt.md](.github/prompts/repository-setup.prompt.md).
- Use reusable workflows in [.github/workflows/](.github/workflows/) instead of duplicating CI logic.
- Use the checked-in `.opencode/` and `opencode.json` files when enabling OpenCode automation.
- Run targeted checks when iterating locally:

  ```bash
  pre-commit run markdownlint -a
  pre-commit run yamllint -a
  ```

- Set `ANTHROPIC_API_KEY` in repository secrets to enable the Claude workflows.
- Set `OPENCODE_API_KEY` in repository secrets to enable the OpenCode workflows.

## Project Layout

- `.devcontainer/`: shared development container configuration and dependencies
- `.github/`: workflows, prompts, instructions, matchers, and contribution metadata
- `.opencode/`: OpenCode agent, command, and local configuration assets
- `.tours/`: VS Code CodeTour onboarding guides
- `AGENTS.md`: repository-specific agent execution guidance
- `CLAUDE.md`: Claude Code workflow guidance
- `README.md`: repository overview and local development entry point

## AI Agents

This repository includes guidance for multiple agent surfaces and reusable prompt assets.

| File/Directory | Audience | Purpose |
| -------------- | -------- | ------- |
| [AGENTS.md](AGENTS.md) | All agents | Repository-specific guidance and workflows |
| [CLAUDE.md](CLAUDE.md) | Claude | Claude-specific configuration |
| [.github/agents/](.github/agents/) | Custom agents | Shared custom agent profiles including Cogni AI |
| [.github/copilot-instructions.md](.github/copilot-instructions.md) | Copilot | Coding standards and project context |
| [.opencode/](.opencode/) | OpenCode | Agent, command, and config assets for OpenCode automation |
| [.github/prompts/](.github/prompts/) | All | Prompt templates for chat and GitHub Models |
| [.github/skills/](.github/skills/) | All agents | Reusable capabilities for common tasks |
| [.github/instructions/](.github/instructions/) | Linters & agents | Language-specific editing standards |

## Contributing

See [.github/CONTRIBUTING.md](.github/CONTRIBUTING.md) for contribution expectations.
Before opening a PR, run `pre-commit run -a` and confirm the relevant workflows still apply.

## License

This repository is licensed under MIT. See [LICENSE](LICENSE) for the full text.

<!-- Named links -->

[pr-reviews-image]: https://img.shields.io/github/issues-pr/Cogni-AI-OU/example-ops-template?label=PR+Reviews&logo=github
[pr-reviews-link]: https://github.com/Cogni-AI-OU/example-ops-template/pulls
[gha-image-check-main]: https://github.com/Cogni-AI-OU/example-ops-template/actions/workflows/check.yml/badge.svg?branch=main
[gha-link-check-main]: https://github.com/Cogni-AI-OU/example-ops-template/actions?query=workflow%3ACheck+branch%3Amain
[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-link]: https://tldrlegal.com/license/mit-license
