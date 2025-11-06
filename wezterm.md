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
config.font_size = 22
config.line_height = 1.1
config.font = wezterm.font 'ZedMono Nerd Font Mono'
config.color_scheme = 'rebecca'
config.color_schemes = {
  ['rebecca'] = {
    ansi = {
     "#12131e",
     "#dd7755",
     "#04dbb5",
     "#f7c20f",
     "#7aa5ff",
     "#bf9cf9",
     "#56d3c2",
     "#e4e3e9",
     },
     background = "#292a44",
     brights = {
      "#666699",
      "#ff92cd",
      "#01eac0",
      "#f7c20f",
      "#69c0fa",
      "#c17ff8",
      "#8bfde1",
      "#f4f2f9",
     },
     cursor_bg = "#D155B1",
     cursor_border = "#D155B1",
     cursor_fg = "#292a44",
     foreground = "#e8e6ed",
     indexed = {},
     selection_bg = "#663399",
     selection_fg = "#f4f2f9",
     scrollbar_thumb = 'FFC300',
    },
}

-- Hide OS panel and disable confirmation for close terminal
config.window_decorations = "RESIZE"
config.window_close_confirmation = 'NeverPrompt'
config.enable_tab_bar = false

-- Set window paddings
config.window_padding = {
  left = 30,
  right = 30,
  top = 30,
  bottom = 30,
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
