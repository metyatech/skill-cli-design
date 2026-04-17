---
name: cli-design
description: Use when designing, building, or reviewing a command-line interface (CLI) tool. Provides a checklist of standard CLI conventions. Do not use for non-CLI applications.
---

# CLI design checklist

## Help and version

- A CLI MUST provide `--help` and `-h` flags with clear usage,
  options, and examples. Examples MUST include all required
  parameters.
- A CLI MUST provide `--version` and `-V` flags. The agent MUST
  reserve `-v` for `--verbose`.

## Input and output

- A CLI MUST support stdin/stdout piping and MUST allow output
  redirection (e.g., `--output` for file creation).
- A CLI emitting structured data MUST offer machine-readable
  output (e.g., `--json`).

## Shell integration

- Provide shell completion scripts for major shells (bash, zsh, fish, powershell); include a command to generate them (e.g., `cli completion zsh`).
- Use consistent flag naming (prefer kebab-case for long flags).

## Safety and control

- A CLI that modifies or deletes data MUST provide `--dry-run`
  and an explicit bypass flag (`--yes` or `--force`).
- A CLI MUST provide controllable logging (`--quiet`, `--verbose`,
  or `--trace`).
- A CLI MUST use deterministic exit codes: 0 for success,
  non-zero for failure. The agent MUST NOT introduce silent
  fallbacks.
- A CLI MUST implement strictly non-interactive modes for CI/CD
  environments.

## Lifecycle and updates

- Implement non-blocking update notifications to inform users of new versions.
- Follow Semantic Versioning (SemVer) for version numbers.

## Configuration

- A CLI that consumes JSON configuration MUST define and update a
  JSON Schema and MUST validate configuration on load.
- A CLI MUST support configuration via environment variables for
  sensitive or environment-specific data.

## User interface and feedback

- Support colors (use standard environment variables like `NO_COLOR` to disable).
- Detect TTY/interactive environments; use appropriate output (e.g., avoid spinners or complex bars in non-TTY).
- Provide progress indicators (spinners, progress bars) for long-running tasks.

## Interactive prompts

- An interactive prompt MUST provide required context before
  asking. For yes/no prompts, Enter MUST mean "Yes" and "n" MUST
  mean "No".
