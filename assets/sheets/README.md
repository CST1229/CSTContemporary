# Sprite sheets

This folder is used for sprite sheets, also allowing for animation using SpriteSheetDef.

## How to make one

Add a .aseprite file to this folder and export it using the following settings:

[_aseprite_settings.png](./_aseprite_settings.png)

Then, add your sheet name to the `assets` variable, defining the path to the json and png files (which MUST have the same name aside from the file extension):
```diff
 	const assets = {
+		player: {sheet: "sheets/player"},
 		errortile: 0,
 		tile0: 0,
 		peterplatform: 0,
 	};
```

Afterwards, you can access the sheet using e.g `assets.player`, as a `SpriteSheetDef` object (see its class definition). All tags will be added to it, alongside a tag with an empty name `""` which contains all frames in the sprite. From the tag objects you can access the actual frames of sprites as `SpriteDef`s, for use with the `drawSprite` function.

## Custom data

You can add custom data to each frame using Aseprite custom data.

First, create a layer in your sheet with a name `data:DATANAME` (where `DATANAME` is the name of your data variable). If you want to set a type or default value for it, add user data to the *layer* with the value `type` or `type=defaultValue`. Valid types are `number`, `string` or `boolean`.

Afterwards, simply add cels to the layer that have user data. Do note however, that you will have to draw something on the layers to be able to add user data to it. Therefore, you might also want to set the layer's opacity to 0 so it isn't visible but is still exported (as making the layer actually invisible will cause it to not be exported).

This data is then added to the `SpriteDef` objects, as keys and values in th e`data` property.