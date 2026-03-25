---
name: cli-design
description: Use when designing, building, or reviewing a command-line interface (CLI) tool. Provides a checklist of standard CLI conventions. Do not use for non-CLI applications.
---

# CLI design checklist

## Help and version

- Provide --help/-h with clear usage, options, and examples; include required parameters in examples.
- Provide --version (use -V); reserve -v for --verbose.

## Input and output

- Support stdin/stdout piping; allow output redirection (e.g., --output for file creation).
- Offer machine-readable output (e.g., --json) when emitting structured data.

## Shell integration

- Provide shell completion scripts for major shells (bash, zsh, fish, powershell); include a command to generate them (e.g., `cli completion zsh`).
- Use consistent flag naming (prefer kebab-case for long flags).

## Safety and control

- For modifying/deleting actions, provide --dry-run and an explicit bypass (--yes/--force).
- Provide controllable logging (--quiet, --verbose, or --trace).
- Use deterministic exit codes (0 success, non-zero failure) and avoid silent fallbacks.
- Implement strictly non-interactive modes for CI/CD environments.

## Lifecycle and updates

- Implement non-blocking update notifications to inform users of new versions.
- Follow Semantic Versioning (SemVer) for version numbers.

## Configuration

- For JSON configuration, define/update a JSON Schema and validate config on load.
- Support configuration via environment variables for sensitive or environment-specific data.

## User interface and feedback

- Support colors (use standard environment variables like `NO_COLOR` to disable).
- Detect TTY/interactive environments; use appropriate output (e.g., avoid spinners or complex bars in non-TTY).
- Provide progress indicators (spinners, progress bars) for long-running tasks.

## Interactive prompts

- Provide required context before asking; for yes/no prompts, Enter means "Yes" and "n" means "No".
