# Settings
An interface to read config files in the format of `minetest.conf`.

It can be created via `Settings(filename)`.

### Methods
* `get(key)`: returns a value
* `get_bool(key, [default])`: returns a boolean
    * `default` is the value returned if `key` is not found.
    * Returns `nil` if `key` is not found and `default` not specified.
* `get_np_group(key)`: returns a NoiseParams table
* `get_flags(key)`:
    * Returns `{flag = true/false, ...}` according to the set flags.
    * Is currently limited to mapgen flags `mg_flags` and mapgen-specific flags like `mgv5_spflags`.
* `set(key, value)`
    * Setting names can't contain whitespace or any of `="{}#`.
    * Setting values can't contain the sequence `\n"""`.
    * Setting names starting with "secure." can't be set on the main settings object (`minetest.settings`).
* `set_bool(key, value)`
    * See documentation for set() above.
* `set_np_group(key, value)`
    * `value` is a NoiseParams table.
    * Also, see documentation for set() above.
* `remove(key)`: returns a boolean (`true` for success)
* `get_names()`: returns `{key1,...}`
* `write()`: returns a boolean (`true` for success)
    * Writes changes to file.
* `to_table()`: returns `{[key1]=value1,...}`

### Format
The settings have the format `key = value`. Example:
```conf
foo = example text
bar = """
Multiline
value
"""
```
