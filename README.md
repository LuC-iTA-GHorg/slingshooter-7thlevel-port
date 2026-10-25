# Slingshooter – unofficial SDL2 port of the 7th Level engine

*Slingshooter* is one of the games of *Pumbaa and Timon's Jungle Arcade* (7th Level, 1996), a Windows 3.1
game built on the **7th Level Runtime Player 1.2**. This repository builds a native 64-bit Windows version of it
with **[7thlevel-engine](https://github.com/LuC-iTA-GHorg/7thlevel-engine)**, a from-scratch
reimplementation of that engine in C11 + SDL2 shared by all the 7th Level games, included here
as a git submodule (`engine\`). No emulator, no virtual machine.

> **You need your own copy of the original game.** This repository contains **no game data, no
> original code and no original assets**. See [NOTICE.md](NOTICE.md).

## Status

Update 2026-10-25, engine `1674013`: sprite replacement (opcode 18) and immediate animation commands (builtin 5A) now behave like the original. This fixes Slingshooter: the purple berry splat was drawn at the centre of the screen instead of on the target.

Update 2026-10-25 (engine `aa95168`): the scores are drawn again; they were empty boxes because `HYENA.TTF` is a symbol font, which is now mapped like Windows GDI does.

The engine implements every feature of the original 7th Level Runtime Player, and the port starts from
`T&PSHTPC.BIN`. Slingshooter has not been compared with the original game yet (only Upsy Daisy has been, screen by
screen), so differences may remain. See the engine repository for the general status and the
known differences.

## Requirements

- Windows 10 or 11, 64-bit, and git.
- The files of the original CD: the `.BIN` libraries (`JUNGCRED.BIN`, `JUNGINT1.BIN`, `JUNGPRTY.BIN`, `JUNGSHOT.BIN`, `JUNGSING.BIN`, `T&PSHTPC.BIN`), `T&PSHTPC.EXE` (for the icon, the cursors and the settings section) and the font `HYENA.TTF`. The `.DLL` files of the CD are not used.
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
