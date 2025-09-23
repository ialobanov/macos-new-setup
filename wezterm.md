# Settings

```shell
vim ~/.wezterm.lua
```

```lua
local wezterm = require 'wezterm'
local mux = wezterm.mux
local config = wezterm.config_builder()

-- Maximize on startup
wezterm.on('gui-startup', function(cmd)
  local tab, pane, window = mux.spawn_window(cmd or {})
  window:gui_window():maximize()
end)

-- General
config.font_size = 20 
config.line_height = 1.1
config.font = wezterm.font 'ZedMono Nerd Font Mono'
config.color_scheme = 'rebecca'

-- Hide OS panel and disable confirmation for close terminal
config.window_decorations = "RESIZE"
config.window_close_confirmation = 'NeverPrompt'
config.enable_tab_bar = false

-- Set window paddings
config.window_padding = {
  left = 20,
  right = 20,
  top = 20,
  bottom = 20,
}

-- Keys bindings
config.keys = {
  {
    key = 'w',
    mods = 'CMD',
    action = wezterm.action.CloseCurrentPane {confirm = false},
  },
  {
    key = 'd',
    mods = 'CMD',
    action = wezterm.action.SplitHorizontal { domain = 'CurrentPaneDomain' },
  },
  {
    key = 'd',
    mods = 'CMD|SHIFT',
    action = wezterm.action.SplitVertical { domain = 'CurrentPaneDomain' },
  },
  {
    key = 'k',
    mods = 'CMD',
    action = wezterm.action.SendString 'clear\n',
  }
}

-- Mouse buttons bindings
config.mouse_bindings = {
  {
    event = { Up = { streak = 1, button = 'Right' } },
    mods = 'NONE',
    action = wezterm.action.PasteFrom 'Clipboard',
  }
}

return config
```
