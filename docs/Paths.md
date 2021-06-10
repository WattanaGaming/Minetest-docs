# Paths
Minetest have paths for locating games, mods, texture packs, etc. and they vary depending on the operating system you use. This page contain user paths and shared paths(also referred to as `$path_user` and `$path_share` respectively) that Minetest can use depending on how you start it.

* `RUN_IN_PLACE=1` (Windows release, local build)
    * `$path_user`: `<build directory>`[^1]
    * `$path_share`: `<build directory>`[^1]
* `RUN_IN_PLACE=0`: (Linux release)
    * `$path_share`:
        * Linux: `/usr/share/minetest`
        * Windows: `<install directory>/minetest-x.x.x`
    * `$path_user`:
        * Linux: `$HOME/.minetest`
        * Windows: `C:/users/<user>/AppData/minetest` (maybe)

!!! warning
    According to a user on the Minetest Discord server, the information on this page may be outdated or wrong.
    ??? quote
        RUN_IN_PLACE=0 is also not a Linux thing, it's a Linux AND system-wide install thing
    ??? quote
        it's just that the documentation documents the way the developers imagine users would use their software, not the way users actually do.  Those of us who self-compile for example, probably find it easier to just RUN_IN_PLACE out of ~/.minetest/bin/ instead of going through the whole systemwide install rigamarole.
!!! todo
    Confirm paths and update the list.


[^1]: If you downloaded Minetest for Windows, `<build directory>` refers to the directory that Minetest comes in. For example, `minetest-5.4.1-win64`
