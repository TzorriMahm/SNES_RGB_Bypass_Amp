# SNES RGB Bypass Amp
**A modding board to bypass the SNES' video encoder by using TI's THS7374 video amplifier, to achieve optimised RGB video.**<br>

This modification works with all 1-Chip models (PAL/NTSC).

![Header image](https://github.com/TzorriMahm/SNES_RGB_Bypass_Amp/blob/master/img_snes/snes_header-wm.png)
<br><br>
**⁓ Designed with ♥ in Germany ⁓**<br><br>
![TzorriMahm](https://github.com/TzorriMahm/SNES_RGB_Bypass_Amp/blob/master/img_snes/tzorri_logo.png)
# Where to get the PCB?
You can order the PCB directly from [OSHPark](https://oshpark.com/shared_projects/Fqaqnu3s).
Of course, feel free to use the gerber files with any manufacturer of your choice.<br>
Use 0.8mm board thickness to ensure an easy and clean installation.

# Before you start
Make sure that your console is a 1-Chip model. If your console is a SNES2/Mini/Jr., this is the case by default.<br>
Otherwise, this can easily done by looking for an indicator at the main board:

![1-CHIP](https://github.com/TzorriMahm/SNES_RGB_Bypass_Amp/blob/master/img_snes/1-chip-wm.jpg)

# Install instructions
## PAL consoles (SNSP-001)
### Preparing the SNES main board
**1-CHIP-01/02 models**
- disconnect +12V from MultiOut Pin 3: **remove R28**
- disconnect stock RGB: **remove R15, R16, R17**
- remove decoupling caps from MultiOut (optional**¹**): **remove C44, C45, C46, C47**

### Installing the modding board
- isolate the bottom side of the modding board to avoid any shorts
- solder the modding board onto the pins of the MultiOut
- solder a wire from the via next to R6 (SNES main board) to pad 'R' (modding board)
- solder a wire from the via next to R7 (SNES main board) to pad 'G' (modding board)
- solder a wire from the via next to R8 (SNES main board) to pad 'B' (modding board)  
- solder a wire from the via that is nearest the bottom left corner of designator C6 (SNES main board) to pad 'CS' (modding board)  

### Install diagram (PAL 1-CHIP)
![PAL install diagram](https://github.com/TzorriMahm/SNES_RGB_Bypass_Amp/blob/master/img_snes/pal_dia-wm.png)

## NTSC consoles (SNS-001/SHVC-001)
### Preparing the SNES main board
**1-CHIP-01/02 models**<br>
These models already have C-Sync connected to pin 3 of the MultiOut.<br>
You can either use this (not recommended) or:
- disconnect C-Sync from MultiOut Pin 3: **remove R12** (optionally **remove R9, R10, R11, Q1** as well)
- disconnect stock RGB: **remove R15, R16, R17**
- remove decoupling caps from MultiOut (optional**¹**): **remove C44, C45, C46, C47**

**1-CHIP-03 model**<br>
This model hasn't C-Sync connected at all, so you'll have nothing to do here.
- disconnect stock RGB:	**remove R15, R16, R17**
- remove decoupling caps from MultiOut (optional**¹**'**²**):	**remove C44, C45, C47**

### Installing the modding board
- isolate the bottom side of the modding board to avoid any shorts
- solder the modding board onto the pins of the MultiOut
- solder a wire from the via next to R6 (SNES main board) to pad 'R' (modding board)
- solder a wire from the via next to R7 (SNES main board) to pad 'G' (modding board)
- solder a wire from the via next to R8 (SNES main board) to pad 'B' (modding board) 
- solder a wire from the via under the left pad of R9 (SNES main board) to pad 'CS' (modding board)

### Install diagram (NTSC 1-CHIP)
![NTSC install diagram](https://github.com/TzorriMahm/SNES_RGB_Bypass_Amp/blob/master/img_snes/ntsc_dia-wm.png)

## NTSC model 2 / SNES2/Mini/Jr. (SNS-101/SHVC-101)
### Preparing the SNES main board
**SNN-CPU-01 model**<br>
Since this model doesn't have stock RGB, here is no preparation needed.

### Installing the modding board
- isolate the bottom side of the modding board to avoid any shorts
- solder the modding board onto the pins of the MultiOut
- solder wires from the vias (shown in the install diagram below) to the appropriate pads on the modding board

### Install diagram (SNES2/Mini/Jr.)
![SNES2 install diagram](https://github.com/TzorriMahm/SNES_RGB_Bypass_Amp/blob/master/img_snes/snes2_dia-wm.png)

### Notes
**¹** if you remove the decoupling caps at the MultiOut, make sure to occupy C22, C32, C42 & C51 on the modding board! Never use both at the same time!<br>
**²** if you leave the decoupling caps at the MultiOut, make sure to occupy **at least** C51 on the modding board! (1-CHIP-03 only!) 

# Troubleshooting
Double-check continuity between connections:
- 'R' (modding board) ⇄ S-CPUN pin 156 / S-RGB pin 5 (SNES main board)
- 'G' (modding board) ⇄ S-CPUN pin 157 / S-RGB pin 3 (SNES main board)
- 'B' (modding board) ⇄ S-CPUN pin 158 / S-RGB pin 1 (SNES main board)
- 'CS' (modding board) ⇄ S-CPUN pin 151 / S-RGB pin 7 (SNES main board)

# Miscellaneous
#### Jumper 'J:LPF'
The THS7374 has a low pass filter on each of the four channels which can be turned on by shorting jumper 'J:LPF' on the modding board. This is mostly needed if you wire the console directly to a flat-screen TV. There's no need for the low pass filter on analogue devices.<br>
If you use an OSSC or a Framemeister, it's better to use their filter options.

#### Ghosting fix
In order to get rid of the ghosting issue (which 1-Chip models are known for), simply replace C11 (SNES main board) by a 470nF ceramic capacitor (0805 for normal/fat models, 0603 for SNES2/Mini/Jr.).

#### RGB cable
You will need a RGB cable with 220µF electrolytic capacitors on each of the 'R', 'G' & 'B' lines. The positive end is facing towards the console.<br>
This modding board is designed to output TTL level C-Sync directly at the MultiOut of the console.<br>
With that in mind, make sure you're using a suitable cable with a 470Ω resistor on the sync line to use it with most consumer products (like TV's, OSSC, Framemeister)!

# Disclaimer
I am not responsible for any damage to you, your devices or anything else!<br>
If you do the modification, you do it at your own risk and responsibility!

# Acknowledgement
Most of the credits should go to [borti4938](https://github.com/borti4938). He has made the actual (slightly different) circuit and inspired me to design this board. Thanks man! Thanks to Voultar for research and findig the ghosting fix! Thanks Bob, for your awesome and informative website [RetroRGB](http://retrorgb.com)!<br>
And of course, thanks to the whole retro gaming community for keeping the spirit alive!