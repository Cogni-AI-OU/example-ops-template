Defect: Regression - Missing workflow inputs

The `workflow_call` and `workflow_dispatch` triggers are missing their input definitions (`agent`, `model`, `prompt`), which breaks the ability to customize runs when manually dispatching or calling this workflow from another. These inputs need to be restored.

```suggestion
  workflow_call:
    inputs:
      agent:
        default: build
        description: Agent to use.
        required: false
        type: string
      model:
        default: ${{ vars.OPENCODE_MODEL_DEFAULT || 'opencode/gemini-3.1-pro' }}
        description: Model to use for OpenCode
        required: false
        type: string
      prompt:
        description: Custom prompt to override the default prompt
        required: false
        type: string
  workflow_dispatch:
    inputs:
      agent:
        default: cogni-ai
        description: Agent to use.
        options:
          - build
          - cogni-ai
          - compaction
          - plan
          - summary
          - title
        required: false
        type: choice
      model:
        default: opencode/gemini-3.1-pro
        description: Model to use for OpenCode
        options:
          - opencode/big-pickle
          - opencode/claude-3-5-haiku
          - opencode/claude-haiku-4-5
          - opencode/claude-opus-4-1
          - opencode/claude-opus-4-5
          - opencode/claude-opus-4-6
          - opencode/claude-sonnet-4
          - opencode/claude-sonnet-4-5
          - opencode/claude-sonnet-4-6
          - opencode/gemini-3.1-pro
          - opencode/gemini-3-flash
          - opencode/gemini-3-pro
          - opencode/glm-4.6
          - opencode/glm-4.7-free
          - opencode/glm-5
          - opencode/glm-5.1
          - opencode/gpt-5
          - opencode/gpt-5-codex
          - opencode/gpt-5-nano
          - opencode/gpt-5.1
          - opencode/gpt-5.1-codex
          - opencode/gpt-5.1-codex-max
          - opencode/gpt-5.1-codex-mini
          - opencode/gpt-5.2
          - opencode/gpt-5.2-codex
          - opencode/gpt-5.3-codex
          - opencode/gpt-5.3-codex-spark
          - opencode/gpt-5.4
          - opencode/gpt-5.4-mini
          - opencode/gpt-5.4-nano
          - opencode/gpt-5.4-pro
          - opencode/grok-code
          - opencode/kimi-k2
          - opencode/kimi-k2-thinking
          - opencode/kimi-k2.5
          - opencode/minimax-m2.1-free
          - opencode/minimax-m2.5
          - opencode/minimax-m2.5-free
          - opencode/nemotron-3-super-free
          - opencode/qwen3-coder
          - opencode/qwen3.6-plus-free
        required: false
        type: choice
      prompt:
        description: Custom prompt to override the default prompt
        required: false
        type: string
```