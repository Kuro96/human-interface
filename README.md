# human-interface

Human interface engineering rules for AI coding agents building, changing, or reviewing graphical user interfaces (GUI) and command-line interfaces (CLI).

[简体中文](<README.zh-CN.md>) · [Read the skill](<SKILL.md>)

## What it covers

| Area | Focus |
| --- | --- |
| All interfaces | Human-readable names, primary results, sensible defaults, concise output, actionable errors |
| GUI | Main-workspace priority, compact panels, grouped rows, a single scroll area, host theme tokens |
| CLI | Separate results and logs, simple commands, compact progress, terminal-aware formatting |
| Before coding | **Filter → Consolidate → Adapt** |

The complete rules live in [SKILL.md](<SKILL.md>).

## Install

Clone the repository:

```sh
git clone https://github.com/Kuro96/human-interface.git
```

Copy or link [SKILL.md](<SKILL.md>) into your coding agent's skill directory using this layout:

```text
<agent-skills-directory>/
└── human-interface/
    └── SKILL.md
```

Use your agent's instructions to load local skills. The skill name is `human-interface`.

For DeepSeek Harness, clone directly into its user skill directory instead:

```sh
mkdir -p "$HOME/.dsh/skills"
git clone https://github.com/Kuro96/human-interface.git "$HOME/.dsh/skills/human-interface"
```

## Use

Ask your agent to apply the skill to a concrete interface task:

> Use human-interface to review this settings page. Apply Filter, Consolidate, and Adapt before making changes.

> Use human-interface to build a file-listing CLI with useful defaults, primary results on stdout, and progress on stderr.

For agents that accept instruction files directly, attach [SKILL.md](<SKILL.md>) to the task.

## Examples

| Situation | Human-facing result |
| --- | --- |
| An internal project record | The project name in the list; technical metadata in an on-demand details view |
| A secondary panel with no content | A collapsed panel that leaves space for the main workspace |
| A long-running CLI operation | One updating progress indicator on stderr and a concise completion summary |
| Output piped to a file, or `--json` / `--plain` | Undecorated output, with primary data on stdout and diagnostics on stderr |
| A failed save | “Could not save changes. Check your connection and try again.” |

CLI formatting also respects `NO_COLOR`. GUI styling uses the host project's CSS variables.

## Contributing

Open an issue or pull request with the interface problem, a concrete example, and the proposed improvement. Keep rule changes in [SKILL.md](<SKILL.md>) and update both language versions of the usage guide together.
