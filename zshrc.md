# Configuration

```shell script
sudo chmod go-w /opt/homebrew/share/zsh/site-functions && sudo chmod go-w /opt/homebrew/share && vim ~/.zshrc
```

```shell
### initialize external tools
eval "$(starship init zsh)"
eval "$(zoxide init zsh)"

### history
if [ -z "$HISTFILE" ]; then
  HISTFILE="$HOME/.zsh_history"
fi
SAVEHIST=20000
HISTSIZE=29999                   # set HISTSIZE > SAVEHIST
setopt EXTENDED_HISTORY         # include timestamp
setopt HIST_BEEP                # beep if attempting to access a history entry which isn’t there
setopt HIST_EXPIRE_DUPS_FIRST   # trim dupes first if history is full
setopt HIST_FIND_NO_DUPS        # do not display previously found command
setopt HIST_IGNORE_DUPS         # do not save duplicate of prior command
setopt HIST_IGNORE_SPACE        # do not save if line starts with space
setopt HIST_REDUCE_BLANKS       # strip superfluous blanks
setopt INC_APPEND_HISTORY       # don’t wait for shell to exit to save history lines


if type brew &>/dev/null; then
    FPATH=$(brew --prefix)/share/zsh-completions:$FPATH

    autoload -Uz compinit
    compinit
fi

### aliases
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
alias ssv='cd $HOME/solidsoft/vault-solidsoft/ && git add . && git commit -m "Work with repository" && git push && cd $HOME && clear'
alias prv='cd $HOME/vault-personal/ && git add . && git commit -m "." && git push && cd $HOME && clear'

### functions
pubhl() {
  read 'target?user@host: ' && ssh-add -L | grep homelab | ssh "$target" 'mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >> ~/.ssh/authorized_keys'
}
pubss() {
  read 'target?user@host: ' && ssh-add -L | grep 'ivan.lobanov@solidsoft$' | ssh "$target" 'mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >> ~/.ssh/authorized_keys'
}
```

```shell
source $HOME/.zshrc && touch .hushlogin
```
