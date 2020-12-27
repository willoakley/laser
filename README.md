The Cubio2Assitant-1.0.5 is the Wiondows 7+ tool for running files through the engraver. it's a bit less user friendly than the app as it lacks previews but it should heve better support for text-based G-code.

# Installation:
The best way to make G-code is with Inkscape and a few plugins.

## Prerequisites:
- Inkscape: https://inkscape.org/
- J Tech Inkscape plugin (for generating G-Code): https://jtechphotonics.com/?page_id=1980
- KM Laser Inkscape plugin (for rasterising solid images into hatched paths): https://github.com/KnoxMakers/KM-Laser

Both plugins are linked to specific versions of Inkscape.

This folder has Inkscape 1.0.1, J Tech 1.1b and KM Laser master::ae610ee (29 Sep 2020) that should all be compatible.

## Instructions
This is a summary of the information found at https://cubiio.com/support/guide/cubiio2-quick-guide/ and http://cubiio.muherz.com/tw/file_convert_text.html

- Install Inkscape
- Run it once to set it up
- Find the extensions location by going to Edit -> Preferences -> System -> User extensions
- Close Inkscape
- Copy the files from the J Tech Zip into the extensions directory
- Copy the files from the /extensions folder in the KM Laser Zip into the extensions directory
- Start Inkscape
  - The plugins should show as 'KM-LASER' and 'Generate Laser Gcode' in the extensions menu

# Engraving
## Making G-Code files
On windows this is probably the easiest way to do this until the windows app recieved antive preview support. Use Inkscape and the plugins to makes files for each layer at full power then use the settings in the application to controll the speed and power for a cut.

When using the KM LASER > HATCH FILL tool on an object, select:
- Hatch spacing (px): 1.0
- Hatch angle (degrees): 0.0
- Crosshatch: ticked
- Connect nearby ends: unticked
- Inset fill from edges: unticked

When using the Generate Laer Gcode > J Tech Photonics Laser Tool, select:
Ensure all your objects in the file have been converted to paths: Path -> Object to Path

- Laser ON Command: M03
- Laser OFF Command: M05
- Travel speed: 600 (use the layer settings in the cubiio assitant to adjust this per run)
- Laser speed: 600 (use the layer settings in the cubiio assitant to adjust this per run)
- Laser power S#: 255 (full power) (use the layer settings in the cubiio assitant to adjust this per run)
- Power-On delay: 0.0
- Passes: 1 (use the layer settings in the cubiio assitant to adjust this per run)
- Add numeric suffix to filename: unticked
- All units: mm

Don't forget to set the save directory and file name!

### Useful tools:
Gcode previewers:
- https://ncviewer.com/
- https://nraynaud.github.io/webgcode/

## Machine start-up:
- Power on the machine
- If the light is breathing green then it has connected to the WiFi. If not, Press the WPS botton on the machine till the flashing changes then press the WPS button on the router it should go green and lock.
- Machine should move to a breathing green state when it's connected and ready
- Run the Cubio2Assitant-1.0.5
- Select the Machine -> Go Home option (Ctrl + Shift + H)
- Run the Machine -> Advance... -> Calibration
- Press the 'Check left down corner' button and see where the laser ends up
  - If miscalibrated try X:3.0, Y:-2.0
  - Run the Go Home command between each adjustment attempt
  - Re-check calibration location
- Once calibrated run the Go Home command
- Now you can laser things

## Material settings
TODO find out some useful rought tool settings for the LC50 module.
