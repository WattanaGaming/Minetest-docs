# Mods
Since Minetest by itself is just an engine, most if not all gameplay functionalities have to be implemented in mods.

A mod is a self-contained collection of scripts, textures and other related files, which is loaded by and interfaces with Minetest. They are contained and ran solely on the server side while definitions and media files are automatically transferred to the client.

## Mod load path
These paths are relative to the directories listed in [Paths](paths.md)

* `games/<gameid>/mods/`
* `mods/`
* `worlds/<worldname>/worldmods/`

## Modpacks
Mods can be put in a subdirectory, if the parent directory, which otherwise should be a mod, contains a file named `modpack.conf`. The file is a key-value store of modpack details.

* `name`: The modpack name. Allows Minetest to determine the modpack name even if the folder is wrongly named.
* `description`: Description of mod to be shown in the Mods tab of the main menu.
* `author`: The author of the modpack. It only appears when downloaded from ContentDB.
* `release`: Ignore this: Should only ever be set by ContentDB, as it is an internal ID used to track versions.
* `title`: A human-readable title to address the modpack.

!!! note
    To support 0.4.x, please also create an empty modpack.txt file.

## Mod directory structure
```
mods
├── modname
│   ├── mod.conf
│   ├── screenshot.png
│   ├── settingtypes.txt
│   ├── init.lua
│   ├── models
│   ├── textures
│   │   ├── modname_stuff.png
│   │   ├── modname_stuff_normal.png
│   │   ├── modname_something_else.png
│   │   ├── subfolder_foo
│   │   │   ├── modname_more_stuff.png
│   │   │   └── another_subfolder
│   │   └── bar_subfolder
│   ├── sounds
│   ├── media
│   ├── locale
│   └── <custom data>
└── another
```

### modname
The location of this directory can be fetched by using `minetest.get_modpath(modname)`.

### mod.conf
A `Settings` file that provides meta information about the mod.

* `name`: The mod name. Allows Minetest to determine the mod name even if the folder is wrongly named.
* `description`: Description of mod to be shown in the Mods tab of the main menu.
* `depends`: A comma separated list of dependencies. These are mods that must be loaded before this mod.
* `optional_depends`: A comma separated list of optional dependencies. Like a dependency, but no error if the mod doesn't exist.
* `author`: The author of the mod. It only appears when downloaded from ContentDB.
* `release`: Ignore this: Should only ever be set by ContentDB, as it is an internal ID used to track versions.
* `title`: A human-readable title to address the mod.

!!! note
    To support 0.4.x, please also provide depends.txt.

### `screenshot.png`
A screenshot shown in the mod manager within the main menu. It should have an aspect ratio of 3:2 and a minimum size of 300×200 pixels.

### `depends.txt`
This file is used if there are no dependencies in mod.conf.

List of mods that have to be loaded before loading this mod.

A single line contains a single modname.

Optional dependencies can be defined by appending a question mark to a single modname. This means that if the specified mod is missing, it does not prevent this mod from being loaded.

!!! warning
    **Deprecated:** you should use mod.conf instead.

### `description.txt`
This file is used if there is no description in mod.conf.

A file containing a description to be shown in the Mods tab of the main menu.

!!! warning
    **Deprecated:** you should use mod.conf instead.

### `settingtypes.txt`
The format is documented in `builtin/settingtypes.txt`. It is parsed by the main menu settings dialogue to list mod-specific settings in the "Mods" category.

### `init.lua`
The main Lua script. Running this script should register everything it wants to register. Subsequent execution depends on minetest calling the registered callbacks.

!!! tip
    `minetest.settings` can be used to read custom or existing settings at load time, if necessary. (See [Settings](Lua%20API/settings.md))

### `textures`, `sounds`, `media`, `models`, `locale`
Media files (textures, sounds, whatever) that will be transferred to the client and will be available for use by the mod and translation files for the clients (see [Translations]).

It is suggested to use the folders for the purpous they are thought for, eg. put textures into `textures`, translation files into `locale`, models for entities or meshnodes into `models` et cetera.

These folders and subfolders can contain subfolders. Subfolders with names starting with `_` or `.` are ignored. If a subfolder contains a media file with the same name as a media file in one of its parents, the parent's file is used.

Although it is discouraged, a mod can overwrite a media file of any mod that it depends on by supplying a file with an equal name.

## Naming conventions
Registered names should generally be in this format:

    modname:<whatever>

`<whatever>` can have these characters:

    a-zA-Z0-9_

This is to prevent conflicting names from corrupting maps and is enforced by the mod loader.

Registered names can be overridden by prefixing the name with `:`. This can be used for overriding the registrations of some other mod.

The `:` prefix can also be used for maintaining backwards compatibility.

!!! example
    In the mod `experimental`, there is the ideal item/node/entity name `tnt`. So the name should be `experimental:tnt`.

    Any mod can redefine `experimental:tnt` by using the name

        :experimental:tnt

    when registering it. That mod is required to have `experimental` as a dependency.
