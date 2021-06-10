# Paths
Minetest have paths for locating games, mods, texture packs, etc. and they vary depending on the operating system you use. This page contain user paths and shared paths(also referred to as `$path_user` and `$path_share` respectively) that Minetest can use depending on how you start it.

* `RUN_IN_PLACE=1` (default for Windows release and local build)
    * `$path_user`: `<build directory>`[^1][^2]
    * `$path_share`: `<build directory>`[^1][^2]
* `RUN_IN_PLACE=0`: (default for system-wide installation on Linux)
    * `$path_share`:
        * Linux: `/usr/share/minetest`
        * Windows: `<install directory>/minetest-x.x.x`
    * `$path_user`:
        * Linux: `$HOME/.minetest`
        * Windows: `C:/users/<user>/AppData/minetest` (maybe)

!!! todo
    Confirm user path for `RUN_IN_PLACE=0` on Windows.

[^1]: If you downloaded Minetest for Windows, `<build directory>` refers to the directory that Minetest comes in. For example, `minetest-5.4.1-win64`.
[^2]: If you build Minetest manually, `<build directory>` is the directory you called CMake from. This will usually be the top level project directory.
