# Texture packs
Texture packs allow you to replace textures provided by a mod with your own textures.

## Directory structure
```
textures
|-- Texture Pack
|   |-- texture_pack.conf
|   |-- screenshot.png
|   |-- description.txt
|   |-- override.txt
|   |-- your_texture_1.png
|   |-- your_texture_2.png
`-- Another Texture Pack
```
!!! info "TODO"
    Document `override.txt`.

### Texture Pack
This is a directory containing the entire contents of a single texture pack. It can be chosen more or less freely and will also become the name of the texture pack. The name must not be “base”.

### `texture_pack.conf`
A key-value config file with the following keys:

* `title` - human readable title
* `description` - short description, shown in the content tab

### `description.txt`
A file containing a short description of the texture pack to be shown in the content tab.

!!! warning
    **Deprecated**, you should use texture_pack.conf instead.

### `screenshot.png`
A preview image showing an in-game screenshot of this texture pack; it will be shown in the texture packs tab. It should have an aspect ratio of 3:2 and a minimum size of 300×200 pixels.

### `your_texture_1.png`, `your_texture_2.png`, etc.
Any other PNG files will be interpreted as textures. They must have the same names as the textures they are supposed to override. For example, to override the apple texture of Minetest Game, add a PNG file named `default_apple.png`.

!!! note
    The custom textures do not necceessarily require the same size as their originals, but this might be required for a few particular textures. When unsure, just test your texture pack in-game.
