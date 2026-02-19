# macos-new-setup

## Sudo without password

```shell
sudo tee /etc/sudoers.d/$USER <<EOF
$USER ALL=(ALL) NOPASSWD: ALL
EOF
sudo chmod 0440 /etc/sudoers.d/$USER
sudo visudo -c
```

## Hostname

```shell
sudo scutil --set ComputerName Macmini-m4
sudo scutil --set HostName Macmini-m4
```

## Software installation

#### Brew

```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### zprofile

```shell
{ unsetopt HIST_SAVE; tee -a $HOME/.zprofile <<EOF
## initialize homebrew environment (for Apple Silicon)
eval "\$(/opt/homebrew/bin/brew shellenv)"

## set up ssh agent for Bitwarden
export SSH_AUTH_SOCK=/Users/$USER/.bitwarden-ssh-agent.sock
EOF
; setopt HIST_SAVE; }
```

Logout or:

```shell
eval "$(/opt/homebrew/bin/brew shellenv)"
```

#### Terminal apps

```shell
brew install --quiet starship eza bat duf gnu-tar zoxide neovim btop ansible ansible-lint
```

#### Cask apps

```shell
brew install --quiet --cask bitwarden --cask telegram-desktop --cask obsidian --cask thunderbird --cask font-zed-mono-nerd-font
```

```shell
brew install --quiet --cask iina --cask stats --cask qbittorrent --cask tunnelblick --cask shottr
```

Logout.
