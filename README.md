# ParaKit--Paradiddle PC / VR w/Clone Hero Export Support

### Custom Song Creator & All-in-One Drum Chart Tool - v4.4.9

*NOTE -- v4.0+ has delivered MASSIVE improvements to the Audio → MIDI auto detector (including the new Neural Stem Isolation in v4.4.4), major UI cleanup, and many quality-of-life features. See the Changelog at the bottom for what has landed since v3.5.1. The v4.5.0 public release is on the way.*

> **DOWNLOAD:** CURRENT RELEASE (v3.5.1): [https://limewire.com/d/svTK9#fqZoG5vUjc]

*v4.5 Release planned for week of May 11th, 2026 README last updated on 5/9/26*

> **v3.5+ ships with all requirements included in the main .zip download** -- no separate installs needed.

The goal of this project is to make drum chart creation as accessible as possible -- no paywalls, no confusing professional audio software, lower barrier to entry. If you've ever wanted to play a song that isn't in the game, this tool is for you.

Compatible with **Paradiddle (PC)** and **Paradiddle VR (Meta Quest 3)** and **Clone Hero (PC)**
Built for use with any supported e-drum kit or the in-game virtual kit

> The **Quick Start & FAQ tab** inside the app covers everything in detail.

> First launch may take a moment. The app opens faster after the first launch.

---

## Is ParaKit Right for You?

If you're already experienced with MIDI charting and have your own workflow using tools like Reaper, Audacity, or similar -- ParaKit probably won't replace your primary methods. That said, parts of it may still save you steps: the Song Creator, Stem Splitter, Sheet Music -> MIDI, YouTube -> FLAC, Asset Manager, and Track Preview can all slot into an existing workflow without replacing it.

If you're new to charting, or find dedicated audio/MIDI software difficult, confusing, or just more than you need -- ParaKit handles the full pipeline in one place with enough automation to get a playable chart without prior experience.

---

## Tab Overview

| # | Tab | What it does |
|---|-----|-------------|
| 1 | **Single Song Creator** | Convert MIDI + audio into a `.rlrr` or `.chart` file |
| 2 | Create Multiple Songs | Batch convert multiple songs at once |
| 3 | Audio to .ogg Converter | Convert audio formats to .ogg |
| 4 | **Stem Splitter** | AI-separate drums from backing track |
| 5 | **Audio -> MIDI** | Auto-detect drum hits, generate MIDI |
| 6 | **MIDI Editor** | Edit and build drum charts visually |
| 7 | Sheet Music -> MIDI | Convert MusicXML charts to MIDI |
| 8 | YouTube -> FLAC | Download YouTube audio as lossless FLAC |
| 9 | **Asset Manager** | Metadata, album art, preview clips |
| 10 | Song Tester | Verify BPM and sync |
| 11 | **Track Preview** | Watch chart as falling notes |
| 12 | Quick Start & FAQ | Built-in guide and troubleshooting |

---

## Quick Start

**STEP 1 -> Stem Splitter (Tab 4)**

Split your song into drums-only and backing. Use `.flac` or `.wav` for best quality. Use **YouTube -> FLAC (Tab 8)** if you need a lossless source.

**STEP 2 -> Audio -> MIDI (Tab 5)**

Convert the drums-only track into MIDI. Select **Hybrid** detection mode and the Genre closest to your song for the best results. Click **"Open Last Result in Editor"** after converting.

If detection quality was off, use the **Detection Troubleshooter** in the Help tab -- paste your log, check the symptom boxes, and get specific setting suggestions with one-click apply.

-- *OR* --

**STEP 2 -> Sheet Music -> MIDI (Tab 7)**

Convert a MusicXML drum chart to 1:1 accurate MIDI. Download `.mxl` from [MuseScore.com](https://musescore.com).

**STEP 3 -> MIDI Editor (Tab 6)**

Clean up the MIDI. Use **Reclassify mode** for wrong instruments -- click a note to pick from a list, or drag it up/down to change lanes in real time. Use **Review Issues** to find likely problems fast. Use **1-8 hotkeys** to place notes while listening. Set dynamics in the **Velocity Lane**.

**STEP 3.5 -> Track Preview (Tab 11)** *(optional but recommended)*

Watch your chart fall exactly as it will appear in-game, synced to your audio.

**STEP 4 -> Song Tester (Tab 10)**

Verify sync. False positives may appear after manual edits -- always confirm in-game.

**STEP 5 -> Asset Manager (Tab 9)** *(optional)*

Auto-fetch metadata, crop album art to 1:1, trim a 15-second preview clip.

**STEP 6 -> Single Song Creator (Tab 1)**

Combine MIDI + audio into a chart. Select **Paradiddle (.rlrr)**, **Clone Hero (.chart)**, or **Both**. Enable **Also save as .zip** for a shareable archive.

**STEP 7 -> Deploy**

- **Paradiddle PC:** `Documents\Paradiddle\Songs\`
- **Paradiddle Quest (USB):** Click **Push to Quest** *(requires adb.exe -- see Setup)*
- **Paradiddle Quest (manual):** `Internal Shared Storage\Paradiddle\Songs\`
- **Clone Hero:** `Clone Hero\Songs\[Artist - Title]\`

---

## Setup

> **ffmpeg, yt-dlp, and adb are all included in the ParaKit release zip.** Extract the full zip and keep the included folder structure together. v4.1.8+ supports a cleaner optional `Requirements\` subfolder for ffmpeg, ffprobe, yt-dlp, and downloaded models.

### FFmpeg -- Included

`ffmpeg.exe` and `ffprobe.exe` are included. They may live next to `ParaKit.exe` or inside a `Requirements\` subfolder next to it. No install or PATH setup needed. Keep the release folder together or audio conversion and the Stem Splitter will stop working.

### YouTube -> FLAC -- yt-dlp Included

`yt-dlp.exe` is included. It may live next to `ParaKit.exe` or inside `Requirements\`. Keep **Auto-update yt-dlp** checked in the YouTube tab because YouTube occasionally changes its API and yt-dlp needs to update to stay compatible.

Manual download if needed: [github.com/yt-dlp/yt-dlp/releases/latest](https://github.com/yt-dlp/yt-dlp/releases/latest)

### Optional Requirements Folder

ParaKit v4.1.8+ can keep external helper files in a cleaner `Requirements\` folder next to `ParaKit.exe`:

```text
ParaKit.exe
Requirements\
  ffmpeg.exe
  ffprobe.exe
  yt-dlp.exe
  platform-tools\
  parakit_drum_model.onnx
  demucs_models\
  drumsep_model\
```

The older layout still works too: those same files/folders may live directly next to `ParaKit.exe`. If `Requirements\` exists, new model downloads are saved there automatically.

### Push to Quest -- ADB Included

The `platform-tools` folder is included in the zip. It contains `adb.exe`, `AdbWinApi.dll`, and `AdbWinUsbApi.dll` -- **all three files must stay together** in one of these locations:

- inside `Requirements\platform-tools\` *(recommended -- matches the new clean layout)*, or
- directly inside `Requirements\` *(flat)*, or
- next to `ParaKit.exe` *(legacy layout still works)*.

Manual download if needed: [Android SDK Platform Tools](https://developer.android.com/tools/releases/platform-tools)

**One-time Quest setup:**

1. Meta app -> Menu -> Devices -> [headset] -> **Developer Mode -> On**
2. Plug Quest into PC via USB
3. Put on the headset -- tap **Allow** on the USB debugging prompt that appears

### GPU Acceleration -- Stem Splitter

| GPU | Status |
|-----|--------|
| NVIDIA GTX 10-series through RTX 40-series | Full GPU acceleration (~30s per song) |
| NVIDIA RTX 50-series | CPU only -- PyTorch support coming |
| AMD and Intel GPUs | CPU only -- Demucs requires CUDA (NVIDIA-exclusive) |

CPU times: typically **45 seconds to ~1m30s**.

---

## Audio Format Guide

> Use `.flac` or `.wav` whenever possible. Converting MP3 -> FLAC does **not** recover quality -- that data is gone permanently.

| Format | Notes |
|--------|-------|
| `.flac` | Lossless + compressed. Best choice. |
| `.wav` | Lossless + uncompressed. Larger files, same quality. |
| `.mp3` | Accepted but not recommended. |

Use the **YouTube -> FLAC tab (Tab 8)** to download lossless audio directly. [Bandcamp](https://bandcamp.com) is a good alternative if you own the release.

---

## Stem Splitter

### Standard Split

Outputs three folders next to your input audio:

- **DRUMS ONLY** -- isolated drum track as `.ogg` *(for game packaging)*
- **BACKINGS** -- everything except drums as `.ogg` *(for game packaging)*
- **SPLITS TO USE IN AUTO DETECTOR** -- lossless `.flac` drums stem *(fed to Audio -> MIDI for cleaner detection)*

The success popup's **Send Lossless Drums to MIDI Converter** button routes the FLAC to the Audio -> MIDI tab automatically -- no manual file picking required.

- **htdemucs** -- fastest, great quality *(recommended)*
- **htdemucs_ft** -- slower, slightly more accurate

### Custom Isolation Split *(BETA)*

Isolates individual stem types -- Drums, Bass, Guitar, Piano, Vocals, Other -- each as a separate `.ogg` file.

> **BETA -- results are not perfect.** Bleed between instruments is expected. Not recommended for Auto MIDI input.

### DrumSep -- Drum Component Separation *(BETA)*

Separates a **drums-only stem** into 4 individual components: **Kick, Snare, Cymbals, Toms**. Uses a specialized drum separation model trained specifically for drum isolation.

> **Run Standard Split first** to get a drums-only stem, then run DrumSep on that result. Do not run it on a full mix.

**First-time setup:** Enable DrumSep, then click **Download Model** (~200MB, one-time). Stored in `Requirements\drumsep_model\` when `Requirements\` exists, otherwise in `drumsep_model\` next to `ParaKit.exe`.

**Best use:** Load each stem into a MIDI Editor stem slot. The kick stem shows only kick transients -- makes note placement much more precise per lane.

---

## Audio -> MIDI -- Detection Engine

ParaKit v4.0 added an AI-powered drum detection engine based on the **ADTOF** neural network -- trained on rhythm game chart data and optimized for drum transcription accuracy.

| Mode | Description |
|------|-------------|
| **Spectral** | Original pipeline. No extra files needed. Works on all systems. |
| **ML / ONNX** | AI detection. Significantly more accurate on kick, snare, hi-hat. Model downloads automatically (~1.7 MB, one-time). |
| **Hybrid** *(recommended)* | Runs ML + Spectral in parallel and merges results using ML timing preferred with spectral cross-confirmation. Best overall accuracy. |

**Recommended workflow:**
1. Run Stem Splitter -> get a drums-only stem
2. Use that stem as input for Audio -> MIDI
3. Select **Hybrid** as the Detection Engine *(works best on both drums-only stems and full mixes since v4.3.30)*
4. *(Optional)* Turn on **Neural Stem Isolation** for an extra AI cleanup layer on tricky tracks -- see next section
5. Review and clean up in the MIDI Editor

Audio to MIDI now auto-cleans obvious crash/hi-hat overlaps and removes detector-generated snare/tom flams before writing the MIDI. Both cleanup options remain toggleable in advanced settings.

**Known limitations:**
- The ML model combines crash and ride into one cymbal class. Ride hits land in the Crash lane -- use Reclassify to move them. Timestamps are already correct.
- Tom classification is improved in Hybrid but the floor/mid/high split may need manual correction.
- Open and closed hi-hat are not distinguished. Set velocity below 40 on hi-hat notes to indicate open hits.

---

## Audio -> MIDI -- Neural Stem Isolation *(v4.4.4+, experimental, opt-in)*

A new section in the **Audio -> MIDI Settings** panel added in v4.4.4. When turned on, ParaKit runs your input audio through an AI drum-stem splitter (**Jarredou MDX23C 6-stem**) before detection runs, cleaning up bleed between kick, snare, hi-hat, toms, and cymbals. Detection then runs on the cleaned audio.

| Mode | Description |
|------|-------------|
| **Off** *(default)* | Detection runs directly on your input audio. No extra processing. |
| **Jarredou MDX23C 6-stem** | AI splitter pre-cleans the audio. Adds ~30-60s per song on CPU. Improves snare / kick / crash detection on tricky tracks. |

**When to use it:** songs with lots of bleed between drum components -- especially metal tracks where kick and crash hit at the same time, or tracks where the hi-hat sits low in the mix and gets confused with cymbals.

**First-time setup:** flip the toggle to Jarredou and click **Download model** -- a one-time ~417 MB download. The model is cached to your user app-data folder, not bundled with the release zip. Subsequent runs reuse the cached model.

**Cost / caveats:**
- CPU-only inference in this version. GPU support coming when PyTorch catches up to RTX 50-series.
- Adds ~30-60s per song to detection time.
- The ride lane still uses default detection (Jarredou's ride stem is not yet routed through the detector).
- If anything goes wrong with the splitter at run time, ParaKit automatically falls back to default detection on the original audio so your conversion still finishes.

**Internal benchmark (5-track metal corpus):** Neural Stem Isolation lifted snare F1 by +0.24, kick by +0.16, and crash by +0.13 over default detection.

### Detection Troubleshooter *(Help Tab)*

If your result has too many or too few hits of a specific instrument:

1. After converting, select all text in the log box and copy it (`Ctrl+A`, `Ctrl+C` directly inside the log)
2. Go to the **Help tab -> Detection Troubleshooter** (open by default)
3. Paste the log, check the symptom boxes that match your result
4. Click **Analyze** -- the troubleshooter reads your actual detection numbers and gives specific settings to try
5. Click **Apply Settings** to choose which suggested changes to push to Audio -> MIDI settings automatically

---

## Audio -> MIDI -- Genre Guide

| Genre | Notes |
|-------|-------|
| Auto | Best starting point for most songs |
| No Adjustment | Raw defaults |
| Pop / Pop-Punk & Rock | Kick threshold raised, snare more sensitive |
| Metal / Hard Rock / Post-Hardcore | Snare detection very sensitive for noisy stems |

**Instrument notes:**

- **Toms** -- unreliable in Spectral, improved in Hybrid. Use Reclassify or add manually. Turn off Snap to Grid for fast fills.
- **Ride** -- leave detection OFF by default. Reclassify hi-hats/crashes that should be ride.
- **Kicks** -- ~90% accurate. Too many: raise ML threshold or disable. Too few: lower threshold or add manually.

---

## MIDI Editor

### 1-8 Note Hotkeys

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
| `B` | Tap BPM |
| `D` | Place marker |
| `Middle-click` | Place marker at position |
| `1` - `8` | Place note in lane |
| Undo / Redo | Full state restore -- notes, markers, flags, selection, timeline |
| Copy / Paste | Paste at playhead; pasted notes auto-selected |
| `Ctrl + Q` | Quantize to 16th grid |
| `Ctrl + scroll` | Zoom |
| `Delete` | Remove selected notes/markers |

### Edit Tools

| Tool | What it does |
|------|-------------|
| Undo / Redo | Full state restore -- notes, markers, flags, selection, timeline |
| Quantize | Snap to 16th-note grid |
| Soft Quantize | Snap only notes within a set window -- preserves feel |
| Copy / Paste | Paste at playhead; pasted notes auto-selected |
| Dedup | Remove duplicate notes -- gap-based dialog, optional impossible-cluster removal |
| Repeat | Tile selection once after itself |
| Flam | Grace note (vel 30) 30ms before each selected note |
| Vel Filter | Remove notes below a velocity threshold -- scopes to selection or whole chart |
| Re-run ML | Re-run AI detection on the same source audio with current settings |
| Review Issues | Scan for duplicates, misclassifications, and low-confidence ML notes |

### Reclassify Mode

Enable the **Reclassify mode** toggle (green checkbox in the toolbar).

- **Click a note** -- opens a picker menu to select the correct instrument lane
- **Drag a note up/down** -- moves it to the lane under the cursor in real time

Works on a single note or on a full multi-note selection. Turn OFF when done to return to normal edit mode.

### Velocity -- Ghost & Accent Notes

| Velocity | Type | Visual in Editor |
|----------|------|-----------------|
| 1-39 | Ghost note | Hollow outline -- quiet, subtle hit |
| 40-114 | Normal | Solid fill -- standard hit |
| 115-127 | Accent | Solid + hot pink outline -- loud, prominent hit |

Open the **Velocity Lane** via the checkbox below the piano roll. Click/drag bars to set velocity. Quick presets: Ghost (30), Normal (100), Accent (120).

### Tempo Map

Click the **Tempo Map** button below the piano roll to open a floating popup window for setting BPM changes. Separated from the Velocity Lane so opening it no longer affects the piano roll height.

### Visual Flags

| Outline / style | Meaning |
|----------------|---------|
| Lime | Selected note |
| Hot pink outline | Accent note (vel >= 115) |
| Hot pink stripes | Low-confidence ML note (< 70% model confidence) |
| Yellow (lime green on Ride notes) | Possible misclassification candidate |

### Multi-Stem Audio

Load up to 4 stems. **Single** mode plays only the active stem. **Layered** mode plays all loaded stems simultaneously. **Mixer** button opens per-stem volume controls.

> Layered mode at non-1.0x speed is CPU-intensive.

### Markers

**D** key or **middle-click** places a marker. Click the triangle handle in the header to select/drag. Color and label via the **Markers** popup button.

### Ghost Overlay

Load a reference MIDI as faded background notes -- useful for charting multiple difficulties from the same song. Browse in the Display & Snap panel. Opacity slider 10-60%.

---

## Track Preview (Tab 11)

Watch your chart fall exactly as it will appear in Paradiddle, synced to your audio.

**Audio toggle** -- switch between Full Mix and Drums-only stem during playback.

---

## Asset Manager (Tab 9)

**Auto-Fetch Metadata** -- searches [MusicBrainz](https://musicbrainz.org) and iTunes. One click fills Song Creator fields. Cover art can be overridden by manually browsing a different image.

**Album Art Cropper** -- crops any image to a centered 1:1 square. Output sizes: 256, 512 *(recommended)*, or 1024px. Paradiddle requires square album art.

**Preview Audio Trimmer** -- exports a `.ogg` clip (~15 seconds) for the Paradiddle song selection menu.

---

## Song Creator -- Output Options

| Option | Notes |
|--------|-------|
| **Paradiddle (.rlrr)** | Standard Paradiddle chart format |
| **Clone Hero (.chart)** | Writes `notes.chart` + `song.ini` with `pro_drums = True`; copies audio and cover art |
| **Both** | Outputs both formats from a single conversion |
| Also save as .zip | Zips the output folder after conversion |
| Zip To | Optional separate folder for zips |
| Push to Quest | Sends Paradiddle output directly to a connected Meta Quest via USB |

**Clone Hero notes:** Place the exported folder in `Clone Hero\Songs\`. Cymbal modifier flags (crash, ride, open hi-hat) require `pro_drums = True` -- ParaKit writes this automatically.

---

## Common Problems

| Problem | Fix |
|---------|-----|
| Notes out of sync | Run Song Tester; adjust audio offset |
| Wrong instrument | Reclassify mode in MIDI Editor -- click or drag note up/down |
| Toms missing | Unreliable in Spectral -- use Hybrid or add manually |
| Ride hits in crash lane | Normal with ML/Hybrid -- Reclassify after conversion |
| Too many / too few hits | Use Detection Troubleshooter in Help tab -- paste log, check symptom boxes |
| Stem Splitter fails | Keep `ffmpeg.exe` / `ffprobe.exe` next to `ParaKit.exe` or in `Requirements\` |
| Stem Splitter slow | Normal for AMD/Intel and RTX 50-series |
| YouTube fails | Keep `yt-dlp.exe` next to `ParaKit.exe` or in `Requirements\`; keep Auto-update on |
| Push to Quest | Sends Paradiddle output directly to a connected Meta Quest via USB |
| App crashed silently | Check `parakit_crash.txt` next to `ParaKit.exe` |
| Clone Hero cymbals wrong | Verify `pro_drums = True` is in `song.ini` (ParaKit writes this automatically) |
| ML model not found | Click Get Model in the Detection Engine section, or place `parakit_drum_model.onnx` next to `ParaKit.exe` / in `Requirements\` |
| Neural Stem Isolation log says "Separator failed" | v4.4.4-v4.4.7 had a bug where the splitter threw a NameError; fixed in v4.4.8. ParaKit cleanly falls back to default detection so your conversion still finishes. Re-download the model only if the log says hash-mismatch. |
| Hybrid feels worse than Spectral on a drums-only stem | Old v4.0-era guidance said Spectral was better for drums-only stems. v4.3.30+ data shows Hybrid wins decisively (snare F1 0.12 → 0.65 on metal). The in-app guidance was corrected in v4.4.9. Use Hybrid. |

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

*Notes not in the above list are silently ignored during conversion.*

---

## Changelog

| Version | Summary |
|---------|---------|
| **v4.4.9** | Audio → MIDI Detection Engine guidance copy corrected. The note under the Spectral / ML / Hybrid radios used to say Spectral was the better choice for drums-only stems. That was outdated v4.0-era advice. Internal testing on a metal drums-only corpus shows Hybrid wins decisively: snare F1 0.12 → 0.65, hi-hat 0.00 → 0.27, crash 0.16 → 0.23. New note now recommends Hybrid for both full mixes and drums-only stems. No detection logic changed; only the guidance text. |
| **v4.4.8** | Neural Stem Isolation actually works now. Since v4.4.4 the new toggle was silently failing every time at the start of conversion (NameError on a missing `import time` inside the v4.4.4 separator-slot wrap), so ParaKit fell back to default detection on the original audio. Conversions still completed but you weren't getting the AI-cleaned drums. Fix: added the missing local import. Surfaced by smoke test 2026-05-09. |
| **v4.4.7** | Loading bars added to the **Audio to .ogg Converter** and **Create Multiple Songs** tabs. Both tabs now show ParaKit's animated purple progress bar while a conversion is running, so you can tell at a glance the app is still working instead of frozen. Covers both the 3-slot batch section and the Folder Batch section underneath it. |
| **v4.4.6** | Audio → MIDI tab: "Setting Snapshots" panel renamed to "Settings Profiles". Same feature -- save, load, and delete your favorite detector configurations under a name. Just a clearer label for what the panel does. |
| **v4.4.5** | Detection Engine "↓ Get Model" button is fixed. Previously the button tried to download the AI drum model from the wrong web address, so it always failed with "Download failed from all sources." Button now reaches the correct GitHub release on the first try. Also: Get / Download Model buttons now gray out automatically once the model is on your computer (applies to the Detection Engine model, the Stem Splitter DrumSep model, and the v4.4.4 Neural Stem Isolation model). |
| **v4.4.4** | **Neural Stem Isolation (experimental, opt-in).** New section in Audio → MIDI Settings. Off by default; flip the radio to Jarredou MDX23C and ParaKit runs your audio through an AI drum-stem splitter before detection, cleaning up bleed between kick / snare / hi-hat / toms / cymbals. Detection then runs on the cleaned audio. First-time setup downloads a one-time ~417 MB model to your user app-data folder. Adds ~30-60s per song on CPU. Internal testing on a 5-track metal corpus measured snare F1 +0.24, kick +0.16, crash +0.13 over default detection. Architecturally the first plug-in for ParaKit's new separator-slot system -- future research-validated drum splitters can plug into the same slot. |
| **v4.4.3** | Kick detection cleanup. The detector sometimes fired multiple kick onsets very close together (under 30ms) for what was actually a single kick hit, leaving cluster-style duplicate notes to clean up in the editor. Kick dedup window widened to 40ms (up from 30ms in spectral / 20ms in hybrid). Validated against a 5-track metal corpus: detection accuracy improves on every track, and legitimate fast double-kicks at metal tempos are not affected. |
| **v4.4.1 - v4.4.2** | YouTube → FLAC tab gained an optional custom-filename override (checkbox + text field with Windows-illegal-character sanitization and a live preview). Enhanced Detection became selectable: Off, Crash only, Toms only, or Crash + Toms; existing v4.4.0 ON setting carries over as Crash + Toms. |
| **v4.4.0** | Enhanced Detection extended from crash-only output to crash + tom output. The toggle that improves cymbal detection on tricky tracks now also helps with tom fills -- big rock and metal tracks with active fills benefit most. Default-OFF; tom-sparse songs should leave it off. |
| **v4.3.30** | Snare wire-band threshold raised after empirical validation on an 18-track tuning corpus. Default snare detection is now stricter on what counts as a real snare hit, removing roughly 97% of detected false positives across pop / metal / rock / alternative tracks. Funk preset's ghost-note sensitivity is intentionally preserved. |
| **v4.3.27 - v4.3.29** | UI polish bundle. Note size sliders in MIDI Editor / Preview / Practice replaced with precise +/- button steppers (preserves 0.3x-1.0x range and 0.3x default). MIDI Editor zoom slider removed; existing -/+ zoom became a labeled stepper. Single track / Layered radios stacked vertically to reclaim horizontal space. Scrollbars across the app recolored to ParaKit's purple accent so the thumb is visible against the dark canvas. Snap to grid checkbox visibility fix. What's New panel cleanup -- only the 3 most recent versions visible at top, older versions in a collapsible section. |
| **v4.3.20 - v4.3.26** | Enhanced Detection cymbal path moved from Jarredou to LarsNet for a permissively-licensed alternative with comparable accuracy. Crash cooldown added to the LarsNet wrapper. Ride-toggle gating fix. Hi-hat adaptive cleaner experiment added then removed after empirical validation showed it was over-filtering real hi-hats on production code path. |
| **v4.3.21 - v4.3.22** | MIDI Editor smoothness pass: playhead update rate doubled from 20 FPS to 40 FPS, reactive-note flash window loosened from 40ms to 50ms with crossing-detection so notes always flash even at fast tempos / heavy redraws. Stripped leftover debug `[PLAYHEAD-DEBUG]` print statements that v4.3.14 added for diagnostics. |
| **v4.3.12 - v4.3.19** | V-drag removed from MIDI Editor (replaced by Reclassify mode -- click a note to pick its lane from a list, or drag up/down). Album art save now uses `album.<ext>` filename matching paradb convention. Audio → MIDI Detection Engine layout regression fixed (Browse / ✕ / Check / Get Model / Reset buttons render correctly again). Active engine label no longer truncated. Reactive-note early-trigger bug fixed (asymmetric trailing-only window). Encoding-corruption emergency recovery (v4.3.16 mojibake round-trip). |
| **v4.3.0 - v4.3.11** | Track Preview tab renamed to Preview/Practice Track. Practice subtab gains pitch-preserving speed slider with live update during playback. Practice game hit feedback cleanup (PERFECT/GOOD/MISS label moved below hit line). Various MIDI Editor stability polish. Preview Audio Trimmer auto-routes preview clip into Song Creator. |
| **v4.2.12** | All option sliders now show faint tick marks below the track so common settings are easier to dial in from memory (ticks every 10 px). Slider knobs are now purple across the app, matching the loading bar and button accent color instead of the default blue. Applies to all sliders on Audio-to-MIDI, MIDI Editor, Song Creator, and Track Preview tabs. |
| **v4.2.11** | MIDI Editor: Chart Start / Chart End markers. A green dashed line marks the first note in the loaded chart; an orange dashed line marks the last note. Both are labeled in the timeline header. On the waveform strip, audio before Chart Start and after Chart End is darkened so you can see at a glance which parts of the audio are not covered by the chart. Prevents users from mistakenly shifting notes to align with pre-roll audio, which would break in-game sync. Help tab updated with Chart Start / Chart End explanation. |
| **v4.2.10** | MIDI Editor: hotkeys (1-8, Ctrl+Z/C/V, Delete, etc.) now resume working after typing in any text field — clicks on the editor canvas, waveform strip, or velocity lane reclaim focus automatically. Audio output latency slider (0-200 ms, auto-estimated per OS at startup: Windows ~42 ms / macOS ~22 ms / Linux ~37 ms) compensates for the gap between when audio playback starts and when sound reaches the speakers, so the playhead stays in sync with what you hear. T-tap and saved-on-pause positions also use the corrected audio-true time. |
| **v4.2.9** | MIDI Editor: Grid resolution toggle added to Display & Snap panel. Choose 1/4, 1/8, 1/16, or 1/32 note subdivisions. Bar lines stay full brightness, beat lines stay normal, and subdivision lines are drawn progressively lighter — in 1/32 mode three shading levels appear (8th, 16th, 32nd). Switching the resolution never moves notes (positions are stored as absolute time and are unaffected by the visual grid). Help tab updated with grid resolution documentation. |
| **v4.2.8** | Song Creator & Create Multiple Songs: "➕ Add more stem options" button replaces the .ogg reminder. Adds up to 4 extra audio tracks per song; each has a checkbox to mark it as Song audio (checked) or Drum audio (unchecked, default). Extra stems are added to the .rlrr track lists and copied to the output folder automatically. Song Creator: "✂ Auto-clip first 15s of Song Audio as preview" checkbox auto-trims a 15-second preview.ogg at convert time — disables the Preview Clip field while active. MIDI Extractor: output directory selector added. Top menu bar: MIDI Extractor added to Audio → MIDI and Tools menus. Help tab: Top Menu Bar section removed; Extra Stems + Auto Preview Clip documented in Song Creator section. |
| **v4.2.7** | Audio → MIDI: MIDI Extractor panel added. Converts Paradiddle chart files (.rlrr) to MIDI without re-recording. Single file or batch folder mode, per-difficulty filter, pre-extraction preview, and metadata editing (title / artist / creator). Reveal via "▾ MIDI Extractor (hidden)" in the Advanced / Debug section of the Audio → MIDI tab. Requires the "Extractor Mini App" folder alongside ParaKit.exe. |
| **v4.2.6** | Song Creator: new "Use album art from audio file metadata" toggle. Auto-extracts embedded cover art from the loaded Song Audio file (FLAC, MP3, OGG Vorbis, M4A, MP4), center-crops to 512x512, and uses it as the chart's cover image. WAV and audio with no embedded art show a clear warning. Cover Image row locks while the toggle is on. Toggle state persists across sessions. Front-cover preference applied for all four formats. Asset Manager Auto-Fetch "Apply to Song Creator" split into two buttons: "Apply Metadata" (Title + Artist) and "Apply art from thumbnail" (Cover Art only) — each independent. Practice Mini-Game: keypresses outside the ±75 ms hit window no longer count as misses or break the streak; only an unhit note passing the hit line still counts as a miss. MIDI Editor drag performance: snap-target search converted from O(N) linear scan to O(log N) bisect lookup, and marker drags now share the 16 ms redraw debounce — large files no longer stutter while dragging notes or markers. |
| **v4.2.5** | Track Preview tab renamed to Practice Mini-Game. Canvases grouped on the left for a more square playfield. New gear button opens a Controls remapping dialog. Per-lane key-press flash bar lights up in the lane color on every keypress. New Beat grid toggle, Speed slider (0.7x to 1.0x with pitch-preserving time-stretching), Square notes toggle, lane color bars in the legend, bolder/spaced-out controls hotkeys. Hit detection now compares against the live playback position so well-timed keypresses correctly register. Mouse wheel scroll locked over the playfield; hit line moved up for visibility. |
| **v4.2.4** | MIDI Editor: new V hotkey lets you drag notes freely in both directions at once -- left/right moves time, up/down moves between lanes. V+RightMouse locks motion to vertical-only. Multi-select V-drag preserves the relative vertical pattern. New "Show even when snap off" toggle keeps the yellow guide line visible during drags. Right-click during an active drag is now swallowed by the canvas so the V+L+R lock gesture cannot accidentally delete notes or open menus. |
| **v4.2.3** | Track Preview now includes a keyboard-only Practice subtab with drum-style controls, hit/miss feedback, streak and accuracy tracking, and input latency adjustment. Practice Mode is visual only and does not edit MIDI files or add external MIDI device support. |
| **v4.2.2** | MIDI Editor: kicks are now selectable only from the Kick lane (clicks landing near a kick line in another lane no longer steal selection from the intended note). Uniform Colored Notes color darkened from near-white to a readable medium gray. |
| **v4.2.1** | Curated ground-truth validation now uses a manifest, so cleaned reference MIDIs can be added without editing code. Added standalone curated MIDI QA checks and per-track Markdown validation reports for detector reference work. |
| **v4.2.0** | UI polish pass: buttons gained subtle borders, raised/pressed states, clearer hover feedback, and neon loading bars were retuned with a cleaner trough, softer glow, tighter dots, and smoother comet trail. |
| **v4.1.9** | Audio to MIDI cleanup logs clarified, Review Issues flam wording updated to distinguish editor softening from generated-flam removal, and stale one-off debug/sweep scripts marked so future detector work uses the current validation path. |
| **v4.1.8** | Optional `Requirements\` folder support for helper files and downloaded models. Audio to MIDI crash/hi-hat overlap cleanup and generated-flam removal default ON. Stem Splitter sends lossless detector FLACs to Audio to MIDI. |
| **v4.1.5** | Detection Troubleshooter "Flag in MIDI Editor" per problem -- flagged notes shown with orange outline, jumps to MIDI Editor. Flag workflow closed: right-click flagged note to clear it, Next Flag button to step through all flags, Clear Flags button, live flag counter. Re-run ML and Review Issues tooltips clarified (Troubleshooter = fix settings, Review Issues = clean up result). MIDI Editor redraws viewport-culled + debounced -- large files dramatically faster. Accent notes now hot pink outline. Misclassification outline yellow (lime on Ride). "Show notes as icons" defaults OFF. Header logo PIL LANCZOS. |
| **v4.1.4** | Detection Troubleshooter added to Help tab -- paste Audio -> MIDI log, check symptom boxes, and auto-apply selected settings. "Show notes as in-game icons" toggle added. App header updated for Paradiddle + Clone Hero. Album art placeholder added to Asset Manager. |
| **v4.1.1** | MIDI Drums playback removed. Velocity Filter added to toolbar. Reclassify mode gains vertical drag -- drag note up/down to change lanes in real time. Tempo Map moved to floating popup. Clone Hero audio filename fix + `pro_drums = True` added to `song.ini`. Help tab search highlights collapsed section headers. |
| **v4.0.9** | Clone Hero export added to Song Creator and Batch conversion. Format selector: Paradiddle, Clone Hero, or Both. Exports `notes.chart` + `song.ini`, copies audio and cover art. |
| **v4.0.8** | Live elapsed-time bars and per-line `[mm:ss]` timestamps added to Audio->MIDI, Sheet Music->MIDI, and YouTube->FLAC logs. Asset Manager metadata fetcher improved. |
| **v4.0.7** | Undo/redo now restores full MIDI Editor state -- notes, markers, flags, selection, and timeline length. Dedup and Flam no longer wipe redo history on bail-out. |
| **v4.0.3-4.0.6** | Gap-based Dedup dialog, impossible 3-hit cluster removal, Soft Quantize, Re-run ML, Review Issues wizard, ML confidence shading, per-song settings memory, kick cross-lane click fix, PyInstaller multiprocessing fix. |
| **v4.0.0-4.0.2** | ML/ONNX Detection Engine (ADTOF), Hybrid mode, confidence threshold, per-engine dedup, ONNX model auto-detect, GitHub version check, graceful fallback to Spectral. |
| **v3.5.1** | DrumSep drum component separator, DPI awareness, ghost/accent visuals, layered audio sync fixed, velocity lane live redraw, collapsible help tab with What's New. |
| **v3.5.0** | Asset Manager, auto-metadata fetch, Push to Quest via ADB, zip output, Ghost Overlay, Custom Isolation Split BETA, global crash handler. |
| v3.3.2 | Multi-stem audio workspace (4 slots), layered playback, mixer, 1-8 hotkeys, Flam, Markers, Velocity Lane, Quantize, Copy/Paste, Dedup, Repeat. |
| v3.3.0 | YouTube -> FLAC tab, auto-updater, edit tools. |
| v3.2.0 | Sheet Music -> MIDI tab. App rebranded from SongMaker to ParaKit. |
| v3.1.0 | Multi-select, playback speed, loop section, project save/load. |
| v3.0.0 | Renamed to ParaKit, dark theme, genre presets reworked. |

---

*Created by Micah P.G. -- ParaKit v4.4.9 -- For the Paradiddle & Clone Hero Community*

