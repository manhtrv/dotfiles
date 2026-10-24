# Dotfiles installation

These configs are organized by tool. The repository does not install packages or manage secrets.

## Install

Back up any existing target before replacing it. The commands below use GNU Stow and create symlinks from `~/dotfiles` into your home directory:

```sh
brew install stow
cd ~/dotfiles
stow --target="$HOME" zsh fish tmux git
```

Stow reports conflicts rather than overwriting existing files. Resolve conflicts by moving or backing up the existing file, then rerun the command. To preview changes first:

```sh
stow --no --verbose --target="$HOME" zsh fish tmux git
```

To remove the symlinks later:

```sh
cd ~/dotfiles
stow --delete --target="$HOME" zsh fish tmux git
```

## Before publishing

- Review `git/.gitconfig`; it contains a Git name and email.
- Check shell paths and tool-specific assumptions for each machine.
- Do not add credentials, tokens, private keys, or generated state to this repository.

## Current machine-specific assumptions

- Zsh expects Homebrew at `/opt/homebrew`.
- Fish and Zsh add user-installed tool directories, including `~/.local/bin`, to `PATH`; the local `omp` binary is expected there.
- tmux clipboard bindings use macOS `pbcopy`; TPM is expected at `~/.tmux/plugins/tpm/tpm`.

Review and adjust these assumptions before deploying on another machine.
