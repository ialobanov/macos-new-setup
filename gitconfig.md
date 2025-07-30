# Configuration

```shell
vim $HOME/.gitconfig
```

```properties
[user]
    name = ialobanov
    email = ivan.a.lobanov@gmail.com

[core]
    autocrlf = input
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
    autocrlf = input
    editor = nvim
```