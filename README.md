# XPM to ANS and MUX
Convert 16 color XPM files to ANSI and MU* description.

![Screenshot](https://github.com/oliverbacsi/XPMtoANSandMUX/blob/master/Screenshot.png)

This software is an aid to make MUD/MUSH/MUX games fancy looking by adding not just a simple text description (**@desc**) to each room, but to create an ANSI art from any arbitrary picture and show it as the description of the room so that the users have a graphical presentation of the game scene using only their ANSI-capable terminals.


## How to create an ANSI art using the software:

0. Copy the provided palette file to Your **~/.gimp/palettes/** folder.
1. Pick an arbitrary picture You want to use as the scene of the game room and load it into **GIMP**.
2. Select and crop the picture to the visible area.
3. Resize the image to that many pixels wide as many characters You want to have in the final ANSI art. (78 is safe choice for 80 wide terminals). Also remember that the length of the resulting room @description is proportional with the **sqare** of the picture size! So maybe 40x25 chars is also enough. Feel free to experiment.
4. Make a vertical-only resize so that the width remains the same while the height is compressed to 75%. This is needed because the fonts of the termial are not square but their height is higher than their width. So the ANSI art will look vertically distorted.
5. As Your ANSI art will only have 16 colors, so generally it is a good idea at this point to **raise the contrast brutally**, so that You predefine what pixel will get what color during the conversion. Hint: Raise the contrast to about +60. Or: contrast+50, brightness+20. Make Your experiments.
6. Now convert the picture from RGB color space to Indexed:  *Menu::Image::Mode::Indexed*. Choose *custom palette* and then select the provided **VGA16** palette from the menu.  Uncheck the *Skip unused colors* option.
7. Export the image as XPM file.
8. Now start **XPMtoANSandMUX**.
9. Browse for the XPM file You've just created. This should be a proper 16-color XPM file now with the predefined palette.
10. Enter Your textual description for the MU* room, this will appear right below the ANSI art.
11. Click *OK*, then You are done
12. In the same folder and under the same name as Your XPM file was You'll see two new files: an *.ans* file that contains the image in ANSI format (capable to be cat into the terminal), and the *.muxdesc* file: it has a single text line, You need to copy-paste it into the command line of the MU* game if You are in the room You want to fancy.

-----

## BUGS and Still to do:

- [ ] My first trial was for 128color (16 FG x 8 BG), and a VGA128 palette, put it caused 2 problems:
	1. It was simply ugly. The backround color of the characters made it ugly looking.
	2. The @desc of the MU* room got soooooo long (because of the color codes) that the MU* game could not handle the string, and only half of the ANSI art was displayed.

	So therefore I am back on 16 FG colors.
