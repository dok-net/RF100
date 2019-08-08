# RF100
A repository with all Conrad documentation, the SD card contents, and the latest
Cura releases plus the RF100 v1 configuration files for it.

## Setup Guide
A link to the latest Cura release can be located in the 
`Software/Windows` or `Software/Mac` directory of this repository.
After installing, please do not chose to start Cura immediately, but rather
perform the following steps first.

In the same directory as the Cura setup file, there is a
`renkforce_rf100_extruder_0.def.json` printer definition file. Replace this
for the original printer definition file of the Cura installation, which is
located in `Program Files/Ultimaker Cura */resources/definitions`.
Do the same with the extruder definition file, that belongs into
`Program Files/Ultimaker Cura */resources/extruders`.

Next, start the Cura application, and in the pop-up window opened via
the menu item `Settings/Profile/Manage Profiles...`, select `Profiles`, and
`Import` the custom profiles locate in this repository's `Config/Windows` or
`Config/Mac` directory.

For the default material selection of the RF100, PLA, you will then probably
want to `Active` the custom profile `Config-PLA` as your default profile.