# Mods
Minetest has a scripting API (Application Programming Interface), which is used to program mods (short for "modifications") for the game, extending its features and adding new items. This API is accessed using an easy-to-use programming language called Lua.

## World-specific games
It is possible to include a game in a world; in this case, no mods or games are loaded or checked from anywhere else.

This is useful for e.g. adventure worlds and happens if the `<worldname>/game/` directory exists.

Mods should then be placed in `<worldname>/game/mods/`.

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
- `depends`: A comma separated list of dependencies. These are mods that must be loaded before this mod.
- `optional_depends`: A comma separated list of optional dependencies. Like a dependency, but no error if the mod doesn't exist.

### screenshot.png
A screenshot shown in the mod manager within the main menu. It should have an aspect ratio of 3:2 and a minimum size of 300×200 pixels.

### settingtypes.txt
The format is documented in `builtin/settingtypes.txt`. It is parsed by the main menu settings dialogue to list mod-specific settings in the "Mods" category.

### init.lua
This is the main Lua script of the mod that Minetest executs when loading the said mod. Subsequent execution depends on Minetest calling the registered callbacks.

`minetest.settings` can be used to read custom or existing settings at load time, if necessary.

### models
Models for entities or meshnodes.

### textures, sounds, media
Media files (textures, sounds, etc.) that will be transferred to the client and will be available for use by the mod.

### locale
Translation files for the clients.

### Deprecated files
These are the files that are no longer used or needed in a Minetest mod

#### depends.txt
**Deprecated:** you should use `mod.conf` instead.

This file is used if there are no dependencies in `mod.conf`. It contains a list of mods that have to be loaded before loading this mod. A single line contains a single modname.

Optional dependencies can be defined by appending a question mark to a single modname. This means that if the specified mod is missing, it does not prevent this mod from being loaded.

#### description.txt
**Deprecated:** you should use `mod.conf` instead.

This file is used if there is no description in `mod.conf`. It contains a description to be shown in the Mods tab of the main menu.

## Naming conventions
Registered names should generally be in this format: `modname:<whatever>`<br/>
`<whatever>` can have these characters: `a-zA-Z0-9_`

This is to prevent conflicting names from corrupting maps and is enforced by the mod loader.

Registered names can be overridden by prefixing the name with `:`. This can be used for overriding the registrations of some other mod.

The `:` prefix can also be used for maintaining backwards compatibility.

### Example
In the mod `experimental`, there is the ideal item/node/entity name `tnt`. So the name should be `experimental:tnt`.

Any mod can redefine `experimental:tnt` by using the name `:experimental:tnt` when registering it. That mod is required to have experimental as a dependency.
