# Configuration

```jsonc
// Zed settings
//
// For information on how to configure Zed, see the Zed
// documentation: https://zed.dev/docs/configuring-zed
//
// To see all of Zed's default settings without changing your
// custom settings, run `zed: open default settings` from the
// command palette (cmd-shift-p / ctrl-shift-p)
{
  "agent": {
    "default_model": {
      "provider": "google",
      "model": "gemini-2.5-pro"
    },
    "play_sound_when_agent_done": true
  },
  "show_edit_predictions": false,
  "ui_font_size": 16,
  "buffer_font_size": 16,
  "buffer_font_family": "Hack Nerd Font Propo",
  "format_on_save": "off",
  "theme": {
    "mode": "system",
    "light": "One Light",
    "dark": "One Dark"
  },
  "file_types": {
    "SSH Config": ["ssh_config*"],
    "Nginx": ["**/solidwall-nginx/**/*"]
  }
}
```
