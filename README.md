# Experimental Control Board (ECB)
This repository houses the electronics, firmware, and enclosure design for the experimental control board. This board was designed by [Max Hunter](https://maxhunter.me/), to the specifications of Philip Coen. It  is designed both with features that are universally applicable to experimental neuroscience rigs, as well as some features which may not (but may) be useful outside the Coen Lab. In particular, the assembled board can be purchased at a comparable price to a _single component_ from a commercial supplier (e.g. this [current driver](https://www.thorlabs.com/thorproduct.cfm?partnumber=LEDD1B) or this [adjustable photodiode](https://www.thorlabs.com/thorproduct.cfm?partnumber=PDA8A2)). For most applications, this board can fully replace these components (in the enclosure of the current driver, it can replace 3 of them), amongst others.

<p align="center">
<img src="https://github.com/Coen-Lab/exp-control-board/assets/1191043/5419c5a1-e87f-4c7d-b258-bab9e3ddde43">
</p>

If purchased directly from Max, the Version 3 board includes:
- 24V, 220W power supply
- Photodiode (2-pin)
- Temperature sensor (3-pin)
- Enclosure (Pink in above images)
- ECB Version 3 with the following features
	- Temperature-controlled PID Peltier cooler output with overheat protection
	- Two fixed 12V, 3A power rails for auxiliary devices, with switchable on/off outputs
	- Four variable 3-24V, 3A power rails for auxiliary devices, with switchable on/off outputs
	- Three adjustable 0-1A continuous current drivers for LEDs or similar devices
	- Photosensor with variable sensitivity trigger (5V TTL digital output)
	- Two DRV104 valve controllers, 12V output
	- One Arduino Nano V3, used to control Peltier output and random ‘flipper’ output, with 6 spare IO for future expansion

For useage instructions, please see:

[Version 3 documentation](Version3/Docs/INSTRUCTIONS.md)

To purchase pre-assembled units, including photodiode etc. mentioned above, for ~£450 (at time of writing), please contact [Max Hunter](https://maxhunter.me/). 

All details are open source, and you can alternatively print your own boards: there is a folder of Gerbers and pick 'n place files for each version. However, please be aware that stock levels may necessitate equivalent-part subsitutions, so if you aren't familiar with ordering your own PCBs (e.g. you have no idea what Gerbers and pick 'n place files are), then we _strongly_ recommend you order pre-assembled units. Max may also be able to make minor design changes (for a design fee) if there are particular elements you would like added or removed.

&nbsp;
&nbsp;
This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg
