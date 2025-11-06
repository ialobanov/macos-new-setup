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
sudo scutil --set ComputerName macmini-m4
sudo scutil --set HostName macmini-m4
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
brew install --quiet --cask bitwarden --cask brave-browser --cask ghostty --cask telegram-desktop --cask obsidian --cask thunderbird --cask visual-studio-code --cask font-zed-mono-nerd-font
```

```shell
brew install --quiet --cask iina --cask anydesk --cask stats --cask qbittorrent --cask tunnelblick --cask shottr --cask postman
```

Logout.

## Zsh

[configuration](./zshrc.md)

## Git

[configuration](./gitconfig.md)

## Neovim

```shell
mkdir -p $HOME/.config/nvim && git clone https://github.com/ialobanov/nvim-plain.git $HOME/.config/nvim
```

## Obsidian vaults

```shell
mkdir $HOME/vault-personal && mkdir -p $HOME/solidsoft/vault-solidsoft
```

```shell
git clone git@github.com:ialobanov/obsidian-vault.git $HOME/vault-personal
```

## Starship

[configuration](./starship.md)

## Wezterm

[configuration](./wezterm.md)

## Ghostty

[configuration](./ghostty.md)

## Zed

[configuration](./zed.md)

## VSCode

[configuration](./vscode.md)
