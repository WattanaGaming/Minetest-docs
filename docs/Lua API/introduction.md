# Introduction
Content and functionality can be added to Minetest using Lua scripting in run-time loaded mods.

A mod is a self-contained bunch of scripts, textures and other related things, which is loaded by and interfaces with Minetest.

Mods are contained and ran solely on the server side. Definitions and media files are automatically transferred to the client.

## Programming in Lua
If you have any difficulty in understanding this, please read [Programming in Lua](http://www.lua.org/pil/).

## Startup
Mods are loaded during server startup from the mod load paths by running
the `init.lua` scripts in a shared environment.

## Paths
* `RUN_IN_PLACE=1` (Windows release, local build)
    * `$path_user`: `<build directory>`
    * `$path_share`: `<build directory>`
* `RUN_IN_PLACE=0`: (Linux release)
    * `$path_share`:
        * Linux: `/usr/share/minetest`
        * Windows: `<install directory>/minetest-0.4.x`
    * `$path_user`:
        * Linux: `$HOME/.minetest`
        * Windows: `C:/users/<user>/AppData/minetest` (maybe)

## Mod load path
Paths are relative to the directories listed in the [Paths] section above.

* `games/<gameid>/mods/`
* `mods/`
* `worlds/<worldname>/worldmods/`
