# macos-new-setup

## Sudo without password

```bash
sudo tee /etc/sudoers.d/$USER <<EOF
$USER ALL=(ALL) NOPASSWD: ALL
EOF
sudo chmod 0440 /etc/sudoers.d/$USER
```

## Hostname

```shell
sudo scutil --set ComputerName MACMINI
```

```shell
sudo scutil --set HostName MACMINI
```

## Software installation

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
brew install --quiet starship eza bat duf gnu-tar zoxide neovim btop ansible ansible-lint
```

#### Cask apps

```shell
brew install --quiet --cask bitwarden --cask brave-browser --cask ghostty --cask telegram-desktop --cask obsidian --cask thunderbird --cask visual-studio-code --cask iina --cask anydesk --cask stats --cask qbittorrent --cask tunnelblick --cask shottr --cask bruno --cask zed
```

## Setup zsh

```shell
sudo chmod go-w /opt/homebrew/share/zsh/site-functions && sudo chmod go-w /opt/homebrew/share && vim $HOME/.zshrc
```

```shell
## initialize external tools
eval "$(starship init zsh)"
eval "$(zoxide init zsh)"

## history
SAVEHIST=9000
HISTSIZE=9999                   # set HISTSIZE > SAVEHIST
setopt EXTENDED_HISTORY         # include timestamp
setopt HIST_BEEP                # beep if attempting to access a history entry which isn’t there
setopt HIST_EXPIRE_DUPS_FIRST   # trim dupes first if history is full
setopt HIST_FIND_NO_DUPS        # do not display previously found command
setopt HIST_IGNORE_DUPS         # do not save duplicate of prior command
setopt HIST_IGNORE_SPACE        # do not save if line starts with space
setopt HIST_NO_STORE            # do not save history commands
setopt HIST_REDUCE_BLANKS       # strip superfluous blanks
setopt INC_APPEND_HISTORY       # don’t wait for shell to exit to save history lines

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

```shell
source $HOME/.zshrc && touch .hushlogin
```

## Git

```shell
vim $HOME/.gitconfig
```

```properties
[user]
    name = ialobanov
    email = ivan.a.lobanov@gmail.com

[core]
    autocrlf = input # unix
    editor = nvim

[alias]
    che = checkout
    cm = commit
    br = branch
    lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
    last = log -1 HEAD

[init]
    defaultBranch = main

[pull]
    rebase = true

[fetch]
    prune = true

[includeIf "gitdir:/Users/ivan/solidsoft/"]
    path = /Users/ivan/.gitconfig-work
```

```shell
git config --list --global
```

#### Work

```shell
vim /Users/ivan/.gitconfig-work
```

```properties
[user]
    name = Ivan Lobanov
    email = ivan.lobanov@solidlab.ru

[core]
    autocrlf = input # unix
    editor = nvim
```

#### Obsidian vault

```shell
mkdir $HOME/personal-vault
```
``
```shell
git clone git@github.com:ialobanov/obsidian-vault.git $HOME/vault-prsnl
```
