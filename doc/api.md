# Lua API

lazy.utils API documentation

## mapper

This module can be loaded with `local lazy_utils = require "lazy.utils"`

### get_plugin

```lua
function lazy_utils.get_plugin(plugin: string)
  -> available: LazyPlugin?
```

Get a plugin spec from lazy

_param_ `plugin` — The plugin to search for

_return_ `available` — The found plugin spec from Lazy

### is_available

```lua
function lazy_utils.is_available(plugin: string)
  -> available: boolean
```

Check if a plugin is defined in lazy. Useful with lazy loading when a plugin is not necessarily loaded yet

_param_ `plugin` — The plugin to search for

_return_ `available` — Whether the plugin is available

### load_plugin_with_func

```lua
function lazy_utils.load_plugin_with_func(plugin: string, module: table, funcs: string|string[])
```

A helper function to wrap a module function to require a plugin before running

_param_ `plugin` — The plugin to call `require("lazy").load` with

_param_ `module` — The system module where the functions live (e.g. `vim.ui`)

_param_ `funcs` — The functions to wrap in the given module (e.g. `"ui", "select"`)

### on_load

```lua
function lazy_utils.on_load(plugins: string|string[], load_op: string|fun()|string[])
```

Execute a function when a specified plugin is loaded with Lazy.nvim, or immediately if already loaded

_param_ `plugins` — the name of the plugin or a list of plugins to defer the function execution on. If a list is provided, only one needs to be loaded to execute the provided function

_param_ `load_op` — the function to execute when the plugin is loaded, a plugin name to load, or a list of plugin names to load

### plugin_opts

```lua
function lazy_utils.plugin_opts(plugin: string)
  -> opts: table
```

Resolve the options table for a given plugin with lazy

_param_ `plugin` — The plugin to search for

_return_ `opts` — The plugin options
