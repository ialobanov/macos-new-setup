# macos-new-setup

## Hostname

```shell
sudo scutil --set ComputerName MACMINI
```

```shell
sudo scutil --set HostName MACMINI
```

## Software installation

## Setup Brew

#### Brew

```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### .zprofile

```shell
vim ~/.zprofile
```

```shell
## initialize homebrew environment (for Apple Silicon)
eval "$(/opt/homebrew/bin/brew shellenv)"

## set up ssh agent for Bitwarden
export SSH_AUTH_SOCK=/Users/$USER/.bitwarden-ssh-agent.sock
```

```shell
eval "$(/opt/homebrew/bin/brew shellenv)"
```

#### Terminal apps

```shell
brew install --quiet starship eza bat duf gnu-tar zoxide neovim btop
```

#### Cask apps

```shell
brew install --quiet --cask bitwarden --cask brave-browser --cask ghostty --cask telegram-desktop --cask obsidian --cask thunderbird --cask visual-studio-code --cask iina --cask anydesk --cask stats --cask qbittorrent
```

## Setup zsh

```shell
sudo chmod go-w /opt/homebrew/share/zsh/site-functions && sudo chmod go-w /opt/homebrew/share && vim ~/.zshrc
```

```shell
## initialize external tools
eval "$(starship init zsh)"
eval "$(zoxide init zsh)"

# shell history settings
HISTFILE=~/.zsh_history
HISTSIZE=10000
SAVEHIST=10000
setopt SHARE_HISTORY
setopt HIST_IGNORE_DUPS

if type brew &>/dev/null; then
    FPATH=$(brew --prefix)/share/zsh-completions:$FPATH

    autoload -Uz compinit
    compinit
fi

## aliases
alias vim='nvim'
alias sudo='sudo '
alias sp='sudo poweroff'
alias sr='sudo reboot'
alias ll='eza -laF --smart-group --icons=always'
alias sv='sudo vim '
alias g='git '
alias gst='git status'
alias gll='git pull && clear'
alias gsh='git add . && git commit -m "." && git push && clear'
alias cle='clear'
alias bat='bat --theme=TwoDark '
```





