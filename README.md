Shield: [![CC BY 4.0][cc-by-shield]][cc-by]

This work is licensed under a
[Creative Commons Attribution 4.0 International License][cc-by].

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg

# miyooDoomdeh
Sets up folder structure and config files for Doom Wads (with companion deh files) for Miyoo Mini+
USE AT YOUR OWN CAUTION. Keep backups of the Wads/Dehs in case something goes wrong when the roms are being moved into folders, though I've never had an issue.

THE SHORT:
Doom wads/dehs in doom folder. Doom II wads/dehs in doom2 folder. Run python file. Copy Roms and Saves folder into root of Miyoo Mini.
ONLY WORKS FOR BOOM COMPATIBLE WADS as Miyoo uses PrBOOM via retroarch.

THE LONG:

  Main GOAL: 
  Play Army of Darkness Doom TC on Miyoo Mini+ which requires executing a DeHacked file.

  Purpose:
  Many of the retro handhelds support DOOM via PrBOOM. I received both a Miyoo Mini+ and a RG35xx recently to play with.
  I found that the custom firmware for the Miyoo (OnionOS) is much better than the RG35xx currently (GarlicOS).
  Looking through the libretro notes for PrBOOM I noticed that regular BOOM port wads also support deh files, which many mods/TCs come with.
    
  Through testing, I've found that embedding the deh files with some newer DOOM editors does not work for PrBOOM.
  There's no way currently for the Miyoo/RetroArch to recognize the deh files, but they can be specified in the prboom.cfg which is creating after running the wad.
  This means that you have to create the custom shortcuts, put the wads in the correct folder, run it once, then edit the cfg in order to add the deh file.
    
  So with a combination of very rusty Python skills, ChatGPT, and Stack Exchange/Overflow I set out to automate the process as much as possible.

  Process:
  Place doom wads in a doom folder along with their deh file (currently only works for a single deh)
  Place doom II wads in a doom2 folder along with their deh file.
  Do the same for tnt wads (may not be necessary)
    
  The program will scan each folder, recognize whether each wad has a companion deh, move the wads into the appropriate rom structure for the miyoo, 
  and then create .notfound shorcuts (for importing), along with appropriate prboom.cfg files, all in appropriate folder structure.
  This results in a Roms and Saves folder which can be copied into the root of the Miyoo.
    
  In the Miyoo head to the ports and Import. Each shortcut should be present and working in the Doom section of the Ports. Provide your own thumnbails in the PORTS\Imgs folder.
  Currently works for me in all scenarios.
   
  Test with:
  Army of Darkness TC for DOOM (DOOM II version should also work), Batman Doom for DOOM II, and Doom 4 Vanilla for DOOM II.
  May need to manually adjust the audio hz in prboom.cfg for AOD as some of the longer Bruce clips seem to play slow. Could be limitation of the system/port.

  Notes on ChatGPT:
  I'm not a programmer, but I write programs every now and then. The only previous one I have on GitHub is a script for converting configs between two different retro front ends. 
  I previously wrote that from scratch in Python. I've always dabbled here and there since BASIC in my yough, and often write .bat scripts and less often Python files to automate tasks often related to emu/retro.
  I can go months or sometimes years without coding, so I lose some knowledge. This is where ChatGPT comes in. I use the free version and it works about half the time. It gets confused easily.
  I often have to fix things by hand. It also can't handle very long code in the free version.
    
  So the base starts out as ChatGPT and then as the versions go along it's me and Stack figuring out why it can't do what I ask it to do. In some cases though, it does
  save quite a bit of time getting the foundations of what I want to do all done for me. I had to fight with it quite a bit due to the length of the config outputs and it not understanding the formatting of them.

TODO: (Maybe)
  Copy over thumbnails (if present) to Imgs folder.
  Support more than one deh file.
  Support secondary wads and or custom music files.
  Figure out the structure for RG35xx (GarlicOS) and provide option or convert between the two.
  Do it all in a UI or Drag n drop folders onto the py?
  Make it executable.
