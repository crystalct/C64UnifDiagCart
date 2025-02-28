# How to mod the DesMaxTest for the UnifDiagCart

You need `bspatch.exe` from [bsdiff-v4.3-win-x64.zip](https://github.com/reitowo/bsdiff-win/releases), `bzip2.exe` from [bzip2-1.0.5-bin.zip](https://gnuwin32.sourceforge.net/downlinks/bzip2-bin-zip.php) and `rhash.exe` from [rhash-1.4.3-win32.zip](https://sourceforge.net/projects/rhash/files/rhash/1.4.3/rhash-1.4.3-win32.zip/download) to check the correct version of the files.

From Factor of Matt [site](https://factorofmatt.com/destestmax-sl-download) download `destest-max.rom` and `patch.bin` from [here](./patch.bin). 

Put `bspatch.exe`, `bzip2.exe`, `rhash.exe`, `destest-max.rom` and `patch.bin` in a folder, for example `C:\tmp>` ...

Check the correct version of `destest-max.rom` using `rhash.exe`: to obtain `ca6effd37cb7205544886b93fac541c8` as CRC<br>
`C:\tmp>rhash --md5 destest-max.rom`<br>
`ca6effd37cb7205544886b93fac541c8  destest-max.rom`

To create the mod version, run the command:<br>
`C:\tmp>bspatch destest-max.rom destest-max-modded.bin patch.bin`

`destest-max-modded.bin` is the binary file to be used as the 8Kbyte image of the Ultimax part to be written to the eprom.
