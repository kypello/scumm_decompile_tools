SCUMM Image Encoder
----
V5 or V6

Unpack a LucasArts game with ScummPacker v3 or higher.
Decode a room background to a PNG file. Pass the LFLF directory as one argument, and the name of the output image as another argument. Also pass the SCUMM version number to target. Pass the "-d" option to decode.
Encode a PNG to a room background (will modify existing assets, so you might want to make a backup). Pass the "-e" option to encode.
Pack the game again with ScummPacker.

If the room uses the background's palette to animate objects, you may get some funny colours when you encode the image. Use the option "-f" to freeze the palette, i.e. no changes will be made to the palette. This requires the input image to have the exact same palette/colour table as the original background.
----
V2

Unpack a LucasArts game with ScummRp.
Decode a room background to a PNG file. Similar to V5 or V6. Will look for a folder "ROv2", containing the files "HDv2" and "IMv2"
Encode a PNG to a room background. This requires a "ROv2" folder to exist in the output directory, and will write new "HDv2" and "IMv2" files (replacing any existing files).
Pack the game again with ScummRp.
----
V1

Unpack a LucasArts game with ScummRp.
Unfortunately, ScummRp doesn't extract all the information required (such as the colour palette!), so you need to run "v1col_extract" on the game resources as well. Make sure you extract to the same directory as the ScummRp output.
Decode all images from a room to PNG files. The decoder will spit out the background image, all object images, the background mask and all image masks. Make sure you don't change the file names.
Encode the images. When you encode, just specify the file name of the background image - the encoder will also pick up all of the object images and masks.
You can try to pack the game again with ScummRp - unfortunately, when I tried this, it gave me an error about an invalid offset. As such, it seems you can't actually insert the new graphics back into the game. If it worked, you would also need to run "v1col_insert" to insert the colour palette.

The V1 image format was designed for the Commodore 64, so there are some limitations you should be aware of:
- Images are divided into 8x8 blocks.
- Each pixel is output twice on the x axis - this means you effectively have half the width of your output image (e.g. in a 320x128 image, you will only have 160x128 pixels to work with). 
- There are 3 common colours defined per room, and each 8x8 block can specify its own "custom" colour when it's displayed.
- There is a limit of 256 different 8x8 blocks. This includes the room's background AND all its objects, but not the masks. This is why the objects must be decoded & encoded when the background is decoded/encoded. (Note that a solid block of a "custom" colour could be used multiple times, each time specifying a different "custom" colour, but using the same block data.)
----
This program and its source code is available at <http://www.jestarjokin.net>.

Any enquiries can be sent directly to Laurence at <jestarjokin@jestarjokin.net>.