# alby13's N64 Demo ROM Collection
Random, Short N64 Demo ROMS

<b>Note: You will find each rom in their own folder</b>

## N64 3 Types of Audio Demo ROM:
9/3/2026

A simple music player with a cool mouse cursor that can be moved like Super Mario 64.

![Music Audio Player](/audio-player/n64-audio-demo.jpg)

It showcases the 3 different types of music that the N64 can do:
Sequencing MIDI, Streaming PCM, MOD/XM

Note: This demo was loosely created, it has some bugs including flickering and sometimes a crash is possible. I was quickly able to stop the music and change the music types to get them all the work; resetting may be required.

<br>
<br>

## N64 WRITER - A Notepad / Wordpad / Word ROM
9/3/2026

A decent typing writer program that lets you create new documents, open documents from a Memory Pak, and save documents to a Memory Pak. Typing happens in the RAM, and then save files create **Controller Pak notes**. Sci-fi terminal HUD (dark navy,
cyan rules, amber caret) — a 64DD-style editor.

![Notepad on N64](/n64-writer/writer-screenshot.jpg)

Resolution: 512×240, 16 bpp, 3 buffers.


### Controls

| Input | Action |
| --- | --- |
| **Z** | Toggle on-screen keyboard (pull up / put away) |
| **START** | Focus the top menu (`NEW` / `OPEN` / `SAVE` / `KEYB`). Left/Right cycle, **A** activates |

#### Keyboard UP (Show for typing)

| Input | Action |
| --- | --- |
| D-Pad | Move the highlighted key (repeat delay on hold) |
| Analog stick | Nudge the key highlight |
| **A** | Type the highlighted key at the caret |
| **B** | Backspace |
| **L** | Shift while held (uppercase / symbol layer). OSK **SHIFT** toggles sticky shift |
| **R** | Space (there is also a SPACE key) |
| **C-Down** | Newline / Enter |

#### Keyboard DOWN (Hide for text navigation)

| Input | Action |
| --- | --- |
| D-Pad | Move the caret (left/right by character, up/down by visual line) |
| Analog stick | Move the caret (same as D-Pad; the view follows) |
| **B** | Backspace at the caret |
| **A** | Does not type (keyboard is hidden) |

Editing works without a **memory pak** (RAM only). 
Open and Save need a Controller Pak in port 1.


- `FILENAME` is 1–16 characters from the pak charset:
  `0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ!"#'*+,-./:=?@` and space.
- Document body is ASCII (lowercase + newlines allowed in RAM). Filenames are
  forced uppercase.
- Open lists only notes whose name starts with `NWTR.` so other games' notes
  are not overwritten.
- Untitled Save prompts for a name on the OSK, then writes with `fopen`/`fwrite`.
- Existing notes with the same name are overwritten.
- If the pak filesystem is missing or corrupt: **Z+A to format** (two-button
  confirm). B cancels. Uses `cpakfs_format`.

Controller Paks are 32 KiB / 256-byte pages / up to 16 notes. The document
buffer is 8 KB (status bar shows used/cap and free pages).
