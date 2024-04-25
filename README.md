# Experimental Control Board
This repository houses the electronics, firmware, and case design for the experimental control board. This board was designed by [Max Hunter](https://maxhunter.me/), to the specifications of Philip Coen. It  is designed both with features that are universally applicable to experimental neuroscience rigs, as well as some features which may not (but may) be useful outside the Coen Lab. In particular, the entire board costs less than the commercial equivalent of some single features (e.g. constant current delivery, or a thresholded, adjustable photodiode circuit) from commercial suppliers.

The v3 board as sold comprises:
- 24V, 220W power supply
- Photodiode (2-pin)
- Temperature sensor (3-pin)
- Enclosure
- ECB Version 3 with the following features
	- Temperature-controlled PID Peltier cooler output with overheat protection
	- Two fixed 12V, 3A power rails for auxiliary devices, with switchable on/off outputs
	- Four variable 3-24V, 3A power rails for auxiliary devices, with switchable on/off outputs
	- Three adjustable 0-1A continuous current drivers for LEDs or similar devices
	- Photosensor with variable sensitivity trigger (5V TTL digital output)
	- Two DRV104 valve controllers, 12V output
	- One Arduino Nano V3, used to control Peltier output and random ‘flipper’ output, with 6 spare IO for future expansion

For instructions, please see:

[V1 docs](Version1/Docs/INSTRUCTIONS.md)
[V2 docs](Version2/Docs/INSTRUCTIONS.md)
[V3 docs](Version3/Docs/INSTRUCTIONS.md)

To purchase pre-assembled units, please contact [Max Hunter](https://maxhunter.me/).

&nbsp;
&nbsp;
This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg
