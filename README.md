# ParaKit for Paradiddle / Paradiddle VR
### Custom Song Creator & All-in-One Tool — v3.3.0
*App is a work in progress, I will release updates as needed as frequently as possible, thank you*
See "What's New" at the bottom for list of updated features and changes/fixes
v3.5 + will now ship with the requirements in the main .zip download 
ALT DOWNLOAD LINK: [https://limewire.com/d/svTK9#fqZoG5vUjc]
---

Compatible with **Paradiddle (PC)** and **Paradiddle VR (Meta Quest 3)**
Built for use with any supported e-drum kit or the in game kit

> 📖 Refer to this README whenever you need help. The **Quick Start & FAQ** tab (Tab 11) inside the app also covers common questions and fixes.

> ℹ️ First launch may take a moment — this is normal. Wait for the app to fully load before clicking anything. It opens faster after the first launch.

---

## Is ParaKit Right for You?

If you're already experienced with MIDI charting and have your own workflow using tools like Reaper, Audacity, or similar — ParaKit probably isn't gonna replace your primary tools or workflow. That said, parts of it may still save you steps: the Song Creator and batch converter, Stem Splitter, Sheet Music → MIDI, Youtube → FLAC, Asset Manager/Auto MetaData Finder, and Track Preview can slot into an existing workflow without replacing it.

If you're new to charting, don't know where to start, or find dedicated audio/MIDI software intimidating — ParaKit is probably exactly what you're looking for. It handles the full pipeline in one place, with a built-in guide and enough automation to get a playable chart without prior experience.

---

Quick Start

STEP 1 → Stem Splitter (Tab 4)
Split your source audio into drums-only and backing tracks. Use `.flac` or `.wav` for best quality. Use YouTube → FLAC (Tab 8) if you need a lossless source.

STEP 2 → Audio → MIDI (Tab 5) (or Sheet Music → MIDI, Tab 7)
Generate MIDI from the drums-only stem. Select the Genre closest to your song. Click Open Last Result in Editor after converting.

STEP 3 → MIDI Editor (Tab 6)
Clean up the MIDI. Use Reclassify mode for wrong instruments. Use 1–8 hotkeys to place notes while listening. Set dynamics with the Velocity Lane.

STEP 3.5 → Track Preview (Tab 11) (optional but recommended)
Watch your chart as falling notes exactly as in Paradiddle.

STEP 4 → Song Tester (Tab 10)
Verify sync before converting. False positives may appear after manual edits — confirm in-game.

STEP 5 → Asset Manager (Tab 9) (optional)
Auto-fetch metadata, crop album art to 1:1, trim a 15s preview clip.

STEP 6 → Single Song Creator (Tab 1)
Combine everything into a `.rlrr` file. Enable Also save as .zip for a shareable archive.

STEP 7 → Deploy

PC: `Documents\Paradiddle\Songs\`
Quest (USB): Click 📲 Push to Quest (requires `adb.exe`)
Quest (manual): `Internal Shared Storage\Paradiddle\Songs\`
---
Setup

⚠️ FFmpeg — Required

Download [ffmpeg-release-essentials.zip from gyan.dev/ffmpeg/builds]

Extract to `C:\ffmpeg`

Add `C:\ffmpeg\bin` to Windows System PATH

Verify: open Command Prompt → `ffmpeg -version`

YouTube → FLAC — yt-dlp Required

Download `yt-dlp.exe` from [github.com/yt-dlp/yt-dlp/releases/latest] and place next to `ParaKit.exe`. Keep Auto-update yt-dlp checked.

Push to Quest — ADB Required

Download Android SDK Platform Tools, extract, place `adb.exe` next to `ParaKit.exe`.

One-time Quest setup: Meta app → Menu → Devices → [headset] → Developer Mode → On. Plug in USB, accept debugging prompt inside headset.

GPU Acceleration (Stem Splitter)

GPU	Status

NVIDIA GTX 10 – RTX 40 series	✅ Full GPU (~30s per song)

NVIDIA RTX 50-series	⚠️ CPU only — PyTorch support pending

AMD / Intel	🖥️ Always CPU — Demucs requires CUDA (NVIDIA-exclusive)

---

MIDI Editor Quick Reference

1–8 Note Hotkeys

Key	Lane	Key	Lane

`1`	Kick	`5`	Ride

`2`	Snare	`6`	Tom 1

`3`	Hi-Hat	`7`	Tom 2

`4`	Crash	`8`	Floor Tom

Place at playhead (playing) or last canvas click (paused). Snap to Grid applies.

Keyboard Shortcuts

Key	Action

`P`	Play / pause

`S`	Stop

`T`	Tap offset

`B`	Tap BPM for last tempo entry

`D`	Place marker

`Middle-click`	Place marker at position

`Ctrl+Z / Y`	Undo / Redo

`Ctrl+C / V`	Copy / Paste notes

`Ctrl+Q`	Quantize to 16th grid

`Ctrl+scroll`	Zoom

`Delete`	Remove selected notes/markers

Velocity & Dynamics

Range	Type	Visual

1–39	Ghost note	Hollow outline

40–114	Normal	Solid fill

115–127	Accent	Solid + white outline

Edit Tools

⊞ Quantize — snap to 16th grid

⧉/⧈ Copy/Paste — relative positions, pastes at playhead

× Dedup — remove stacked duplicate notes

↻ Repeat — tile selection once after itself

🥁 Flam — grace note (vel 30) 30ms before each selected note

---

Audio Format Guide

> ⚠️ Use `.flac` or `.wav` whenever possible. Converting MP3 → FLAC does **not** recover quality.

Format	Notes

`.flac`	Best — lossless, compressed

`.wav`	Lossless, larger files

`.mp3`	Accepted but degrades stem/MIDI quality

---

Paradiddle MIDI Note Mapping

MIDI Notes	Instrument

35, 36	Kick Drum

37, 38, 40	Snare

41, 43	Floor Tom

42, 44, 46	Hi-Hat

45, 47	Tom 2

48, 50	Tom 1

49, 55, 57	Crash

51, 53, 59	Ride

---

Common Problems

Problem	Fix

Notes out of sync	Run Song Tester; use .ogg not MP3

Wrong instrument	Reclassify mode in MIDI Editor

Toms missing	Add manually or Reclassify — unreliable

Stem Splitter fails	FFmpeg not on PATH

Stem Splitter slow	Normal for AMD/Intel and RTX 50-series

YouTube fails	Check yt-dlp next to exe; Auto-update on

Push to Quest fails	Accept USB debugging prompt in headset

App crashed silently	Check `parakit_crash.txt` next to exe

Zip missing files	Confirm conversion succeeded first

Drag/drop broken	Use Browse buttons

What's New in v3.5.0

🎨 Asset Manager (Tab 9)

Auto-Fetch Metadata — searches MusicBrainz for title/artist/album and iTunes for cover art. One click fills Song Creator fields. Cover art can be overridden by manually browsing in Song Creator — an indicator shows when art came from auto-fetch.

Album Art Cropper — crops any image to a centered 1:1 square at 256/512/1024px. Paradiddle requires square art.

Preview Audio Trimmer — exports any clip as `.ogg` (~15s recommended) for the Paradiddle song selection menu.

📲 Push to Quest (ADB)

📲 Push to Quest button in Song Creator sends the converted song folder directly to a connected Meta Quest via USB. No SideQuest or file manager needed.

Requires `adb.exe` placed next to `ParaKit.exe` (download here).

Quest one-time setup: enable Developer Mode in the Meta app, plug in USB, accept the debugging prompt inside the headset.

📦 Zip Output

Also save as .zip toggle in Song Creator automatically zips the output folder after conversion.

Optional Zip To folder — leave blank to save the zip next to the output folder.

Ready-to-share archive for ParadiddleDB or community upload.

👻 Ghost Overlay (MIDI Editor)

Load a second MIDI file as faded background notes in the piano roll.

Ideal for difficulty scaling — chart Expert, then load it as a ghost while charting Hard or Medium.

Opacity slider (10–60%). Non-interactive — ghost notes cannot be clicked or moved.

Ghost & Accent Visual Distinction (MIDI Editor)

Ghost notes (vel < 40) — hollow outline, no fill. Matches Paradiddle's in-game hollow note appearance.

Accent notes (vel ≥ 115) — solid fill + white outline.

Normal notes (vel 40–114) — solid fill as before.

🧪 Custom Isolation Split — Stem Splitter (BETA)

Isolate individual drum parts (Kick, Snare, Hi-Hat, Toms, Cymbals) as separate `.ogg` files using the `htdemucs\_6s` model.

> ⚠️ \*\*BETA — results are NOT perfect.\*\* Bleed between instruments is expected. \*\*Not recommended as input for Auto MIDI generation\*\* — use the standard drums-only stem for that. Best use: load isolated stems into the MIDI Editor for per-lane note verification.
Selecting all 5 parts simultaneously reverts to the standard split automatically.

🛡 Global Crash Handler

Fatal crashes now show a user-friendly dialog and write `parakit\_crash.txt` next to the exe.

`parakit\_debug.log` written on every launch for troubleshooting.

Bug Fixes

Extra kick note appearing on canvas clicks — root binding conflict fixed (`<Key-1>` format)

Hotkeys 3, 4, 5 broken — same fix

Layered audio playing multiple copies simultaneously — stop-before-play added

Mixer popup floating over other tabs / visible on desktop when minimized — fixed with `transient()` Toplevel

Status bar / keyboard shortcut legend disappeared — layout fixed

Pause/resume broken in layered mode — all stem channels handled correctly

Cyan listed in markers help but not in menu — corrected to Sky Blue

---
Tab Overview

#	Tab	Purpose

1	Single Song Creator	Convert MIDI + audio into a `.rlrr` Paradiddle chart

2	Audio to .ogg Converter	Convert audio to .ogg format

3	Create Multiple Songs	Batch convert multiple songs

4	Stem Splitter	AI separation — drums vs backing track

5	Audio → MIDI	Auto-detect drum hits from audio

6	MIDI Editor	Edit, clean up, and build drum MIDI charts

7	Sheet Music → MIDI	Convert MusicXML drum charts to MIDI

8	YouTube → FLAC	Download YouTube audio as FLAC

9	Asset Manager	Metadata, album art, preview clips

10	Song Tester	Verify BPM and sync

11	Track Preview	Watch chart as falling notes

12	Quick Start & FAQ	Built-in guide and troubleshooting

---

Changelog

Version	Summary

v3.5.0	Asset Manager, auto-metadata, ADB Push to Quest, zip output, ghost overlay, ghost/accent visual, custom stem isolation (BETA), crash handler, major bug fixes

v3.3.2	Multi-stem workspace, layered audio, 1-8 hotkeys, flam, markers, velocity lane, quantize, copy/paste, dedup, repeat, YouTube tab, auto-updater

v3.3.0	YouTube FLAC, auto-updater, velocity lane, edit tools, markers, notes fill row height

v3.2.0	Sheet Music → MIDI, rubber-band multi-select, rename to ParaKit

v3.1.0	Multi-select, playback speed, loop, project save/load

v3.0.0	ParaKit rebrand, dark theme, genre presets

---

*Created by Micah P.G. — ParaKit v3.3.0 — For the Paradiddle Community*# ParaKit---Releases

All in one tool built for Paradiddle to make it easier for beginners or people who just don't want to use other audio software that could be confusing or frustrating for some (me)
