# Configuration

NativeLogi stores settings in a TOML file. The internal config path still uses
the inherited `openlogi` name during the first migration phase:

- macOS and Linux: `$XDG_CONFIG_HOME/openlogi/config.toml`
- Default: `~/.config/openlogi/config.toml`

Per-device settings are keyed by the HID++ device identifier.

```toml
schema_version = 1
selected_device = "2b042"

[app_settings]
launch_at_login = true

[devices.2b042]
dpi_presets = [800, 1600, 3200]

[devices.2b042.button_bindings]
Back = "BrowserBack"
Forward = "BrowserForward"

[devices.2b042.per_app_bindings."com.microsoft.VSCode"]
Back = "Undo"
```

Mouse side buttons left on the default Back / Forward bindings are passed
through as native Mouse4 / Mouse5 events on macOS.
