# Slingshooter – unofficial SDL2 port of the 7th Level engine

*Slingshooter* is one of the games of *Pumbaa and Timon's Jungle Arcade* (7th Level, 1996), a Windows 3.1 game built on the
**7th Level Runtime Player 1.2**. This repository builds a native 64-bit Windows version of it
with **[7thlevel-engine](https://github.com/LuC-iTA-GHorg/7thlevel-engine)**, a from-scratch
reimplementation of that engine in C11 + SDL2, included here as a git submodule (`engine\`).
No emulator, no virtual machine.

> **You need your own copy of the original game.** This repository contains **no game data, no
> original code and no original assets**. See [NOTICE.md](NOTICE.md).

## Status

The port starts from `T&PSHTPC.BIN`, plays the Jungle Arcade intro and reaches the game screen. See the engine repository for the general status and the known differences.

## Requirements

- Windows 10 or 11, 64-bit, and git.
- The files of the original CD: `HYENA.TTF`, `JUNGA02.DLL`, `JUNGCRED.BIN`, `JUNGINT1.BIN`, `JUNGPRTY.BIN`, `JUNGR02.DLL`, `JUNGS02.DLL`, `JUNGSHOT.BIN`, `JUNGSING.BIN`, `JUNGU02.DLL`, `T&PSHTPC.BIN`, `T&PSHTPC.EXE`.
- About 120 MB of free space for the portable build tools (downloaded on request).

## Building

```bat
git clone --recursive https://github.com/LuC-iTA-GHorg/slingshooter-7thlevel-port.git
cd slingshooter-7thlevel-port
rem copy the files of your CD here (or set GAME_DATA to their folder), then:
build.bat
```

The first time, the engine's `tools\setup_tools.bat build` shows what it is going to download
(w64devkit GCC, SDL2, the GeneralUser GS SoundFont), asks for confirmation and checks the SHA-256
of every file. The scripts of the game are translated to C from your `.BIN` files into
`build\gamesrc\` and compiled with the engine: do not publish those generated files.

Output: `build\slingshooter.exe` and `build\slingshooter_launcher.exe`. `engine\tools\make_dist.bat`
(with `GAME_ROOT` set to this folder) collects what is needed to play in `dist\`.

If you cloned without `--recursive`: `git submodule update --init`.

## Running

Start `build\slingshooter_launcher.exe` (settings, then "Start"), or `build\slingshooter.exe`. Options,
keys and the `slingshooter.ini` settings are described in the engine's README.

## License

No license has been chosen yet for the code of this project: until then, all rights are reserved
by its author. The game, its names and its data belong to their respective owners.
