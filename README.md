# macos-new-setup

## Setup Brew and zsh

#### Brew

```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

```shell
touch /Users/$USER/.zprofile && echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/$USER/.zprofile && eval "$(/opt/homebrew/bin/brew shellenv)"
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

#### .zshrc

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
alias glog='git log --oneline --graph' # Visual, compact git log
alias cle='clear'
alias bat='bat --theme=TwoDark '
```

## Software installation

#### Cask

```shell
brew install --cask bitwarden --cask brave-browser --cask ghostty --cask telegram-desktop --cask obsidian --cask thunderbird --cask visual-studio-code --cask iina 
```

#### Terminal

```shell
brew install starship eza bat duf gnu-tar zoxide neovim btop  
```
