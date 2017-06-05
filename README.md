This is a plugin for the 3D printer host software [OctoPrint](http://www.octoprint.org), designed to accurately calibrate delta printers.

# About
This plugin is forked from the Delta Auto Calibration plugin which is dedicated for delta printers manufactured by SeeMeCNC (http://www.seemecnc.com) to support original Repetier and Marlin firmware.

## Credits:
- David Crocker (dc42) with his "least squares" calibration algorithm:
http://www.escher3d.com/pages/wizards/wizarddelta.php
- Gene Buckle (geneb) with his original plugin:
https://github.com/geneb/OctoPrint-Delta-Calibration
- Marc Ponschab (ponschab) with his Delta Calibration plugin for Repetier:
https://github.com/ponschab/OctoPrint-Delta-Calibration

For now, the plugin ist fixed to 6-factors-calibration (endstop corrections, delta radius, and two tower angular position corrections) by measuring 10 points.

# Getting Started

## Disclaimer

:warning: This version is very experimental. Be warned at your own risk! 

## Prerequisites

### Z-Probe
You need a working Z-Probe.

This plugin uses G30 for probing the print bed. So, when G30 is working, there is a good chance that the plugin works too.

### Firmware
* Marlin Firmware Version 1.1.1
* Stock Repetier: Version 0.92.8 and up. I'm using 1.0.0-dev.
* SeeMeCNC's fork of Repetier Firmware with a firmware date of 20161209 or later. (Issue an M115 to see the firmware date, ex.: FIRMWARE_NAME:Repetier_0.92.2 FIRMWARE_DATE:20161209 MACHINE_TYPE:Rostock MAX v3)

## Installation

To use this plugin, you can install it either:

### Using the OctoPrint Plugin Manager

Click on the Settings link in OctoPrint and then click on the "Plugin Manager" link that's listed in the Plugins pane on the lower left. Then click the "Get More..." button, enter the URL https://github.com/ringel/OctoPrint-Delta-Calibration/archive/marlin-1.1.1.zip and finally click the "Install" button.

### Using pip from a shell prompt

    pip install https://github.com/ringel/OctoPrint-Delta-Calibration/archive/marlin-1.1.1.zip

If you're working with an OctoPi distribution, you can sign into the "pi" account and
install the plugin this way:

    /home/pi/oprint/bin/pip install https://github.com/ringel/OctoPrint-Delta-Calibration/archive/marlin-1.1.1.zip

## Do it!
Before running this utility on your printer, you should issue a G29 command via the OctoPrint
terminal. This will kick off the internal calibration and will get the Z height properly set.

In order to use the plugin, click on the Settings link in OctoPrint and then click on the
"Delta Autocalibration" link that's listed in the Plugins pane on the lower left.

Click the Load EEPROM button and then click the Begin Delta Calibration button.

You may run it as many times as you like, but you MUST click the Load EEPROM button before you begin
the calibration sequence!  If you fail to do this, the calibration routine will NOT know what the current
parameters are and you'll get poor, bad, or moderately catastrophic results.

There's also an additional button 'Check Z-Probe Repeatability', which runs multiple G30 z-probes, and calculates the deviation between them.

# Issues
If you encounter any issues, don't hesitate to create an issue.

# Thanks
* Marc Ponschab. For the Repetier version - only minor adjustments needed to implement Marlin.
* Gene Buckle. For the great plugin and for releasing it unter the [AGPLv3](https://www.gnu.org/licenses/agpl-3.0.html) License.
* Ryan Rittenhouse, SeeMeCNC's new cat herder (software developer). If it wasn't for his valuable assistance, this plugin simply wouldn't have worked right for a very long time.
* David Crocker (dc42). For his ingenious calibration algorithm and for giving it to the community.
* platsch. The core of this was shamelessly stripped from [OctoPrint-Autocalibration
](https://github.com/platsch/OctoPrint-Autocalibration). Pretty much the only thing left is the routines used to read/write the EEPROM. :)

**Enjoy!**
