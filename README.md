# C64UnifDiagCart

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
* Zero Page Memory resides at Locations $0000 - $00FF.
* The Stack Page resides at Memory Locations $0100 - $01FF.
* RAM Locations $0200 - $03FF.
* The Screen RAM resides at Memory Locations $0400 - $07FF.
* The Color RAM resides at Memory Locations $D800 - $DC00.
* RAM Locations $0800 - $0FFF.

Due to the hardware configuration of the Commodore C64's DRAMs, all DRAMs come into play in the management of the first 4Kbytes of RAM ($0000 - $0FFF), so if at least one of the DRAM chips is not functioning correctly, the test carried out by Dead Test will highlight the problem.

When the Dead Test does not detect system malfunctions, it is notorious for changing the type of diagnostics, and therefore the type of cartridge, for a more in-depth analysis.

**Appeareance**

|||
|:---:|:---:|
|![PCB](./files/UnifA.PNG)|![PCB](./files/UnifB.PNG)|
