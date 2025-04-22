I am currently playing Phantasy Star Online Ver 2 on PC using 4k resolution and high color contrast in Arch Linux. This is every step I took to get my game working.

Notes on creating a WINEPREFIX: If you're not familiar with now Wine and Linux works, think of your WINEPREFIX as a psuedo sandboxed windows layer specific for your game. This way, when you install things like `dsound` it won't interfere with your other Wine prefixes for other games. 

For sections that say `/your/path/to/prefix`, this a path you will determine. For example, you could make it `/home/replace_me_with_your_username/pso_pc` or if you prefer XDG you can make it something like `/home/replace_me_with_your_username/.local/share/pso_pc`

Notes on macOS: I do not have much experience with macOS, however I assume that since it's Unix and supports Wine the steps *might* be similar. If you are on macOS and this method works for you, please feel free to let me know.

Create WINEPREFIX
```
WINEPREFIX=/your/path/to/prefix wineboot
```

Mount your ISO using whatever methods you want.

Run the PSO Installer (Run NORMAL install, not full or custom)
```
WINEPREFIX=/your/path/to/prefix wine /your/path/to/setup.exe
```

Install directmusic and dsound
```
WINEPREFIX=/your/path/to/prefix winetricks directmusic dsound
```

Run winecfg to test audio and set overrides
```
WINEPREFIX=/your/path/to/prefix winecfg
```

Set the following to `native` in the libraries tab (or try "native then bulletin" if you have issues)
```
dsound
dmusic
dmime
dmsynth
```

Move exe files from IVES zip folder to your PSO folder
```
autorun.exe
online.exe
online_offline.exe
pso.exe
```

Open Lutris and "Add locally installed game". Select the path to autorun.exe. Set your prefix path in the game configuration in Lutris.

Download the PSO Music Patch for high quality sound and run the bat file to convert FLAC to WAV in your "22" folder and move it to the following path
```
drive_c/Program Files (x86)/SEGA/PhantasyStarOnline/Media/PSO/SoundBGM/22
```

Copy the contents of Sound/11 to Sound/22

Download `dgvoodooo278.zip`, `PSO_PC_Graphics_Fix.zip` and `PsoWindowSize.7z` from the PSO Peeps Proton Drive or another source if you have one.

Extract contents of `dgvoodooo278.zip` to `/your/path/to/prefix/drive_c/Program Files(x86)/SEGA/PhantasyStarOnline`

Extract contents of `PSO_PC_Graphics_Fix.zip` to

Extract contents of `PsoWindowSize.7z` to `/your/path/to/prefix/drive_c/Program Files(x86)/SEGA/PhantasyStarOnline` and point the Lutris launcher to this file instead of autorun.exe.

Open dgvoodooCpl.exe and set your Glide and DirectX settings to fit your needs.

Open your launcher. Since dgvoodoo is handling the upscaling to your preferred resolution, just select one of the three options for resolution instead of a custom one.

Sidenote: In absent of a widescreen mod, if you prefer true 4:3 instead of a stretched 16:9 image my solution was to enable Gamescope in Lutris. However, this sort of breaks the launcher as it launches it in the higher resolution. When you close PSO, your launcher may crash and require stopping in your system processes. If anyone knows a workaround for this feel free to open an issue.

LAUNCH THE GAME!
