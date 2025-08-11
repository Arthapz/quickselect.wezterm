# Quick Select

A [WezTerm plugin](https://wezterm.org/config/plugins.html) to [jump to the build error](https://quantonganh.com/2023/07/21/jump-to-build-error-helix.md) by opening them in [Helix](https://helix-editor.com/).

## Installation

Add the following to your `~/.wezterm.lua`:

```lua
local quickselect_plugin = wezterm.plugin.require 'https://github.com/quantonganh/quickselect.wezterm'
quickselect_plugin.apply_to_config(config)
```

## Configuration

If you are using `config.keys = { ... }` in your config, make sure to change it to something like this:

```lua
local my_keys = {
    ...
}

for _, keymap in ipairs(my_keys) do
    table.insert(config.keys, keymap)
end
```

This ensures that the plugin's key bindings are not overwritten.

The following extensions are currently supported:

```lua
    local text_extensions = opts.text_extensions or {
        md = true,
        c = true,
        go = true,
        scm = true,
        rkt = true,
        rs = true,
        java = true,
    }
    local patterns = opts.patterns or {
        'https?://\\S+',
        '^/[^/\r\n]+(?:/[^/\r\n]+)*:\\d+:\\d+',
        '[^\\s]+\\.rs:\\d+:\\d+',
        'rustc --explain E\\d+',
        '[^\\s]+\\.go:\\d+',
        '[^\\s]+\\.go:\\d+:\\d+',
        '[^\\s]+\\.java:\\[\\d+,\\d+\\]',
        '[^{]*{.*}',
    }
```

You can adjust these to match your preferred languages and/or patterns.
