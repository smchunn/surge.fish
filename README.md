# surge.fish

> Customizable prompt with async Git status for [Fish](https://fishshell.com).

## Inspiration

`surge` is inspired by and uses code from [hydro](https://github.com/jorgebucaran/hydro), an ultra-pure, lag-free Fish prompt. We extend gratitude to the `hydro` project for its foundational contributions.

## Installation

Install with [Fisher](https://github.com/jorgebucaran/fisher):

```console
fisher install smchunn/surge.fish
```

## Features

A sleek, single prompt symbol to guide your workflow. [Customize it](#configuration)?

```
❯
```

Display Git branch name and status with asynchronous prompt repaints!

```
surge.fish • main
```

Track commits ahead or behind your upstream with async updates!

```
surge.fish • main 1↑1↓
```

Show [`$CMD_DURATION`](https://fishshell.com/docs/current/language.html?highlight=cmd_duration#envvar-CMD_DURATION) for commands taking longer than `1` second. [Configurable](#configuration).

```
8.1s ❯
```

Highlight the last non-zero [exit status](https://fishshell.com/docs/current/tutorial.html#exit-status) from [`$pipestatus`](https://fishshell.com/docs/current/language.html?highlight=cmd_duration#envvar-pipestatus).

```
❯ false
1❯ false | false
1 1❯
```

<!-- Smart [`$PWD`](https://fishshell.com/docs/current/language.html?highlight=cmd_duration#envvar-PWD) truncation, showing the basename or Git repository root. -->
<!---->
<!-- ``` -->
<!---->
<!-- ``` -->

<!-- ## Performance -->
<!---->
<!-- ``` -->
<!---->
<!-- ``` -->

## Configuration

Set variables using `set --universal` from the command line or `set --global` in your `config.fish`.

### Symbols

| Variable                  | Type   | Description                | Default |
| ------------------------- | ------ | -------------------------- | ------- |
| `surge_symbol_prompt`     | string | Prompt symbol.             | `❯`     |
| `surge_symbol_git_branch` | string | Git branch symbol.         | `•`     |
| `surge_symbol_git_ahead`  | string | Ahead of upstream symbol.  | `↑`     |
| `surge_symbol_git_behind` | string | Behind of upstream symbol. | `↓`     |

### Colors

> Any argument accepted by [`set_color`](https://fishshell.com/docs/current/cmds/set_color.html).

| Variable                       | Type  | Description                    | Default            |
| ------------------------------ | ----- | ------------------------------ | ------------------ |
| `surge_color_pwd`              | color | Color of the PWD segment.      | `magenta`          |
| `surge_color_git`              | color | Color of the Git segment.      | `blue`             |
| `surge_color_git_branch`       | color | Color of the Git branch.       | `$surge_color_pwd` |
| `surge_color_git_branch_clean` | color | Color of a clean Git branch.   | `brgreen`          |
| `surge_color_git_branch_dirty` | color | Color of a dirty Git branch.   | `brred`            |
| `surge_color_git_ahead`        | color | Color of ahead indicator.      | `brblue`           |
| `surge_color_git_behind`       | color | Color of behind indicator.     | `green`            |
| `surge_color_error`            | color | Color of the error segment.    | `red`              |
| `surge_color_prompt`           | color | Color of the prompt symbol.    | `blue`             |
| `surge_color_duration`         | color | Color of the duration segment. | `yellow`           |

### Flags

| Variable          | Type    | Description                         | Default |
| ----------------- | ------- | ----------------------------------- | ------- |
| `surge_fetch`     | boolean | Fetch Git remote in the background. | `false` |
| `surge_multiline` | boolean | Display prompt on a separate line.  | `false` |

### Misc

| Variable                       | Type    | Description                                        | Default |
| ------------------------------ | ------- | -------------------------------------------------- | ------- |
| `surge_ignored_git_paths`      | strings | Space-separated list of paths to exclude Git info. | `""`    |
| `surge_cmd_duration_threshold` | numeric | Minimum command duration (ms) to display.          | `1000`  |

## License

[MIT License](LICENSE) © [smchunn]

[MIT License](https://github.com/jorgebucaran/hydro/blob/main/LICENSE.md) © [Jorge Bucaran]
