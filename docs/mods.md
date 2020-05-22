# Mods
Minetest has a scripting API (Application Programming Interface), which is used to program mods (short for "modifications") for the game, extending its features and adding new items. This API is accessed using an easy-to-use programming language called Lua.

## Modpacks
Mods can be put into a subdirectory, provided that the parent directory, which would otherwise be a mod, contains a file named `modpack.conf`. This file is a key-value store of modpack details.

- `name`: The modpack name.
- `Description`: Description of mod to be shown in the Mods tab of the main menu.

## Mod directory structure
```
mods
├── modname
│   ├── mod.conf
│   ├── screenshot.png
│   ├── settingtypes.txt
│   ├── init.lua
│   ├── models
│   ├── textures
│   │   ├── modname_stuff.png
│   │   └── modname_something_else.png
│   ├── sounds
│   ├── media
│   ├── locale
│   └── <custom data>
└── another
```

### modname
The location of this directory can be fetched by using `minetest.get_modpath(modname)`.

### mod.conf
A settings file that provides information about the mod.

- `name`: The mod name. Allows Minetest to determine the mod name even if the directory is wrongly named.
- `description`: Description of the mod to be shown in the Mods tab of the main menu.
- `depends`: A comma separated list of dependencies. These are mods that must be loaded before this mod
- `optional_depends`: A comma separated list of optional dependencies. Like a dependency, but no error if the mod doesn't exist.

### screenshot.png
A screenshot shown in the mod manager within the main menu. It should have an aspect ratio of 3:2 and a minimum size of 300×200 pixels.

### depends.txt (deprecated)
**Deprecated:** you should use `mod.conf` instead.

This file is used if there are no dependencies in `mod.conf`. It contains a list of mods that have to be loaded before loading this mod.

A single line contains a single modname.

Optional dependencies can be defined by appending a question mark to a single modname. This means that if the specified mod is missing, it does not prevent this mod from being loaded.

### description.txt (deprecated)
**Deprecated:** you should use `mod.conf` instead.

This file is used if there is no description in `mod.conf`. It contains a description to be shown in the Mods tab of the main menu.

### settingtypes.txt
The format is documented in builtin/settingtypes.txt. It is parsed by the main menu settings dialogue to list mod-specific settings in the "Mods" category.
