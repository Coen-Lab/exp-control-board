#Experimental Control Board
This repository houses the electronics, firmware, and case design for the experimental control board. This board was designed by [Max Hunter](https://maxhunter.me/), to the specifications of Philip Coen. It  is designed both with features that are universally applicable to experimental neuroscience rigs, as well as some features which may not (but may) be useful outside the Coen Lab. In particular, the entire board costs less than the commercial equivalent of some single features (e.g. constant current delivery, or a thresholded, adjustable photodiode circuit).

The board as sold comprises:
- 24V, 220W power supply
- Photodiode (2-pin)
- Temperature sensor (3-pin)
- Enclosure
- ECB Version 1 with the following features
	- Temperature-controlled PID Peltier cooler output with overheat protection
	- Two fixed 12V, 3A(max) 2A(continuous) power rails for auxiliary devices, one with switchable on/off output
	- Four variable 3-23V, 3A(max) 2A(continuous) power rails for auxiliary devices, all with switchable on/off outputs
	- One 1A ±12V, zero-centred power supply for Thorlabs photodiode
	- Photosensor with variable sensitivity trigger (5V TTL digital output)
	- Three DRV104 valve controllers, 12V output
	- Two logic inverters (5V TTL logic I/O)
	- One Arduino Nano V3, used to control Peltier output and random ‘flipper’ output, with 6 spare IO for future expansion

For detailed instructions, please contact [Max Hunter](https://maxhunter.me/).

&nbsp;
&nbsp;
This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg
