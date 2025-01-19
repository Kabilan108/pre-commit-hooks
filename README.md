# Pre-commit Hooks

A collection of pre-commit hooks for Python and JavaScript/TypeScript projects using Ruff and Biome.

## Features

- **Ruff Hooks**: Fast Python linting and formatting
  - `ruff`: Linting with automatic fixes
  - `ruff-format`: Code formatting

- **Biome Hooks**: Modern JavaScript/TypeScript toolchain
  - `biome-ci`: CI-focused checks
  - `biome-check`: Code checking
  - `biome-format`: Code formatting
  - `biome-lint`: Linting with automatic fixes

## Installation

1. Install pre-commit:
```bash
uv tool install pre-commit
```

2. Add a `.pre-commit-config.yaml` file to your project:
```yaml
repos:
  - repo: https://github.com/kabilan108/pre-commit-hooks
    rev: v0.0.1  # Use the latest version
    hooks:
      # Python hooks
      - id: ruff
      - id: ruff-format

      # JavaScript/TypeScript hooks
      - id: biome-check
```

3. Install the pre-commit hooks:
```bash
pre-commit install
```

## Configuration

### Ruff Configuration

The Ruff hooks use the configuration file at `config/ruff.toml`. Current settings include:

- Python 3.11 target version
- 88 character line length
- 4-space indentation
- Double quotes for strings
- Common exclusions (`.git`, `node_modules`, etc.)
- Specific ignore rules: `E402`, `F403`

You can override these settings by creating your own `ruff.toml` file in your project.

### Biome Configuration

Biome hooks use the configuration file at `config/biome.json`. The hooks support various file types:
- JavaScript (`.js`, `.cjs`, `.mjs`)
- TypeScript (`.ts`, `.cts`, `.mts`, `.d.ts`)
- JSX/TSX (`.jsx`, `.tsx`)
- JSON/JSONC (`.json`, `.jsonc`)
- CSS (`.css`)
- Svelte (`.svelte`)
- Vue (`.vue`)
- Astro (`.astro`)
- GraphQL (`.graphql`, `.gql`)

## Usage

After installation, the hooks will run automatically on git commit. You can also run them manually:

```bash
# Run all hooks on all files
pre-commit run --all-files

# Run specific hooks
pre-commit run ruff --all-files
pre-commit run biome-format --all-files
```

## Hook Details

### Ruff Hooks

- `ruff`: Runs Ruff linter with --fix option
  - Automatically fixes common issues
  - Uses configuration from `config/ruff.toml`

- `ruff-format`: Runs Ruff formatter
  - Formats Python code according to style rules
  - Consistent with black formatter
  - Uses configuration from `config/ruff.toml`

### Biome Hooks

- `biome-ci`: Runs checks suitable for CI environments
  - No automatic fixes
  - Strict checking for code quality

- `biome-check`: Runs code checks with automatic fixes
  - Combines linting and formatting checks
  - Automatically fixes issues when possible

- `biome-format`: Runs code formatter
  - Formats code according to style rules
  - Handles multiple file types

- `biome-lint`: Runs linter with automatic fixes
  - Checks for code quality issues
  - Automatically fixes common problems

## Requirements

- Python 3.11 or higher
- Node.js (for Biome hooks)
- pre-commit 2.9.2 or higher
