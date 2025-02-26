# C64 Unified Diagnostic Cartridge

The original Dead Test Diagnostic Cartridge is designed to test
the C64 and C128/C128D, (C64 Mode), Systems that fail
to display video information on Power Up even with the
C64 or C128/C128D Diagnostic Assembly installed.

The Dead Test is meant only as an extra troubleshooting
tool to assist the Technician in repairing Dead PCBs and
does not replace the current C64 or C128/C128D Diagnostic
Assemblies now being used.

The Dead Test is almost completely dedicated to System RAM
testing and does no type of System ROM or Port Testing.

The Dead Test is an Ultimax type cartridge that starts the Commodore 64 in that mode and not all areas of the RAM (64KByte) are accessible. Only the following locations were accessible:
* Zero Page Memory resides at locations $0000 - $00FF.
* The Stack Page resides at Memory locations $0100 - $01FF.
* RAM locations $0200 - $03FF.
* The Screen RAM resides at Memory locations $0400 - $07FF.
* The Color RAM resides at Memory locations $D800 - $DC00.
* RAM locations $0800 - $0FFF.

Due to the hardware configuration of the Commodore C64's DRAMs, all DRAMs come into play in the management of the first 4Kbytes of RAM ($0000 - $0FFF), so if at least one of the DRAM chips is not functioning correctly, the test carried out by Dead Test will highlight the problem.

When the Dead Test does not detect system malfunctions, it is notorious for changing the type of diagnostics, and therefore the type of cartridge, for a more in-depth analysis.

The <b>C64 Unified Diagnostic Cartridge</b> simplifies and automatically unifies this procedure in one single cartrdige. It starts the Commodore 64 in Ultimax mode, executing the code present in a portion of memory (Eprom or FlashRom) of the cartridge, 16Kbytes large, in particular the second 8Kbytes. In this memory area there must be the code of a Dead Test (but DesTestMax can also be fine) appropriately modified.

The modification consists in carrying out only a complete cycle of Dead Test analysis and then making sure that the type of cartridge changes automatically by switching from Ultimax mode to Standard mode, accessing the $DE00 location, and then doing a soft reset of the system. By changing the mode, the first 8KBytes of the cartridge will be executed as a standard cartridge, it follows that the code of a complete analysis and test cartridge must be present in the first 8KBytes. The soft reset will be the trigger for the start of the latter.


**Original Dead Test Mod**

How was the original Dead Test modified by worldofjani.com?
It was identified in the source assembly as the point at which the increment of the full test cycle count occurs, and then a check was added to see if the second cycle was starting, and at that point a jump to an additional piece of code copying the cartridge type change routine plus softreset, in RAM area $0334.
|Original 781220| Mod (cycle control)|Mod (routine)|
|:---:|:---:|:---:|
|![PCB](./files/DeadOrig.PNG)|![PCB](./files/DeadOrigMod1.PNG)|![PCB](./files/DeadOrigMod2.PNG)|

[Original C64 deadtest diagnostic 781220](./files/C64_Diag_781220_deadtest_disasm_orig.tas), [modded src verion](./files/C64_Diag_781220_deadtest_disasm.tas), [modded bin verion](./files/C64_Diag_781220_deadtest_disasm_mod.bin).
Get your favourite version of the standard diagnostic from [worldofjani.com](https://blog.worldofjani.com/?p=1981).

To make the 32Kbyte file to be written to the eprom, merge the 8Kbyte binary file (first block) of the Standard Diagnostics with the binary file of the Dead Test mod version (second 8Kbyte block), then add 16Kbyte (third and fourth blocks) of hexadecimal #$FF values. Working example: [Unified_32k.bin](./files/Unified_32k.bin).

Components
---------
- 27C256 or 27C512 (DIP_28) [U1]
- 74HCT74 (or 74LS74) (DIP_14 or SMD SO_14) [U2]
- 74HCT00 (or 74LS00) (DIP_14 or SMD SO_14) [U3]
- 100nF (THT or SMD_0805) x3 [C1, C2, C3]

**Optional lighting eyes**
- SMD led (SMD_0603) x2 [DE1, DE2] (UP/DOWN reverse mounted to see the light through the hole)
- From 400 to 1K Ω (SMD_1206) [R1]

**Appeareance**

|||
|:---:|:---:|
|![PCB](./files/UnifA.PNG)|![PCB](./files/UnifB.PNG)|

Jumper configuration
--------------------

**JPE** and **JPG** are used to configure which mode (Ultimax or Standard) should start at start-up. They are already configured to start the Ultimax mode. If you want to reverse the order, you have to cut the pre-existing tracks in JPE and JPG.

**Start with Ultimax mode (default,connection already present)**

| JPE | JPG |
|:---:|:---:|
|Short 1 and 2|Short 1 and 2|
|![J2](./files/j1.png)|![J1](./files/j1.png)|

**Start with Stadard mode (cut and soldering)**

| JPE | JPG |
|:---:|:---:|
|Short 2 and 3|Short 2 and 3|
|![J2](./files/j2.png)|![J1](./files/j2.png)|

**JPS**<br>
There is the possibility of being able to select a second image (the second 16Kbyte of the BIN file to be written to the eprom) to start a different image created, for example with a different dead test or with DesTestMax. This can be done using **JPS**.
By default, the central pin of JPS must be closed with pin 0. On position 0, the image of the first part of the total 32Kbyte eprom will be executed at start-up. At position 1, the image of the second part will be executed at start-up. Solder the middle part of JPS with the 0 if you do not want to create a cartridge with two different images.

**JPT**<br>
The eprom to be used can be either a 27C256 or a 27C512. It is necessary to solder the appropriate part.

| 27C256| 27C512 |
|:---:|:---:|
|Short 1 and 2|Short 2 and 3|
|![J2](./files/j1r.png)|![J1](./files/j2r.png)|

PCB
---

You can find the gerber file on [PCBWay](https://www.pcbway.com/project/shareproject/C64_Unified_Diagnostic_Cartridge_a834cce3.html) and if you want to support my work order it from them.

![PCBWAY](./files/pcbway.png)
