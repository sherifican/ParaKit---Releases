# ParaKit for Paradiddle / Paradiddle VR
### Custom Song Creator & All-in-One Tool — v3.3.0
*App is a work in progress, I will release updates as needed as frequently as possible, thank you*

---

Compatible with **Paradiddle (PC)** and **Paradiddle VR (Meta Quest 3)**
Built for use with any supported e-drum kit or the in game kit

> 📖 Refer to this README whenever you need help. The **Quick Start & FAQ** tab (Tab 11) inside the app also covers common questions and fixes.

> ℹ️ First launch may take a moment — this is normal. Wait for the app to fully load before clicking anything. It opens faster after the first launch.

---

## Is ParaKit Right for You?

If you're already experienced with MIDI charting and have your own workflow using tools like Reaper, Audacity, or similar — ParaKit probably isn't your primary tool. That said, parts of it may still save you steps: the Song Creator and batch converter, Stem Splitter, Sheet Music → MIDI, and Track Preview can slot into an existing workflow without replacing it.

If you're new to charting, don't know where to start, or find dedicated audio/MIDI software intimidating — ParaKit is probably exactly what you're looking for. It handles the full pipeline in one place, with a built-in guide and enough automation to get a playable chart without prior experience.

---

## Quick Start

**The full recommended workflow:**

**STEP 1 → Stem Splitter tab**
Split your song into a drums-only track and a backing track. Use `.flac` or `.wav` source files for best quality *(see Audio Format section below)*.

**STEP 2 → Audio → MIDI tab** *(skip if you already have a MIDI file)*
Convert the drums-only track into a MIDI file. Select the Genre that best matches your song. Think of this as a rough draft — it won't be perfect. Click **"Open Last Result in Editor"** after converting to jump straight to the MIDI Editor.

&emsp;— *OR* —

**STEP 2 → Sheet Music → MIDI tab (Tab 7)** *(if you have sheet music)*
Convert a MusicXML drum chart into a 1:1 accurate MIDI file. No detection errors, no cleanup needed — what's written is what you get. Download `.mxl` directly from [MuseScore.com](https://musescore.com) or export `.xml` from any notation software. Full band scores work fine — ParaKit finds the drum part automatically.

**STEP 3 → MIDI Editor tab** *(always do this)*
Review and clean up the generated MIDI. Fix misclassified notes using **Reclassify mode**, remove false hits, add missing ones. Use Reclassify — it's almost always the fastest fix. Shift+drag on empty space to rubber-band select multiple notes.

**STEP 3.5 → Track Preview tab (Tab 9, optional but recommended)**
Watch your chart fall exactly as it will in Paradiddle, synced to your audio.

**STEP 4 → Song Tester tab** *(recommended before converting)*
Check that your MIDI and audio are properly synced. Manual edits may produce some false-positive warnings — always confirm in-game.

**STEP 5 → Single Song Creator tab**
Combine your MIDI + audio into a `.rlrr` song file. Use **Save Project** to save all your file paths and settings for next time.

