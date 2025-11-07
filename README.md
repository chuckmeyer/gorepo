# gorepo

Quickly navigate to GitHub repositories with fuzzy matching and fzf-powered tab completion for zsh.

## Features

- **Interactive fuzzy finder** - Browse and select repos with arrow keys using fzf
- **Tab completion** - Press Tab to trigger interactive selection
- **Exact match detection** - Instantly navigate when repo name matches exactly
- **Pattern filtering** - Pre-filter results by typing partial repo names
- **Fast caching** - Repository list cached for instant performance
- **Oh My Zsh plugin** - Seamless integration with Oh My Zsh

## Requirements

- [zsh](https://www.zsh.org/) - Z shell
- [Oh My Zsh](https://ohmyz.sh/) - Zsh framework
- [fzf](https://github.com/junegunn/fzf) - Fuzzy finder (required for interactive selection)

### Installing prerequisites

```bash
# Install Oh My Zsh (if not already installed)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Install fzf
# macOS
brew install fzf

# Linux
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```

## Installation

### Oh My Zsh Plugin (Recommended)

1. Clone this repository into your Oh My Zsh custom plugins directory:
```bash
git clone https://github.com/chuckmeyer/gorepo.git ~/.oh-my-zsh/custom/plugins/gorepo
```

2. Add `gorepo` to your plugins in `~/.zshrc`:
```bash
plugins=(git fzf gorepo)
```

3. Reload your shell:
```bash
source ~/.zshrc
```

### Standalone Installation (Alternative)

If you're not using Oh My Zsh:

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

By default, `gorepo` looks for repositories in `~/Documents/GitHub`. To change this:

**For Oh My Zsh plugin users:**
Edit the `GOREPO_DIR` variable in `~/.oh-my-zsh/custom/plugins/gorepo/gorepo.plugin.zsh`:

```bash
typeset -g GOREPO_DIR="$HOME/your/custom/path"
```

**For standalone installation:**
Edit the `GOREPO_DIR` variable in the `gorepo` script:

```bash
typeset -g GOREPO_DIR="$HOME/your/custom/path"
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
