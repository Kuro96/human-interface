---
name: human-interface
description: Apply these rules when you build, change, or review Graphical User Interfaces (GUI) or Command-Line Interfaces (CLI). This skill stops the direct output of backend data structures to the user interface.
---

# Human Interface Engineering Rules (GUI and CLI)

Build interfaces for human users, not as a raw dump of backend code. Do not map internal data structures or function parameters directly to the screen or terminal. Obey these rules when you write GUI or CLI code.

## 1. Universal Interface Rules (All Interfaces)
Apply these core rules to both graphical views and command-line tools:
- **Hide internal identifiers**: Show only clear, human-readable names. Do not show internal IDs, route prefixes, enum keys, or raw database fields in visible labels or default terminal output.
- **Hide secondary data by default**: Show only primary results in the default view. Put secondary metadata, debug data, and long text behind on-demand triggers (use drawers or tooltips in GUI; use `--verbose` or `inspect` commands in CLI).
- **Use sensible defaults**: Do not force the user to configure every internal parameter. Set safe default values for common tasks.
- **Remove repeated text**: Group shared titles, units, and notes into one header. Do not repeat the same static text for every item in a list or log.
- **Write actionable error messages**: Do not show raw stack traces or internal state codes to the user. State clearly what failed and how the user can fix it.

## 2. Graphical User Interface (GUI) Rules
Apply these rules when you write HTML, CSS, or frontend component code:
- **Give maximum space to the main work area**: Give the primary list or canvas the largest part of the screen (`flex: 1` and `min-height: 0`).
- **Collapse empty areas**: When a secondary panel has no data, hide it or collapse it into one thin bar. Do not show a large empty box.
- **Do not put boxes inside boxes**: Do not put a bordered card around each single field or row. Put related items in one shared container and separate them with empty space or thin lines.
- **Use one scroll bar**: Use only one vertical scroll bar in each view area. Do not use a scroll bar and pagination buttons on the same short list.
- **Inherit host theme tokens**: Use existing CSS variables from the host project. Do not hardcode hex or RGB color values.

## 3. Command-Line Interface (CLI) Rules
Apply these rules when you write terminal tools, scripts, or console output:
- **Separate data from logs**: Send only primary result data to standard output (`stdout`). Send all progress messages, warnings, and errors to standard error (`stderr`).
- **Keep flags simple**: Map common actions to short subcommands and simple flags. Do not create a required CLI flag for every internal function argument.
- **Protect the terminal scroll buffer**: Do not print a new line for each step of a loop. Update progress on a single line (such as a progress bar or spinner), and print one short summary at the end.
- **Adapt to the terminal environment**:
  - When `stdout` is an interactive terminal (TTY), format output as clean, aligned tables or compact lists.
  - When `stdout` is piped to another command or file (non-TTY), or when the `--json` or `--plain` flag is present, disable ANSI colors, spinners, and decorative borders. Respect the `NO_COLOR` environment variable.

## 4. Pre-Coding Verification Steps
Complete these three steps before you write interface code:
1. **Filter**: Remove machine prefixes, internal enum keys, and system logic notes from default user output and flags.
2. **Consolidate**: Merge repeated UI cards into compact rows (GUI), or merge repetitive log lines into one single-line progress indicator (CLI).
3. **Adapt**: Verify that the interface uses host CSS variables (GUI) or respects TTY streams and pipe redirection (CLI).
