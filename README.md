# RF100
A repository with all Conrad documentation, the SD card contents, and the latest
Cura releases plus the RF100 v1 (also v2 with a few manual corrections)
configuration files for it.

## Setup Guide
A link to the latest Cura release can be located in the 
`Software/Windows` or `Software/Mac` directory of this repository.
After installing, please do not chose to start Cura immediately, but rather
perform the following steps first. For owners of the v2 of the printer, read
the pertinent section below first before installing the configuration files.

In the same directory as the Cura setup file, there is a
`renkforce_rf100.def` printer definition file. Replace this
for the original printer definition file of the Cura installation, which is
located in `Program Files/Ultimaker Cura */resources/definitions`.
Do the same with the extruder definition file `renkforce_rf100_extruder_0.def`,
that belongs into `Program Files/Ultimaker Cura */resources/extruders`.

Next, start the Cura application, and in the pop-up window opened via
the menu item `Settings/Profile/Manage Profiles...`, select `Profiles`, and
`Import` the custom profiles locate in this repository's `Config/Windows` or
`Config/Mac` directory.

For the default material selection of the RF100, PLA, you will then probably
want to `Active` the custom profile `Config-PLA` as your default profile.

### RF100 v2 additional steps
The printer definition file `renkforce_rf100.def` sets the space constraints of
the printer, for the RF100 v2 these are 120mm in each of the three dimensions,
alter the values in the configuration file accordingly, affected are the settings:

```
"machine_depth": {
    "value": "110"
}
```
```
"machine_height": {
    "value": "110"
}
```
```
"machine_width": {
    "value": "105"
}
```

You could also adapt the values for `machine_head_with_fans_polygon` to your
printer, Cura has a configuration dialog for this.

## Firmware Guide
The RF100 printer runs the Open Source [Marlin](http://marlinfw.org/) firmware.
The most obvious advantage of switching to an updated community-configured
version of Marlin on the RF100 v1 is the increased print space, from 100mm to
105mm, 110mm and 110mm in x/y/z dimensions, respectively. If you own the
RF100 v2, the only difference in the Open Source firmware published by Conrad
actually is just this print space declaration, 120mm cubed for that printer.

### Downloading pre-built firmware file to your RF100
In the menu bar, locate the `Settings` drop-down menu, select `Printer`,
then `Manager Printers...`. When you select your RF100 printer and push the
`Update Firmware` button, the remaining steps should be self-explaining. Use
the firmware hex file provided here in the `Software/Firmware` folder. The
`RF100 V1.1.cpp.hex` firmware is the official one provided by Conrad. For
updated community firmware, that for instance is based on much more recent
Marlin releases, choose among the `RF100 Marlin xxx.hex` firmware binaries.

### Build from source and flash in Arduino IDE (or compatible IDE)
If you have some familiarity with the Arduino IDE, this should be quite simple.
Obtain the sources from the Github repository
[dok-net/Marlin](https://github.com/dok-net/Marlin/tree/renkforce_rf100).
There should be a version tag that mimics the version tag in this repository,
like our version `v2.2-pre` is matched by `rf100-v2.2-pre` there.
Use this if you want to inspect the sources or rebuild the same binary firmware
as included here. Otherwise, the `renkforce_rf100` branch is where updated
merges with new Marlin releases can be found.
Please install the [LiquidCrystal](https://www.arduino.cc/en/Reference/LiquidCrystal)
library.
Copy the contents of the `Marlin/example_configurations/Renkforce/RF100` folder
into the Marlin folder.
Select this in the board manager: `ATmega2560 (Mega 2560) (Arduino/Genuino Mega)`.
Build the `Marlin.ino` project.

#### Manual adaptation of the firmware sources for the RF100 V2
In order not to lose 10mm of 120mm (vs. 100mm in stock Conrad firmware for v1)
in each dimension that the improved v2 of the printer hardware offers, before
copying `Marlin/example_configurations/Renkforce/RF100/Configuration.h`,
locate `@section machine` in that file. Set the correct values for your printer:

```
#define X_BED_SIZE 105
#define Y_BED_SIZE 110
```
```
#define Z_MAX_POS 110
```
