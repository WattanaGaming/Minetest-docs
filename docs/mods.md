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