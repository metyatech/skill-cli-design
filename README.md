# skill-cli-design

Agent skill for designing and reviewing command-line interface (CLI) tools. Provides a standard conventions checklist covering help, versioning, I/O, safety, and configuration.

## Overview

This skill provides a comprehensive checklist for software engineers and AI agents to ensure that CLI tools follow industry-standard conventions. It focuses on usability, safety, and interoperability.

## Supported Environments

- **Runners**: Claude Code, Codex, and other Agent Skills-compatible runners.
- **Operating Systems**: Platform-agnostic (Windows, macOS, Linux).

## Installation

```sh
npx skills add metyatech/skill-cli-design
```

## Usage

### Claude Code

```text
/cli-design
```

### Codex

```text
$cli-design
```

## Development

### Verification

Run the following commands to verify the project:

```sh
# Install markdownlint
npm install -g markdownlint-cli

# Run linting
markdownlint **/*.md --ignore node_modules --ignore AGENTS.md
```

### Rule Composition

This project uses `compose-agentsmd` to manage `AGENTS.md`. To update rules:

```sh
# Generate AGENTS.md
compose-agentsmd --compose
```

## License

MIT
