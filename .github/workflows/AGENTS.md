# GitHub Actions Workflows (Agent Catalog)

Authoritative, agent-facing catalog of workflows in this repository. Use this when loading or modifying
workflows and keep it in sync with the files in this directory.

For a human-readable overview, see [README.md](README.md).

## Workflow catalog

| Workflow | Purpose | Key triggers / notes |
| -------- | ------- | -------------------- |
| [check.yml](check.yml) | Linting and quality gates via actionlint and pre-commit | push, pull_request, schedule; reusable via `workflow_call` |
| [claude-review.yml](claude-review.yml) | Automated PR review with Claude | pull_request (non-bot), `workflow_call` with `pr_number` |
| [claude.yml](claude.yml) | Interactive Claude mentions on issues/PRs | issue_comment, pull_request_review_comment, workflow_dispatch, `workflow_call` |
| [opencode-review.yml](opencode-review.yml) | OpenCode PR review | pull_request_target (trusted authors), `/review` comments, workflow_dispatch, `workflow_call` |
| [opencode.yml](opencode.yml) | Interactive OpenCode mentions on issues/PRs | issue_comment and review comment `/oc` or `/opencode`, workflow_dispatch, `workflow_call` |
| [devcontainer-ci.yml](devcontainer-ci.yml) | Build/test devcontainer and required tools/packages | push/pull_request touching .devcontainer or workflow; schedule; `workflow_call` |

## Details

### check.yml

- Purpose: run actionlint and pre-commit to enforce workflow and repo standards.
- Reusable: `uses: Cogni-AI-OU/.github/.github/workflows/check.yml@main`.
- Jobs: `actionlint`, `pre-commit`.

### claude-review.yml

- Purpose: AI code review that comments on PRs.
- Inputs: `pr_number` (required for `workflow_call`), `model` (default `claude-opus-4-5`),
  `additional_prompt` (optional extra review instructions).
- Trigger: pull_request (skips bot authors) and `workflow_call`.
- Reusable: `uses: Cogni-AI-OU/.github/.github/workflows/claude-review.yml@main`.

### claude.yml

- Purpose: respond to `@claude` mentions for interactive assistance.
- Input: `model` (default `claude-opus-4-5`).
- Triggers: issue_comment, pull_request_review_comment, workflow_dispatch, `workflow_call`.
- Reusable: `uses: Cogni-AI-OU/.github/.github/workflows/claude.yml@main`.
- Access: restricted to OWNER, MEMBER, COLLABORATOR, CONTRIBUTOR associations.

### opencode-review.yml

- Purpose: OpenCode-driven PR review.
- Inputs: `pr_number` (required for `workflow_call`/`workflow_dispatch`), `agent`, `model`,
  `prompt`, and `additional_prompt`.
- Triggers: pull_request_target for trusted authors, `/review` issue/review comments from trusted users,
  `workflow_call`, and `workflow_dispatch`.
- Reusable: `uses: Cogni-AI-OU/.github/.github/workflows/opencode-review.yml@main`.

### opencode.yml

- Purpose: respond to `/oc`, `/opencode`, or `@opencode` mentions for interactive assistance.
- Inputs: `agent`, `model`, and `prompt`.
- Triggers: issue_comment, pull_request_review_comment, workflow_dispatch, `workflow_call`.
- Reusable: `uses: Cogni-AI-OU/.github/.github/workflows/opencode.yml@main`.
- Access: restricted to trusted non-bot collaborators, contributors, members, and owners.

### devcontainer-ci.yml

- Purpose: build and validate the dev container; ensure required tools and Python packages exist.
- Inputs: `required_commands` (defaults to common CLI tools), `required_python_packages`
  (defaults to ansible, ansible-lint, docker, molecule, pre-commit, uv).
- Triggers: pull_request/push affecting `.devcontainer/` or this workflow; weekly schedule;
  `workflow_call`.
- Permissions: callers must grant `packages: write` when pushing images to GHCR.
- Reusable: `uses: Cogni-AI-OU/.github/.github/workflows/devcontainer-ci.yml@main`.

## Model selection

- `claude-haiku-4-5`: fastest, best for quick tasks.
- `claude-opus-4-5`: default balance.
- `claude-sonnet-4-5`: most capable.
- Provide `model` input when calling `claude.yml` or `claude-review.yml`; defaults to `claude-opus-4-5`.
- OpenCode workflows accept `opencode/*` model IDs and default to `opencode/claude-opus-4-5`.

## Notes

- Follow [.github/instructions/github-workflows.instruction.md](../instructions/github-workflows.instruction.md)
  when editing workflow files (ordering, formatting, validation).
- Keep this catalog updated when workflows are added, removed, or renamed.
