# [dok-net/RF100](https://github.com/dok-net/RF100/)
This is a repository with all Conrad documentation, the SD card contents,
and the latest Cura releases plus the RF100 V1 and V2 configuration files for it.

## Setup Guide
A link to the latest Cura release can be located in the 
`Software/Windows` or `Software/Mac` directory of this repository.
After installing, please do not chose to start Cura immediately, but rather
perform the following steps first.

In the same directory as the Cura setup file, there is a
`renkforce_rf100.def.json` printer definition file. Replace this
for the original printer definition file of the Cura installation, which is
located in `Program Files/Ultimaker Cura */resources/definitions`.
Also copy the `renkforce_rf100_v2.def.json` and `renkforce_rf100_xl.def.json`
printer definition files for the RF100 V2 and the XL to the same location.
Then copy the extruder definition files `renkforce_rf100_extruder_0.def` and
`renkforce_rf100_xl_extruder_0.def.json`, both belong
into `Program Files/Ultimaker Cura */resources/extruders`.

Next, start the Cura application, and in the pop-up window opened via
the menu item `Preferences/Configure Cura...`, select `Profiles`, and
then `Import` the custom profiles locate in this repository's `Config/Windows`
or `Config/Mac` directory.

For the default material selection of the RF100, PLA, you will then probably
want to `Activate` the custom profile `Config-PLA` as your default profile.

## Firmware Guide
The RF100 printer runs the Open Source [Marlin](http://marlinfw.org/) firmware.
The most obvious advantage of switching to the updated community-configured
version of Marlin versus the RF100 v1 is the increased print space, from 100mm
to 105mm, 110mm and 105mm in x/y/z dimensions, respectively. If you own the
RF100 v2, the only update in the stock firmware sources published by Conrad
actually was just this print space declaration, 120mm cubed for that printer.

After flashing new firmware to your printer, please reset the EEPROM to defaults
via the appropriate menu item under `Control`.

### Downloading pre-built firmware file to your RF100
In the menu bar, locate the `Settings` drop-down menu, select `Printer`,
then `Manager Printers...`. When you select your RF100 V1, V2, or XL printer
and push the `Update Firmware` button, the remaining steps should be
self-explaining. Use the matching firmware hex file for your printer version
provided here in the `Software/Firmware` folder. The `RF100 V1.1.cpp.hex` or
`RF100 V2.2.cpp.hex` firmware are the official ones provided by Conrad. For
updated community firmware, that for instance is based on much more recent
Marlin releases, choose among the RF100 Marlin hex firmware binaries.

### Build from source and flash in Arduino IDE (or compatible IDE)
If you have some familiarity with the Arduino IDE, this should be quite simple.
For V2 of the RF100, insert V2 into the repository names/branches/directory names
as appropriate.

Obtain the sources from the Github repository
[dok-net/Marlin](https://github.com/dok-net/Marlin/tree/renkforce_rf100_v2).
There should be a version tag that mimics the version tag in this repository,
like our version `v2.2-pre` is matched by `rf100-v2.2-pre` there.
Use this if you want to inspect the sources or rebuild the same binary firmware
as included here.
Please install the [LiquidCrystal](https://www.arduino.cc/en/Reference/LiquidCrystal)
library.
Copy the contents of the `Marlin/example_configurations/Renkforce/RF100` folder
into the Marlin folder.
Select this in the board manager: `ATmega2560 (Mega 2560) (Arduino/Genuino Mega)`.
Build the `Marlin.ino` project.
