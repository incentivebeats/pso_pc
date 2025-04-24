⚠️ macOS Users: This guide is tailored for Linux. Due to macOS’s lack of Vulkan support and limitations in Wine, vkBasalt, dgVoodoo will not work. For macOS, try CrossOver or Wine + MoltenVK and run the game using default rendering settings.

⚠️ Notes on creating a WINEPREFIX: If you're not familiar with how Wine and Linux works, think of your WINEPREFIX as a psuedo sandboxed windows layer specific for your game. This way, when you install things like `dsound` it won't interfere with your other Wine prefixes for other games. 

⚠️ For sections that say `/your/path/to/prefix`, this a path you will determine. For example, you could make it `/home/replace_me_with_your_username/pso_pc` or if you prefer XDG you can make it something like `/home/replace_me_with_your_username/.local/share/pso_pc`

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

Download `dgvoodooo278.zip`, `PSO_PC_Graphics_Fix.zip` from the PSO Peeps Proton Drive or another source if you have one.

Extract contents of `dgvoodooo278.zip` to `/your/path/to/prefix/drive_c/Program Files(x86)/SEGA/PhantasyStarOnline`

Extract contents of `PSO_PC_Graphics_Fix.zip` to

Open dgvoodooCpl.exe and set DirectX settings to fit your needs. You can use the config file provided in this guide (this is what worked for me for 4k).

Open autorun.exe and play.
