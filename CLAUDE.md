# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

surge.fish is a customizable Fish shell prompt with asynchronous Git status display. It's inspired by the hydro prompt and provides:
- Sleek, single-symbol prompts
- Asynchronous Git branch and status information
- Command duration display
- Exit status highlighting
- Extensive customization options

## Architecture

The prompt system consists of three main files:

- `conf.d/surge.fish`: Core configuration and functions that set up the prompt system
- `functions/fish_prompt.fish`: Simple wrapper that calls `surge_prompt`
- `functions/fish_right_prompt.fish`: Simple wrapper that calls `surge_git`

### Key Components

**Event-driven Architecture**: The prompt uses Fish's event system extensively:
- `__surge_pwd`: Triggered on PWD changes to update current directory display
- `__surge_postexec`: Triggered after command execution to handle status and duration
- `__surge_prompt`: Triggered on prompt display to update Git information
- Color functions: Auto-update when color variables change

**Asynchronous Git Updates**: Git status is fetched in background Fish processes to prevent blocking the prompt. The system uses:
- Universal variables (`$_surge_git`) for cross-session state
- Process management to kill old background jobs
- Separate fetch operations when `surge_fetch` is enabled

**Configuration System**: All customization is handled through global Fish variables with sensible defaults:
- Colors: `surge_color_*` variables
- Symbols: `surge_symbol_*` variables
- Behavior: `surge_multiline`, `surge_fetch`, `surge_cmd_duration_threshold`
- Exclusions: `surge_ignored_git_paths`

## Development Commands

This is a Fish shell plugin, so development primarily involves:

```bash
# Install the plugin locally for testing
fisher install .

# Test changes by reloading Fish configuration
source conf.d/surge.fish

# Uninstall for clean testing
fisher remove surge
```

## Git Workflow

This project follows Conventional Commits specification (https://www.conventionalcommits.org/en/v1.0.0/).

### Commit Message Format

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Commit Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `perf`: Performance improvements
- `test`: Adding or updating tests
- `build`: Build system or dependency changes
- `ci`: CI configuration changes
- `chore`: Other changes that don't modify src or test files

### Examples

```
feat: add multiline prompt support
fix: resolve async git status race condition
docs: update configuration examples in README
refactor: simplify color variable handling
```

### Automated Commits

When Claude Code creates commits automatically, they include the `[AUTO]` prefix and footer indicators:

```
[AUTO] feat: add new configuration option

Generated with Claude Code (claude.ai/code)

Co-Authored-By: Claude <noreply@anthropic.com>
```

## Testing

Test the prompt by navigating to different directories and Git repositories:
- Clean/dirty Git repos to verify status display
- Repos with upstream tracking to test ahead/behind indicators
- Long-running commands to verify duration display
- Failed commands to verify exit status display
- Different directory structures to verify PWD truncation