**STEP 6 → Copy the output folder to your Paradiddle Songs directory:**
- **PC:** `Documents\Paradiddle\Songs\`
- **Quest:** `Internal Shared Storage\Paradiddle\Songs\`

---

## Audio Format — FLAC / WAV vs MP3

The format of your source audio directly affects stem split and MIDI quality.

> ⚠️ **Use `.flac` or `.wav` whenever possible.** MP3 is a lossy format — audio data is permanently discarded during compression. Even a 320 kbps MP3 has less information than the original recording, which reduces stem separation quality and MIDI detection accuracy.

| Format | Notes |
|--------|-------|
| `.flac` | Lossless + compressed. **Best choice for most users.** |
| `.wav` | Lossless + uncompressed. Larger files, identical quality to FLAC. |
| `.mp3` | Accepted but not recommended. Results may be less accurate. |

> ℹ️ **Converting MP3 → FLAC does NOT improve quality.** The data lost during MP3 encoding is gone permanently. Source lossless files from the start — [Bandcamp](https://bandcamp.com) often offers FLAC downloads directly from artists.

**New in v3.3.0:** Use the **YouTube → FLAC tab** (Tab 10) to download audio from YouTube directly as FLAC — the ideal format for the Stem Splitter.

---

## Setup — Read Before Launching

### ⚠️ Install FFmpeg Before Using the App — Required

FFmpeg is a free tool that ParaKit needs for audio conversion and stem splitting. Without it, the Stem Splitter will fail and audio conversion will not work.

**How to install FFmpeg:**
1. Go to: [https://www.gyan.dev/ffmpeg/builds/](https://www.gyan.dev/ffmpeg/builds/)
2. Download **"ffmpeg-release-essentials.zip"**
3. Extract the zip to a permanent location — recommended: `C:\ffmpeg`
4. Open the Start Menu and search for **"environment variables"**
5. Click **"Edit the system environment variables"**
6. Click **"Environment Variables"** at the bottom
7. Under **"System variables"** find **"Path"** and double-click it
8. Click **"New"** and add: `C:\ffmpeg\bin`
9. Click OK on all windows to save

To verify: open Command Prompt and type `ffmpeg -version`. If it prints version info, you're good. If it says "not recognized", repeat the steps above.

### YouTube → FLAC Tab — yt-dlp Required

The YouTube → FLAC tab requires **yt-dlp.exe** placed in the same folder as `ParaKit.exe`.

Download it free from: [https://github.com/yt-dlp/yt-dlp/releases/latest](https://github.com/yt-dlp/yt-dlp/releases/latest)](https://github.com/yt-dlp/yt-dlp/releases/download/2026.03.17/yt-dlp_arm64.exe)

> ℹ️ The tab has an **Auto-update yt-dlp** toggle — keep this on. YouTube occasionally changes its API and yt-dlp needs to update to stay compatible.

### GPU Acceleration (Stem Splitter)

| GPU | Status |
|-----|--------|
| NVIDIA GTX 10-series through RTX 40-series | ✅ Full GPU acceleration (~30s per song) |
| NVIDIA RTX 50-series (5070, 5080, 5090) | ⚠️ CPU only for now — PyTorch support coming |
| AMD and Intel GPUs | 🖥️ CPU only — Demucs requires CUDA (NVIDIA-exclusive) |

CPU times are typically **45s to ~1m30s** depending on your processor.

---

## Audio → MIDI — Tips & Genre Guide

The auto-detector gives you a strong starting point, not a finished chart. Always clean up the output in the MIDI Editor. **Use Reclassify mode first** — a misclassified note is always better than a missing one because the timing is already correct.
The Audio to MIDI generator will sometimes place the notes slightly off the point they should be, use the quantify feature either en-mass or individually to fix, or use the snap/drag manually method.

### Genre Presets

| Genre | Notes |
|-------|-------|
| Auto | Best starting point for most songs |
| No Adjustment | Raw defaults, useful for manual tuning |
| Pop / Pop-Punk & Rock | Kick threshold raised, snare more sensitive, tom filters loosened |
| Metal / Hard Rock / Post-Hardcore | Snare detection much more sensitive to handle guitar bleed on noisy stems |

### Instrument-Specific Notes

- **Toms** — unreliable regardless of preset. Use Reclassify mode or add manually. Turn off Snap to Grid for fast tom fills.
- **Ride** — auto-detection unreliable. Leave ride detection OFF. Generate normally — ride hits will appear as hi-hats or crashes. Use Reclassify to change them.
- **Kicks** — ~90% accurate for most songs. If too many false kicks, disable kick detection and add manually or use Reclassify.

### Rapid Roll Fix
If a fast snare or tom roll shows the first hit correctly but the rest appear as hi-hats/crashes — the timing is correct, just reclassify. If you hear a roll but see a total note gap, lower the dedup gap and regenerate, or add notes manually with Snap to Grid off.

---

## Sheet Music → MIDI — Tips

Converts a MusicXML drum chart into a Paradiddle-ready MIDI file. The result is 1:1 accurate — no detection errors, no guesswork.

**Where to find drum sheet music:**
- [MuseScore.com](https://musescore.com) — search for your song and download the `.mxl` file. Many scores require a Pro subscription (~$39.99/year). Free scores are available and marked on the site.
- The Sheet Music tab has a built-in search box that opens MuseScore.com with the drumset filter pre-applied.

**Finding your audio offset (in-app method):**
1. Open the MIDI Editor and load your drums-only stem in **Playback Audio — Drums Only**
2. Look at the waveform strip below the piano roll — the first spike is your first drum hit
3. Slow to 0.3x or pause near the spike
4. Press **T** at the moment you hear it (or while paused at that position) — the offset field updates automatically
5. Re-convert — or hit **Apply Offset to All Notes** in the MIDI Editor

---

## MIDI Editor — Tips

### Reclassify Mode
Click any note to change its instrument without moving it. With multiple notes selected, reclassifies all at once. This is the fastest cleanup tool — use it first.

### Multi-Select
| Action | Result |
|--------|--------|
| Shift + drag on empty space | Rubber-band select all notes in the area |
| Ctrl + left-click | Toggle individual notes in/out of selection |
| Delete / Backspace | Delete all selected notes and/or markers |
| Drag a selected note | Moves the entire selection together |

### Keyboard Shortcuts
| Key | Action |
|-----|--------|
| `P` | Play / pause |
| `S` | Stop |
| `T` | Tap to mark offset |
| `B` | Tap BPM for last tempo map entry |
| `D` | Place a marker at playhead or last click |
| `Middle-click` | Place a marker at clicked position |
| `Ctrl + Z` | Undo |
| `Ctrl + Y` | Redo |
| `Ctrl + C` | Copy selected notes |
| `Ctrl + V` | Paste at playhead or last click |
| `Ctrl + Q` | Quantize selected (or all) to 16th grid |
| `Ctrl + scroll` | Zoom in / out |
| `Delete / Backspace` | Delete selected notes and/or markers |

### Edit Tools (Toolbar)
- **⊞ Quantize** — snaps selected notes to the nearest 16th-note grid. If nothing selected, quantizes all. Use when auto-detected notes land slightly off-beat.
- **⧉ Copy / ⧈ Paste** — copies selected notes, pastes at playhead. Pasted notes are automatically selected. Paste can be repeated.
- **× Dedup** — removes exact duplicate notes at the same time and lane. Run after generating to clean stacked duplicates.
- **↻ Repeat** — tiles the selected pattern once immediately after itself. Useful for building out a chart from a detected verse or fill.

### Velocity Lane
Open by checking **Tempo Map + Velocity Lane** in the editor. Each bar in the lane represents one note — taller = louder (1–127). In Paradiddle this controls accent and ghost note dynamics.

| Preset | Velocity | Use |
|--------|----------|-----|
| Ghost | 30 | Very quiet, barely audible |
| Normal | 100 | Standard playing |
| Accent | 120 | Loud, prominent hits |

Click a bar to set its velocity. The slider + **Apply to Selected** sets a precise value for selected notes.

### Markers
Place markers with **D** (at playhead) or **middle-click** anywhere on the canvas. Each marker is a full-height vertical line. Click the triangle handle in the header to select and drag. Labels and colors are set in the **📍 Markers** popup button (right column).

### Tempo Map
If notes are in sync at the start but drift increasingly out of sync after a certain point, add a tempo map entry:
1. Find where drift starts — use 0.3x speed + T key or waveform
2. Find the new BPM — rubber-band select notes in that section and click **"BPM from Selection"**, or tap with **B key** or the Tap button
3. Enter time + BPM and click **Apply Tempo Map**
4. Fully undoable with Ctrl+Z

---

## YouTube → FLAC (Tab 10)

Downloads audio from YouTube and converts it to **FLAC** — the best format for Stem Splitter input.

**Requirements:**
- `yt-dlp.exe` in the same folder as `ParaKit.exe` — download from [github.com/yt-dlp/yt-dlp/releases](https://github.com/yt-dlp/yt-dlp/releases/latest)
- `ffmpeg.exe` — ships with ParaKit

**Usage:**
1. Paste a YouTube URL
2. Choose an output folder
3. Select format (FLAC recommended)
4. Keep **Auto-update yt-dlp** checked
5. Click **Download & Convert**

> ⚠️ Only download content you have the legal right to use. Age-restricted and private videos cannot be downloaded.

---

## Song Creator — Project Files

- **💾 Save Project** — saves all Song Creator fields to a `.parakit` file: MIDI, audio, cover, title, artist, difficulty, BPM, offset, output folder
- **📂 Load Project** — restores all those fields from a saved file
- **÷2 / ×2 buttons** — halve or double the detected BPM if auto-detect gives half or double the correct value

> ⚠️ **BPM auto-detect requires a drums-only stem.** Running it against a full mix or backing track almost always gives half the real BPM. Use the Stem Splitter first, or switch to Manual BPM and enter the correct value.

---

## Common Problems & Fixes

| Problem | Fix |
|---------|-----|
| Notes out of sync in-game | Run Song Tester for recommended BPM/offset. Convert audio to .ogg — MP3 can cause drift. |
| Sheet Music → MIDI: 0 notes | Drum staff may not be set to Percussion in your notation software. |
| Too many crashes / wrong instrument | Use Reclassify mode in the MIDI Editor. |
| Toms missing | Tom detection is unreliable — add manually or Reclassify. |
| Kicks missing or too many | Too many: disable kick detection. Too few: enable it or add manually. |
| Fast roll — only first hit shows | Timing correct — Reclassify the rest. |
| Stem Splitter fails | FFmpeg not installed or not on PATH. See Setup section. |
| Stem Splitter is slow | Normal on AMD/Intel — CPU only. RTX 50-series also CPU for now. |
| YouTube download fails | Check yt-dlp is placed next to ParaKit.exe and auto-update is on. |
| App crashes on launch | ParaKit.exe must stay in its original folder. Windows Defender may delay first launch — this is normal. |
| Drag and drop not working | Use the Browse buttons as a fallback — they always work. |

---

## Paradiddle MIDI Note Mapping Reference

| MIDI Notes | Instrument | Paradiddle |
|-----------|-----------|------------|
| 35, 36 | Kick Drum | BP_Kick_C |
| 37 | Rim Click / Side Stick | BP_Snare_C |
| 38, 40 | Snare Drum | BP_Snare_C |
| 41, 43 | Floor Tom | BP_FloorTom_C |
| 42, 44 | Closed / Pedal Hi-Hat | BP_HiHat_C |
| 46 | Open Hi-Hat | BP_HiHat_C |
| 45, 47 | Low Tom | BP_Tom2_C |
| 48, 50 | Mid Tom | BP_Tom1_C |
| 49, 55 | Crash / Splash Cymbal | BP_Crash15_C |
| 51, 53 | Ride Cymbal / Bell | BP_Ride17_C |
| 57 | Crash Cymbal (17") | BP_Crash17_C |
| 59 | Ride Cymbal (20") | BP_Ride20_C |

*Notes not in the above list are silently ignored during conversion.*

---

## What's New — v3.3.0

### New Tab: YouTube → FLAC (Tab 10)
- Download audio from YouTube and convert to FLAC, WAV, or MP3 directly in-app
- FLAC by default — best quality for Stem Splitter input
- Auto-updates yt-dlp before each download to stay compatible with YouTube
- Real-time progress log, cancel button, format selection
- Requires yt-dlp.exe placed next to ParaKit.exe

### Auto-Update
- ParaKit now checks for new versions on launch and prompts to update
- Downloads and replaces the exe automatically — no manual download needed
- Fully silent if already on the latest version

### MIDI Editor
- **Notes fill row height** — new display toggle that stretches each note to fill its full lane row. Note Size slider controls width only in this mode. Useful for dense charts and piano-roll style viewing.
- **Quantize** (⊞ / Ctrl+Q) — snap selected or all notes to the nearest 16th-note grid
- **Copy / Paste** (⧉⧈ / Ctrl+C/V) — copy selected notes, paste at playhead or last click. Pasted notes are automatically selected.
- **Dedup** (×) — remove exact duplicate stacked notes silently created by auto-detection
- **Repeat** (↻) — tile the selected pattern once after itself, snapped to nearest beat
- **Velocity Lane** — bar graph inside the Tempo Map section showing per-note velocity. Click/drag to set, quick presets (Ghost 30 / Normal 100 / Accent 120), slider + Apply to Selected. Velocity maps to accent/ghost note dynamics in Paradiddle.
- **Markers** — place full-height vertical time markers with D key or middle-click. Color-code and label them via the 📍 Markers popup. Select and drag via header triangle handles.
- Ctrl+scroll to zoom already existed — now documented in keyboard shortcuts

### Bug Fixes
- Fixed reclassify menu closing the entire editor after repeated use — `tk.Menu` widgets were leaking and exhausting Tkinter's widget table
- Fixed SongMaker references throughout — all updated to ParaKit

---

## Changelog

| Version | Summary |
|---------|---------|
| **v3.3.0** | YouTube → FLAC tab, auto-updater, velocity lane, quantize, copy/paste, dedup, repeat, full-height notes, markers |
| v3.2.4 | Snap to nearby notes, BPM from selection, B key, tempo map improvements, note display toggles, zoom fix, grid ruler fix |
| v3.2.3 | Note offset field, tempo map, drift fix, timer fix |
| v3.2.2 | Pitch-preserving slow playback, waveform display, T key offset tap, drag undo fix |
| v3.2.0 | Sheet Music → MIDI tab, rubber-band multi-select fix, loop color fix |
| v3.1.0 | Multi-select, keyboard shortcuts, playback speed, loop section, project save/load |
| v3.0.0 | Renamed from SongMaker to ParaKit, new dark theme, genre presets reworked |
| v2.9.6 | Genre selector, kick detection on by default, Quick Start & FAQ tab |
| v2.8.3 | MIDI Editor tab (new), Song Tester balance check |

---

*Created by Micah P.G. — ParaKit v3.3.0 — For the Paradiddle Community*# ParaKit---Releases
All in one tool built for Paradiddle to make it easier for beginners or people who just don't want to use other audio software that could be confusing or frustrating for some (me)
