# ParaKit for Paradiddle / Paradiddle VR

### Custom Song Creator & All-in-One Tool — v3.5.1

*App is a work in progress — updates released as frequently as possible. Thank you for your patience.*

> ⬇️ **ALT DOWNLOAD:** [https://limewire.com/d/svTK9#fqZoG5vUjc](https://limewire.com/d/svTK9#fqZoG5vUjc)

> 📦 **v3.5+ ships with all requirements included in the main .zip download** — no separate installs needed.

The goal of this project is to make MIDI charting for Paradiddle as accessible as possible — no paywalls, no confusing professional audio software, no barrier to entry. If you've ever wanted to play a song that isn't in the game, this tool is for you.

Compatible with **Paradiddle (PC)** and **Paradiddle VR (Meta Quest 3)**
Built for use with any supported e-drum kit or the in-game virtual kit

> 📖 The **Quick Start & FAQ tab (Tab 12)** inside the app covers everything in detail.

> ℹ️ First launch may take a moment. The app opens faster after the first launch.

---

## Is ParaKit Right for You?

If you're already experienced with MIDI charting and have your own workflow using tools like Reaper, Audacity, or similar — ParaKit probably won't replace your primary methods. That said, parts of it may still save you steps: the Song Creator, Stem Splitter, Sheet Music → MIDI, YouTube → FLAC, Asset Manager, and Track Preview can all slot into an existing workflow without replacing it.

If you're new to charting, or find dedicated audio/MIDI software difficult, confusing, or just more than you need — ParaKit handles the full pipeline in one place with enough automation to get a playable chart without prior experience.

---

## Tab Overview

| # | Tab | What it does |
|---|-----|-------------|
| 1 | **Single Song Creator** | Convert MIDI + audio into a `.rlrr` chart |
| 2 | Audio to .ogg Converter | Convert audio to .ogg |
| 3 | Create Multiple Songs | Batch convert |
| 4 | **Stem Splitter** | AI-separate drums from backing |
| 5 | Audio → MIDI | Auto-detect drum hits, generate MIDI |
| 6 | **MIDI Editor** | Edit and build drum charts visually |
| 7 | Sheet Music → MIDI | Convert MusicXML charts to MIDI |
| 8 | YouTube → FLAC | Download YouTube audio as lossless FLAC |
| 9 | **Asset Manager** | Metadata, album art, preview clips |
| 10 | Song Tester | Verify BPM and sync |
| 11 | Track Preview | Watch chart as falling notes |
| 12 | Quick Start & FAQ | Built-in guide and troubleshooting |

---

## Quick Start

**STEP 1 → Stem Splitter (Tab 4)**

Split your song into drums-only and backing. Use `.flac` or `.wav` for best quality. Use **YouTube → FLAC (Tab 8)** if you need a lossless source.

**STEP 2 → Audio → MIDI (Tab 5)**

Convert the drums-only track into MIDI. Select the Genre closest to your song. Click **"Open Last Result in Editor"** after converting.

— *OR* —

**STEP 2 → Sheet Music → MIDI (Tab 7)**

Convert a MusicXML drum chart to 1:1 accurate MIDI. Download `.mxl` from [MuseScore.com](https://musescore.com).

**STEP 3 → MIDI Editor (Tab 6)**

Clean up the MIDI. Use **Reclassify mode** for wrong instruments. Use **1–8 hotkeys** to place notes while listening. Set dynamics in the **Velocity Lane**.

**STEP 3.5 → Track Preview (Tab 11)** *(optional but recommended)*

Watch your chart fall exactly as it will in Paradiddle.

**STEP 4 → Song Tester (Tab 10)**

Verify sync. False positives may appear after manual edits — always confirm in-game.

**STEP 5 → Asset Manager (Tab 9)** *(optional)*

Auto-fetch metadata, crop album art to 1:1, trim a 15-second preview clip.

**STEP 6 → Single Song Creator (Tab 1)**

Combine MIDI + audio into a `.rlrr` file. Enable **Also save as .zip** for a shareable archive.

**STEP 7 → Deploy**

- **PC:** `Documents\Paradiddle\Songs\`
- **Quest (USB):** Click **📲 Push to Quest** *(requires adb.exe — see Setup)*
- **Quest (manual):** `Internal Shared Storage\Paradiddle\Songs\`

---

## Setup

> ✅ **ffmpeg, yt-dlp, and adb are all included in the ParaKit release zip.** Extract the full zip — do not move `ParaKit.exe` out of its folder. Everything needs to stay together in the same directory.

### FFmpeg — Included

`ffmpeg.exe` and `ffprobe.exe` are included next to `ParaKit.exe` — no install or PATH setup needed. **Do not move `ParaKit.exe` out of its folder** or audio conversion and the Stem Splitter will stop working.

### YouTube → FLAC — yt-dlp Included

`yt-dlp.exe` is included next to `ParaKit.exe`. Keep **Auto-update yt-dlp** checked in the YouTube tab — YouTube occasionally changes its API and yt-dlp needs to update to stay compatible.

Manual download if needed: [github.com/yt-dlp/yt-dlp/releases/latest](https://github.com/yt-dlp/yt-dlp/releases/latest)

### Push to Quest — ADB Included

The `platform-tools` folder is included in the zip. It contains `adb.exe`, `AdbWinApi.dll`, and `AdbWinUsbApi.dll` — **all three files must be in the same folder as `ParaKit.exe`** for Push to Quest to work.

Manual download if needed: [Android SDK Platform Tools](https://developer.android.com/tools/releases/platform-tools)

**One-time Quest setup:**

1. Meta app → Menu → Devices → [headset] → **Developer Mode → On**
2. Plug Quest into PC via USB
3. Put on the headset — tap **Allow** on the USB debugging prompt that appears

### Album Art Cropper — Pillow Included

The Asset Manager album art cropper uses **Pillow** (image library). It is bundled inside `ParaKit.exe` — no separate install needed.

### GPU Acceleration — Stem Splitter

| GPU | Status |
|-----|--------|
| NVIDIA GTX 10-series through RTX 40-series | ✅ Full GPU acceleration (~30s per song) |
| NVIDIA RTX 50-series | ⚠️ CPU only — PyTorch support coming |
| AMD and Intel GPUs | 🖥️ CPU only — Demucs requires CUDA (NVIDIA-exclusive) |

CPU times: typically **45 seconds to ~1m30s**.

---

## Audio Format Guide

> ⚠️ Use `.flac` or `.wav` whenever possible. Converting MP3 → FLAC does **not** recover quality — that data is gone permanently.

| Format | Notes |
|--------|-------|
| `.flac` | Lossless + compressed. Best choice. |
| `.wav` | Lossless + uncompressed. Larger files, same quality. |
| `.mp3` | Accepted but not recommended. |

Use the **YouTube → FLAC tab (Tab 8)** in the app to download lossless audio directly — this is the recommended source. [Bandcamp](https://bandcamp.com) is a good alternative if you own the release, as it often offers FLAC downloads from artists.

---

## Stem Splitter

### Standard Split

Outputs **DRUMS ONLY** and **BACKINGS** as `.ogg` files.

- **htdemucs** — fastest, great quality *(recommended)*
- **htdemucs_ft** — slower, slightly more accurate

### Custom Isolation Split *(🧪 BETA)*

Isolates individual drum parts — Kick, Snare, Hi-Hat, Toms, Cymbals — each as a separate `.ogg` file. Uses `htdemucs_6s` automatically. Optional Backings split.

> ⚠️ **BETA — results are not perfect.** Bleed between instruments is expected. Not recommended for Auto MIDI input. Best use: load isolated stems into the MIDI Editor for per-lane note verification.

Selecting all 6 stems at once automatically reverts to the standard split.

### 🥁 DrumSep — Drum Component Separation *(🧪 BETA)*

Separates a **drums-only stem** into 4 individual components: **Kick, Snare, Cymbals, Toms**. Uses a specialized drum separation model (not demucs) trained specifically for drum isolation.

> ⚠️ **Run Standard Split first** to get a drums-only stem, then run DrumSep on that result. Do not run it on a full mix.

**First-time setup:** Enable DrumSep → click **↓ Download Model** (~200MB, one-time). Downloads from GitHub first, Google Drive as fallback. Stored in `drumsep_model\` next to `ParaKit.exe`.

**Output:** `songname_kick.ogg`, `songname_snare.ogg`, `songname_cymbals.ogg`, `songname_toms.ogg` in separate subfolders.

**Best use:** Load each stem into a MIDI Editor stem slot. The kick stem shows only kick transients in the waveform — makes note placement much more precise per lane.

---

## Audio → MIDI — Genre Guide

The auto-detector gives a strong starting point, not a finished chart. Notes may land slightly off-beat — use **Quantize** to fix in bulk, or drag manually with Snap to Grid off.

| Genre | Notes |
|-------|-------|
| Auto | Best starting point for most songs |
| No Adjustment | Raw defaults |
| Pop / Pop-Punk & Rock | Kick threshold raised, snare more sensitive |
| Metal / Hard Rock / Post-Hardcore | Snare detection very sensitive for noisy stems |

**Instrument notes:**

- **Toms** — unreliable. Use Reclassify or add manually. Turn off Snap to Grid for fast fills.
- **Ride** — leave detection OFF. Reclassify hi-hats/crashes that should be ride.
- **Kicks** — ~90% accurate. Too many: disable detection. Too few: enable or add manually.

---

## MIDI Editor

### 1–8 Note Hotkeys

| Key | Lane | Key | Lane |
|-----|------|-----|------|
| `1` | Kick | `5` | Ride |
| `2` | Snare | `6` | Tom 1 |
| `3` | Hi-Hat | `7` | Tom 2 |
| `4` | Crash | `8` | Floor Tom |

Hotkeys place at the **playhead** (playing) or **last canvas click** (paused). Snap to Grid applies.

### Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `P` | Play / pause |
| `S` | Stop |
| `T` | Tap offset |
| `B` | Tap BPM for last tempo entry |
| `D` | Place marker |
| `Middle-click` | Place marker at position |
| `1` – `8` | Place note in lane |
| `Ctrl + Z / Y` | Undo / Redo |
| `Ctrl + C / V` | Copy / Paste |
| `Ctrl + Q` | Quantize to 16th grid |
| `Ctrl + scroll` | Zoom |
| `Delete` | Remove selected notes/markers |

### Edit Tools

| Tool | What it does |
|------|-------------|
| ⊞ Quantize | Snap to 16th-note grid |
| ⧉ / ⧈ Copy / Paste | Paste at playhead; pasted notes auto-selected |
| × Dedup | Remove stacked duplicate notes |
| ↻ Repeat | Tile selection once after itself |
| 🥁 Flam | Grace note (vel 30) 30ms before each selected note |

### Velocity — Ghost & Accent Notes

| Velocity | Type | Visual in Editor | Paradiddle |
|----------|------|-----------------|------------|
| 1–39 | Ghost note | Hollow outline | Quiet, subtle hit |
| 40–114 | Normal | Solid fill | Standard hit |
| 115–127 | Accent | Solid + white outline | Loud, prominent hit |

Open the **Velocity Lane** via the Tempo Map + Velocity Lane checkbox. Click/drag bars to set velocity. Quick presets: Ghost (30), Normal (100), Accent (120).

### Multi-Stem Audio

Load up to 4 stems. Radio button selects the active stem. **Single** or **Layered** playback mode. **🎚 Mixer** button opens per-stem volume controls.

> ⚠️ Layered mode at non-1.0x speed is CPU-intensive.

### Markers

**D** key or **middle-click** places a marker. Click the triangle handle in the header to select/drag. Color and label via the **📍 Markers** popup button.

### Ghost Overlay

Load a reference MIDI as faded background notes for charting multiple difficulties. Browse in the Display & Snap panel. Opacity slider 10–60%.

---

## Asset Manager (Tab 9)

**Auto-Fetch Metadata** — searches [MusicBrainz](https://musicbrainz.org) and iTunes. One click fills Song Creator fields. Cover art can be overridden by manually browsing a different image.

**Album Art Cropper** — crops any image to a centered 1:1 square. Output sizes: 256, 512 *(recommended)*, or 1024px.

**Preview Audio Trimmer** — exports a `.ogg` clip (~15 seconds) for the Paradiddle song selection menu.

---

## Song Creator — Output Options

- **Also save as .zip** — automatically zips the output folder after conversion
- **Zip To** — optional separate folder for zips; leave blank to save next to the output
- **📲 Push to Quest** — sends the converted folder directly to a connected Meta Quest via USB

---

## Common Problems

| Problem | Fix |
|---------|-----|
| Notes out of sync | Run Song Tester; use .ogg not MP3 |
| Wrong instrument | Reclassify mode in MIDI Editor |
| Toms missing | Unreliable — add manually or Reclassify |
| Stem Splitter fails | FFmpeg not on PATH |
| Stem Splitter slow | Normal for AMD/Intel and RTX 50-series |
| YouTube fails | Check yt-dlp is next to exe; Auto-update on |
| Push to Quest fails | Accept USB debugging prompt in headset |
| App crashed silently | Check `parakit_crash.txt` next to ParaKit.exe |
| Drag/drop broken | Use Browse buttons |

---

## Paradiddle MIDI Note Mapping

| MIDI Notes | Instrument | Paradiddle |
|-----------|-----------|------------|
| 35, 36 | Kick Drum | BP_Kick_C |
| 37, 38, 40 | Snare Drum | BP_Snare_C |
| 41, 43 | Floor Tom | BP_FloorTom_C |
| 42, 44, 46 | Hi-Hat | BP_HiHat_C |
| 45, 47 | Low Tom | BP_Tom2_C |
| 48, 50 | Mid Tom | BP_Tom1_C |
| 49, 55, 57 | Crash Cymbal | BP_Crash15_C / BP_Crash17_C |
| 51, 53, 59 | Ride Cymbal | BP_Ride17_C / BP_Ride20_C |

*Notes not in the above list are silently ignored.*

---

## Changelog

| Version | Summary |
|---------|---------|
| **v3.5.1** | DrumSep drum component separator, DPI awareness, ghost/accent visual fixes, layered audio sync & volume, stem switch during playback, velocity lane live redraw, beat ruler fix, collapsible help tab, auto-updater filter |
| **v3.5.0** | Asset Manager, auto-metadata, Push to Quest, zip output, Ghost Overlay, ghost/accent visuals, Custom Isolation Split (BETA), crash handler, major bug fixes |
| v3.3.2 | Multi-stem workspace, layered audio, 1-8 hotkeys, Flam, Markers, Velocity Lane, Quantize, Copy/Paste, Dedup, Repeat |
| v3.3.0 | YouTube → FLAC, auto-updater, edit tools, markers |
| v3.2.0 | Sheet Music → MIDI tab |
| v3.1.0 | Multi-select, playback speed, loop, project save/load |
| v3.0.0 | Renamed to ParaKit, dark theme |

---

*Created by Micah P.G. — ParaKit v3.5.1 — For the Paradiddle Community*# ParaKit for Paradiddle / Paradiddle VR

### Custom Song Creator & All-in-One Tool — v3.5.1

*App is a work in progress — updates released as frequently as possible. Thank you for your patience.*

> ⬇️ **ALT DOWNLOAD:** [https://limewire.com/d/svTK9#fqZoG5vUjc](https://limewire.com/d/svTK9#fqZoG5vUjc)

> 📦 **v3.5+ ships with all requirements included in the main .zip download** — no separate installs needed.

The goal of this project is to make MIDI charting for Paradiddle as accessible as possible — no paywalls, no confusing professional audio software, no barrier to entry. If you've ever wanted to play a song that isn't in the game, this tool is for you.

Compatible with **Paradiddle (PC)** and **Paradiddle VR (Meta Quest 3)**
Built for use with any supported e-drum kit or the in-game virtual kit

> 📖 The **Quick Start & FAQ tab (Tab 12)** inside the app covers everything in detail.

> ℹ️ First launch may take a moment. The app opens faster after the first launch.

---

## Is ParaKit Right for You?

If you're already experienced with MIDI charting and have your own workflow using tools like Reaper, Audacity, or similar — ParaKit probably won't replace your primary methods. That said, parts of it may still save you steps: the Song Creator, Stem Splitter, Sheet Music → MIDI, YouTube → FLAC, Asset Manager, and Track Preview can all slot into an existing workflow without replacing it.

If you're new to charting, or find dedicated audio/MIDI software difficult, confusing, or just more than you need — ParaKit handles the full pipeline in one place with enough automation to get a playable chart without prior experience.

---

## Tab Overview

| # | Tab | What it does |
|---|-----|-------------|
| 1 | **Single Song Creator** | Convert MIDI + audio into a `.rlrr` chart |
| 2 | Audio to .ogg Converter | Convert audio to .ogg |
| 3 | Create Multiple Songs | Batch convert |
| 4 | **Stem Splitter** | AI-separate drums from backing |
| 5 | Audio → MIDI | Auto-detect drum hits, generate MIDI |
| 6 | **MIDI Editor** | Edit and build drum charts visually |
| 7 | Sheet Music → MIDI | Convert MusicXML charts to MIDI |
| 8 | YouTube → FLAC | Download YouTube audio as lossless FLAC |
| 9 | **Asset Manager** | Metadata, album art, preview clips |
| 10 | Song Tester | Verify BPM and sync |
| 11 | Track Preview | Watch chart as falling notes |
| 12 | Quick Start & FAQ | Built-in guide and troubleshooting |

---

## Quick Start

**STEP 1 → Stem Splitter (Tab 4)**

Split your song into drums-only and backing. Use `.flac` or `.wav` for best quality. Use **YouTube → FLAC (Tab 8)** if you need a lossless source.

**STEP 2 → Audio → MIDI (Tab 5)**

Convert the drums-only track into MIDI. Select the Genre closest to your song. Click **"Open Last Result in Editor"** after converting.

— *OR* —

**STEP 2 → Sheet Music → MIDI (Tab 7)**

Convert a MusicXML drum chart to 1:1 accurate MIDI. Download `.mxl` from [MuseScore.com](https://musescore.com).

**STEP 3 → MIDI Editor (Tab 6)**

Clean up the MIDI. Use **Reclassify mode** for wrong instruments. Use **1–8 hotkeys** to place notes while listening. Set dynamics in the **Velocity Lane**.

**STEP 3.5 → Track Preview (Tab 11)** *(optional but recommended)*

Watch your chart fall exactly as it will in Paradiddle.

**STEP 4 → Song Tester (Tab 10)**

Verify sync. False positives may appear after manual edits — always confirm in-game.

**STEP 5 → Asset Manager (Tab 9)** *(optional)*

Auto-fetch metadata, crop album art to 1:1, trim a 15-second preview clip.

**STEP 6 → Single Song Creator (Tab 1)**

Combine MIDI + audio into a `.rlrr` file. Enable **Also save as .zip** for a shareable archive.

**STEP 7 → Deploy**

- **PC:** `Documents\Paradiddle\Songs\`
- **Quest (USB):** Click **📲 Push to Quest** *(requires adb.exe — see Setup)*
- **Quest (manual):** `Internal Shared Storage\Paradiddle\Songs\`

---

## Setup

> ✅ **ffmpeg, yt-dlp, and adb are all included in the ParaKit release zip.** Extract the full zip — do not move `ParaKit.exe` out of its folder. Everything needs to stay together in the same directory.

### FFmpeg — Included

`ffmpeg.exe` and `ffprobe.exe` are included next to `ParaKit.exe` — no install or PATH setup needed. **Do not move `ParaKit.exe` out of its folder** or audio conversion and the Stem Splitter will stop working.

### YouTube → FLAC — yt-dlp Included

`yt-dlp.exe` is included next to `ParaKit.exe`. Keep **Auto-update yt-dlp** checked in the YouTube tab — YouTube occasionally changes its API and yt-dlp needs to update to stay compatible.

Manual download if needed: [github.com/yt-dlp/yt-dlp/releases/latest](https://github.com/yt-dlp/yt-dlp/releases/latest)

### Push to Quest — ADB Included

The `platform-tools` folder is included in the zip. It contains `adb.exe`, `AdbWinApi.dll`, and `AdbWinUsbApi.dll` — **all three files must be in the same folder as `ParaKit.exe`** for Push to Quest to work.

Manual download if needed: [Android SDK Platform Tools](https://developer.android.com/tools/releases/platform-tools)

**One-time Quest setup:**

1. Meta app → Menu → Devices → [headset] → **Developer Mode → On**
2. Plug Quest into PC via USB
3. Put on the headset — tap **Allow** on the USB debugging prompt that appears

### Album Art Cropper — Pillow Included

The Asset Manager album art cropper uses **Pillow** (image library). It is bundled inside `ParaKit.exe` — no separate install needed.

### GPU Acceleration — Stem Splitter

| GPU | Status |
|-----|--------|
| NVIDIA GTX 10-series through RTX 40-series | ✅ Full GPU acceleration (~30s per song) |
| NVIDIA RTX 50-series | ⚠️ CPU only — PyTorch support coming |
| AMD and Intel GPUs | 🖥️ CPU only — Demucs requires CUDA (NVIDIA-exclusive) |

CPU times: typically **45 seconds to ~1m30s**.

---

## Audio Format Guide

> ⚠️ Use `.flac` or `.wav` whenever possible. Converting MP3 → FLAC does **not** recover quality — that data is gone permanently.

| Format | Notes |
|--------|-------|
| `.flac` | Lossless + compressed. Best choice. |
| `.wav` | Lossless + uncompressed. Larger files, same quality. |
| `.mp3` | Accepted but not recommended. |

Use the **YouTube → FLAC tab (Tab 8)** in the app to download lossless audio directly — this is the recommended source. [Bandcamp](https://bandcamp.com) is a good alternative if you own the release, as it often offers FLAC downloads from artists.

---

## Stem Splitter

### Standard Split

Outputs **DRUMS ONLY** and **BACKINGS** as `.ogg` files.

- **htdemucs** — fastest, great quality *(recommended)*
- **htdemucs_ft** — slower, slightly more accurate

### Custom Isolation Split *(🧪 BETA)*

Isolates individual drum parts — Kick, Snare, Hi-Hat, Toms, Cymbals — each as a separate `.ogg` file. Uses `htdemucs_6s` automatically. Optional Backings split.

> ⚠️ **BETA — results are not perfect.** Bleed between instruments is expected. Not recommended for Auto MIDI input. Best use: load isolated stems into the MIDI Editor for per-lane note verification.

Selecting all 6 stems at once automatically reverts to the standard split.

### 🥁 DrumSep — Drum Component Separation *(🧪 BETA)*

Separates a **drums-only stem** into 4 individual components: **Kick, Snare, Cymbals, Toms**. Uses a specialized drum separation model (not demucs) trained specifically for drum isolation.

> ⚠️ **Run Standard Split first** to get a drums-only stem, then run DrumSep on that result. Do not run it on a full mix.

**First-time setup:** Enable DrumSep → click **↓ Download Model** (~200MB, one-time). Downloads from GitHub first, Google Drive as fallback. Stored in `drumsep_model\` next to `ParaKit.exe`.

**Output:** `songname_kick.ogg`, `songname_snare.ogg`, `songname_cymbals.ogg`, `songname_toms.ogg` in separate subfolders.

**Best use:** Load each stem into a MIDI Editor stem slot. The kick stem shows only kick transients in the waveform — makes note placement much more precise per lane.

---

## Audio → MIDI — Genre Guide

The auto-detector gives a strong starting point, not a finished chart. Notes may land slightly off-beat — use **Quantize** to fix in bulk, or drag manually with Snap to Grid off.

| Genre | Notes |
|-------|-------|
| Auto | Best starting point for most songs |
| No Adjustment | Raw defaults |
| Pop / Pop-Punk & Rock | Kick threshold raised, snare more sensitive |
| Metal / Hard Rock / Post-Hardcore | Snare detection very sensitive for noisy stems |

**Instrument notes:**

- **Toms** — unreliable. Use Reclassify or add manually. Turn off Snap to Grid for fast fills.
- **Ride** — leave detection OFF. Reclassify hi-hats/crashes that should be ride.
- **Kicks** — ~90% accurate. Too many: disable detection. Too few: enable or add manually.

---

## MIDI Editor

### 1–8 Note Hotkeys

| Key | Lane | Key | Lane |
|-----|------|-----|------|
| `1` | Kick | `5` | Ride |
| `2` | Snare | `6` | Tom 1 |
| `3` | Hi-Hat | `7` | Tom 2 |
| `4` | Crash | `8` | Floor Tom |

Hotkeys place at the **playhead** (playing) or **last canvas click** (paused). Snap to Grid applies.

### Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `P` | Play / pause |
| `S` | Stop |
| `T` | Tap offset |
| `B` | Tap BPM for last tempo entry |
| `D` | Place marker |
| `Middle-click` | Place marker at position |
| `1` – `8` | Place note in lane |
| `Ctrl + Z / Y` | Undo / Redo |
| `Ctrl + C / V` | Copy / Paste |
| `Ctrl + Q` | Quantize to 16th grid |
| `Ctrl + scroll` | Zoom |
| `Delete` | Remove selected notes/markers |

### Edit Tools

| Tool | What it does |
|------|-------------|
| ⊞ Quantize | Snap to 16th-note grid |
| ⧉ / ⧈ Copy / Paste | Paste at playhead; pasted notes auto-selected |
| × Dedup | Remove stacked duplicate notes |
| ↻ Repeat | Tile selection once after itself |
| 🥁 Flam | Grace note (vel 30) 30ms before each selected note |

### Velocity — Ghost & Accent Notes

| Velocity | Type | Visual in Editor | Paradiddle |
|----------|------|-----------------|------------|
| 1–39 | Ghost note | Hollow outline | Quiet, subtle hit |
| 40–114 | Normal | Solid fill | Standard hit |
| 115–127 | Accent | Solid + white outline | Loud, prominent hit |

Open the **Velocity Lane** via the Tempo Map + Velocity Lane checkbox. Click/drag bars to set velocity. Quick presets: Ghost (30), Normal (100), Accent (120).

### Multi-Stem Audio

Load up to 4 stems. Radio button selects the active stem. **Single** or **Layered** playback mode. **🎚 Mixer** button opens per-stem volume controls.

> ⚠️ Layered mode at non-1.0x speed is CPU-intensive.

### Markers

**D** key or **middle-click** places a marker. Click the triangle handle in the header to select/drag. Color and label via the **📍 Markers** popup button.

### Ghost Overlay

Load a reference MIDI as faded background notes for charting multiple difficulties. Browse in the Display & Snap panel. Opacity slider 10–60%.

---

## Asset Manager (Tab 9)

**Auto-Fetch Metadata** — searches [MusicBrainz](https://musicbrainz.org) and iTunes. One click fills Song Creator fields. Cover art can be overridden by manually browsing a different image.

**Album Art Cropper** — crops any image to a centered 1:1 square. Output sizes: 256, 512 *(recommended)*, or 1024px.

**Preview Audio Trimmer** — exports a `.ogg` clip (~15 seconds) for the Paradiddle song selection menu.

---

## Song Creator — Output Options

- **Also save as .zip** — automatically zips the output folder after conversion
- **Zip To** — optional separate folder for zips; leave blank to save next to the output
- **📲 Push to Quest** — sends the converted folder directly to a connected Meta Quest via USB

---

## Common Problems

| Problem | Fix |
|---------|-----|
| Notes out of sync | Run Song Tester; use .ogg not MP3 |
| Wrong instrument | Reclassify mode in MIDI Editor |
| Toms missing | Unreliable — add manually or Reclassify |
| Stem Splitter fails | FFmpeg not on PATH |
| Stem Splitter slow | Normal for AMD/Intel and RTX 50-series |
| YouTube fails | Check yt-dlp is next to exe; Auto-update on |
| Push to Quest fails | Accept USB debugging prompt in headset |
| App crashed silently | Check `parakit_crash.txt` next to ParaKit.exe |
| Drag/drop broken | Use Browse buttons |

---

## Paradiddle MIDI Note Mapping

| MIDI Notes | Instrument | Paradiddle |
|-----------|-----------|------------|
| 35, 36 | Kick Drum | BP_Kick_C |
| 37, 38, 40 | Snare Drum | BP_Snare_C |
| 41, 43 | Floor Tom | BP_FloorTom_C |
| 42, 44, 46 | Hi-Hat | BP_HiHat_C |
| 45, 47 | Low Tom | BP_Tom2_C |
| 48, 50 | Mid Tom | BP_Tom1_C |
| 49, 55, 57 | Crash Cymbal | BP_Crash15_C / BP_Crash17_C |
| 51, 53, 59 | Ride Cymbal | BP_Ride17_C / BP_Ride20_C |

*Notes not in the above list are silently ignored.*

---

## Changelog

| Version | Summary |
|---------|---------|
| **v3.5.1** | DrumSep drum component separator, DPI awareness, ghost/accent visual fixes, layered audio sync & volume, stem switch during playback, velocity lane live redraw, beat ruler fix, collapsible help tab, auto-updater filter |
| **v3.5.0** | Asset Manager, auto-metadata, Push to Quest, zip output, Ghost Overlay, ghost/accent visuals, Custom Isolation Split (BETA), crash handler, major bug fixes |
| v3.3.2 | Multi-stem workspace, layered audio, 1-8 hotkeys, Flam, Markers, Velocity Lane, Quantize, Copy/Paste, Dedup, Repeat |
| v3.3.0 | YouTube → FLAC, auto-updater, edit tools, markers |
| v3.2.0 | Sheet Music → MIDI tab |
| v3.1.0 | Multi-select, playback speed, loop, project save/load |
| v3.0.0 | Renamed to ParaKit, dark theme |

---

*Created by Micah P.G. — ParaKit v3.5.1 — For the Paradiddle Community*
