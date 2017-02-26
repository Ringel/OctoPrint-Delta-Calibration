This is a plugin for the 3D printer host software [OctoPrint](http://www.octoprint.org), designed to accurately calibrate delta printers.

# About
This version is a expermimental modification of Gene Buckle's ["OctoPrint-Delta-Calibration Plugin"](https://github.com/geneb/OctoPrint-Delta-Calibration), which was initially designed for the RAMBo and Mini-Rambo based line of delta printers manufactured by SeeMeCNC.

As of now, it also works well with stock [Repetier Firmware](https://github.com/repetier/Repetier-Firmware), at least on my printer. Theoretically, it should work on any delta printer running an up-to-date [Repetier Firmware](https://github.com/repetier/Repetier-Firmware).

The "brains" behind this calibration plugin were graciously supplied by David Crocker (dc42).
David's "least squares" calibration algorithm is so good that it's essentially magic. The calibration
code in this plugin is the same code that can be found behind his website, here: 
[Delta printer least-squares calibration calculator](http://www.escher3d.com/pages/wizards/wizarddelta.php). His calibration routines are also found
in the dc42 fork of RepRapFirmware for the Duet controller.

# Getting Started

## Disclaimer

:warning: This version is very experimental. Be warned at your own risk! 

## Prerequisites

### Z-Probe
You need a working Z-Probe.

This plugin uses G30 for probing the print bed. So, when G30 is working, there is a good chance that the plugin works too.
If you are not shure, read Repetier's site on [Z-Probing with Repetier-Firmware](https://www.repetier.com/documentation/repetier-firmware/z-probing/).

### Firmware
You must also be running an up-to-date version of Repetier Firmware.
* Stock Repetier: Version 0.92.8 and up. I'm using 1.0.0-dev.
* SeeMeCNC's fork of Repetier Firmware with a firmware date of 20161209 or later. (Issue an M115 to see the firmware date, ex.: FIRMWARE_NAME:Repetier_0.92.2 FIRMWARE_DATE:20161209 MACHINE_TYPE:Rostock MAX v3)

## Installation

To use this plugin, you can install it either:

### Using the OctoPrint Plugin Manager

Click on the Settings link in OctoPrint and then click on the "Plugin Manager" link that's listed in the Plugins pane on the lower left. Then click the "Get More..." button, enter the URL https://github.com/ponschab/OctoPrint-Delta-Calibration/archive/stock-repetier.zip and finally click the "Install" button.

### Using pip from a shell prompt

    pip install https://github.com/ponschab/OctoPrint-Delta-Calibration/archive/stock-repetier.zip

If you're working with an OctoPi distribution, you can sign into the "pi" account and
install the plugin this way:

    /home/pi/oprint/bin/pip install https://github.com/ponschab/OctoPrint-Delta-Calibration/archive/stock-repetier.zip

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
* Gene Buckle. For the great plugin and for releasing it unter the [AGPLv3](https://www.gnu.org/licenses/agpl-3.0.html) License.
* Ryan Rittenhouse, SeeMeCNC's new cat herder (software developer). If it wasn't for his valuable assistance, this plugin simply wouldn't have worked right for a very long time.
* David Crocker (dc42). For his ingenious calibration algorithm and for giving it to the community.
* platsch. The core of this was shamelessly stripped from [OctoPrint-Autocalibration
](https://github.com/platsch/OctoPrint-Autocalibration). Pretty much the only thing left is the routines used to read/write the EEPROM. :)

**Enjoy!**
