# gorepo

Quickly navigate to GitHub repositories with fuzzy matching and fzf-powered tab completion for zsh.

## Features

- **Interactive fuzzy finder** - Browse and select repos with arrow keys using fzf
- **Tab completion** - Press Tab to trigger interactive selection
- **Exact match detection** - Instantly navigate when repo name matches exactly
- **Pattern filtering** - Pre-filter results by typing partial repo names

## Requirements

- [zsh](https://www.zsh.org/) - Z shell
- [fzf](https://github.com/junegunn/fzf) - Fuzzy finder (required for interactive selection)

### Installing fzf

```bash
# macOS
brew install fzf

# Linux
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```

## Installation

1. Clone this repository:
```bash
git clone https://github.com/chuckmeyer/gorepo.git ~/gorepo
```

2. Create the `.zfunc` directory if it doesn't exist:
```bash
mkdir -p ~/.zfunc
```

3. Create a symbolic link to the gorepo script:
```bash
ln -s ~/gorepo/gorepo ~/.zfunc/gorepo
```

4. Add to your `~/.zshrc`:
```bash
# Add gorepo to function path
fpath=(~/.zfunc $fpath)
autoload -Uz gorepo
```

5. Reload your shell:
```bash
source ~/.zshrc
```

## Configuration

By default, `gorepo` looks for repositories in `~/Documents/GitHub`. To change this, edit the `GOREPO_DIR` variable at the top of the script:

```bash
# Edit this line in the gorepo script
typeset -g GOREPO_DIR="$HOME/Documents/GitHub"  # Change this to your repo directory
```

## Usage

### Basic navigation

Navigate to a repository with exact name:
```bash
gorepo myrepo
```

If the name matches exactly, you'll be taken directly to that repository. Otherwise, fzf opens with filtered results.

### Interactive selection

Open fzf to browse all repositories:
```bash
gorepo
```

Pre-filter results with a pattern:
```bash
gorepo doc
```

### Tab completion

Type a partial name and press Tab for interactive selection:
```bash
gorepo my<TAB>
```

This opens fzf with "my" pre-filled in the search. Use arrow keys to navigate, Enter to select, or Esc to cancel.

### Special commands

Navigate to the GitHub directory itself:
```bash
gorepo root
```

## How it works

1. Type `gorepo [pattern]` and press Enter or Tab
2. If there's an exact match, navigate directly
3. Otherwise, fzf opens with arrow navigation and highlighting
4. Select a repo and it changes to that directory

Tab completion works for all gorepo commands while preserving normal Tab behavior for other commands.

## License

MIT License - see [LICENSE](LICENSE) file for details.
