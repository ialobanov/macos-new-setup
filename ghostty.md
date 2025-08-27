# Configuration

```shell
mkdir -p $HOME/.config/ghostty && vim $HOME/.config/ghostty/config
```

```properties
# general settings
term = xterm-ghostty
theme = Whimsy
shell-integration = zsh
window-save-state = always

# font management
font-family = "JetBrainsMono Nerd Font Mono"
font-size = 18

# appearance
window-padding-x = 20
window-vsync = true
adjust-cursor-thickness = 23
cursor-color = "#FFC300"
cursor-style-blink = true
macos-titlebar-style = tabs
## opacity
# background-opacity = 0.96
# background-blur-radius = 20

# working directory
window-inherit-working-directory = false
working-directory = "home"
```
