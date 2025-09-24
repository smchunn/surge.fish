# surge.fish

Customizable prompt with async Git status for [Fish](https://fishshell.com). Inspired by [hydro](https://github.com/jorgebucaran/hydro).

## Installation

```console
fisher install smchunn/surge.fish
```

## Features

- **Prompt symbol**: `❯`
- **Git status**: `surge.fish • main 1↑1↓` (async updates)
- **Command duration**: `8.1s ❯` (configurable threshold)
- **Exit status**: `1❯` (highlights non-zero exits)

## Configuration

Set variables using `set --universal` or `set --global` in your `config.fish`.

### Symbols

| Variable | Description | Default |
|----------|-------------|---------|
| `surge_symbol_prompt` | Prompt symbol | `❯` |
| `surge_symbol_git_branch` | Git branch symbol | `•` |
| `surge_symbol_git_ahead` | Ahead symbol | `↑` |
| `surge_symbol_git_behind` | Behind symbol | `↓` |

### Colors

All colors accept [`set_color`](https://fishshell.com/docs/current/cmds/set_color.html) arguments.

| Variable | Description | Default |
|----------|-------------|---------|
| `surge_color_pwd` | PWD segment | `magenta` |
| `surge_color_git` | Git segment | `blue` |
| `surge_color_git_branch` | Git branch | `$surge_color_pwd` |
| `surge_color_git_branch_clean` | Clean branch | `brgreen` |
| `surge_color_git_branch_dirty` | Dirty branch | `brred` |
| `surge_color_git_ahead` | Ahead indicator | `brblue` |
| `surge_color_git_behind` | Behind indicator | `green` |
| `surge_color_error` | Error segment | `red` |
| `surge_color_prompt` | Prompt symbol | `blue` |
| `surge_color_duration` | Duration segment | `yellow` |

### Behavior

| Variable | Description | Default |
|----------|-------------|---------|
| `surge_fetch` | Fetch Git remote in background | `false` |
| `surge_multiline` | Display prompt on separate line | `false` |
| `surge_ignored_git_paths` | Space-separated paths to exclude Git info | `""` |
| `surge_cmd_duration_threshold` | Minimum duration (ms) to display | `1000` |

## License

[MIT License](LICENSE) © [smchunn]
[MIT License](https://github.com/jorgebucaran/hydro/blob/main/LICENSE.md) © [Jorge Bucaran]