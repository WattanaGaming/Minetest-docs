# Games
In Minetest, a game is a collection of configurations, mods, and a few extra files(mostly for main menu images), but packaged together to provide a complete interactive experience, which can be used out-of-the-box. When a player starts a game, all the mods packaged with that game will be used.

Games are looked up from these directories:

* `$path_share/games/<gameid>/`
* `$path_user/games/<gameid>/`

Where `<gameid>` is unique to each game(see [Paths](Lua%20API/introduction.md#paths)).

The game directory can contain the following files:

* `game.conf`, with the following keys:
    * `name`: Required, a human readable title to address the game, e.g. `name = Minetest`.
    * `description`: Short description to be shown in the content tab
    * `allowed_mapgens = <comma-separated mapgens>` e.g. `allowed_mapgens = v5,v6,flat`. Mapgens not in this list are removed from the list of mapgens for the game. If not specified, all mapgens are allowed.
    * `disallowed_mapgens = <comma-separated mapgens>` e.g. `disallowed_mapgens = v5,v6,flat`. These mapgens are removed from the list of mapgens for the game. When both `allowed_mapgens` and `disallowed_mapgens` are specified, `allowed_mapgens` is applied before `disallowed_mapgens`.
    * `disallowed_mapgen_settings= <comma-separated mapgen settings>` e.g. `disallowed_mapgen_settings = mgv5_spflags`. These settings are hidden for this game in the world creation dialog and game start menu.
    * `author`: The author of the game. It only appears when downloaded from ContentDB.
    * `release`: Ignore this: Should only ever be set by ContentDB, as it is an internal ID used to track versions.
* `minetest.conf`: Used to set default settings when running this game.
* `settingtypes.txt`: In the same format as the one in builtin. This settingtypes.txt will be parsed by the menu and the settings will be displayed in the "Games" category in the advanced settings tab.

!!! note
    If the game contains a folder called `textures` the server will load it as a texturepack, overriding mod textures. Any server texturepack will override mod textures and the game texturepack.
