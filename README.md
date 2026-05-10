*NOTE -- v4.0+ is still being developed and will include MASSIVE improvements to the Audio → MIDI auto detector as well as major UI clean up, more Q.O.L. features, and more* 

CHECK THE BOTTOM OF THE PAGE FOR THE CHANGELOG/PROGRESS

*most recent update for this README was on: 5/6/26*

THE DOWNLOAD LINK IS FOR v3.5.1 to be clear! v4.0+ is coming soon, 

I am posting progress of the development on here via the readmes. I expect to release the current build very soon. I can't give an exact date,
I want to make sure I deliver on the quality increase that I've mentioned. So I expect sometime in the week of May 11th 2026.

google drive is a placeholder text file for now, v3.5.1 is the limewire link

# ParaKit -- Paradiddle / Paradiddle VR w/Clone Hero Export Option -- Custom Song Creator & All-in-One Drum Chart Tool — v4.3.25 
*App is a work in progress — updates released as frequently as possible. Thank you for your patience.* 

I've updated the theme in v4.0+ to match the PD colors, but I wanna be clear that this app is not officially related to Paradiddle in any way, this is a community made app

I am aware that there are much better and longer standing tools for Clone Hero specifically, I just thought it would be nice to add the option for dual exports. 

> ⬇️ **DOWNLOAD:** 
> Alt: https://limewire.com/d/svTK9#fqZoG5vUjc

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

ParaKit v4.0 added an AI-powered drum detection engine based on the **ADTOF** neural network -- trained on rhythm game chart data and optimized for drum transcription accuracy. v4.3 adds an optional **Enhanced Detection** path for cymbals that significantly improves crash recall on tricky material (fast metal, sparse intros, dense fills).

| Mode | Description |
|------|-------------|
| **Spectral** | Original pipeline. No extra files needed. Works on all systems. |
| **ML / ONNX** | AI detection. Significantly more accurate on kick, snare, hi-hat. Model downloads automatically (~1.7 MB, one-time). |
| **Hybrid** *(recommended)* | Runs ML + Spectral in parallel and merges results using ML timing preferred with spectral cross-confirmation. Best overall accuracy. |

**Enhanced Detection toggle (v4.3.20+) -- optional cymbal upgrade:**

A separate cymbal-specialist model can be enabled for crash detection. On edge-case material -- very fast metal, very slow ballads, sparse intros, dense crash sections -- this raised combined-cymbals detection accuracy by roughly 3x in internal testing. Also adds a 300 ms cooldown (v4.3.23) that prevents one big crash from registering as several closely-spaced hits when the decay tail is long.

| Toggle state | What you get |
|--------------|--------------|
| OFF *(default)* | Standard ADTOF cymbal detection. Faster, simpler. |
| ON | Enhanced cymbal separator + crash cooldown. ~8 sec extra per track. First time you turn it on, a one-time ~110 MB model downloads. |

> **Heads up on rides:** while Enhanced Detection is on, ride hits aren't auto-detected -- the cymbal model groups all cymbals together and routes them to the Crash lane. If a hit should be a ride, switch it in the MIDI Editor (drag in Reclassify mode, or right-click for a lane picker). The built-in detector still handles ride when the toggle is off. A separate ride-detection improvement is researched for a future release.

**Recommended workflow:**
1. Run Stem Splitter -> get a drums-only stem
2. Use that stem as input for Audio -> MIDI
3. Select **Hybrid** as the Detection Engine
4. *(Optional)* Enable **Enhanced Detection** for tracks with prominent or unusual crash work
5. Review and clean up in the MIDI Editor

Audio to MIDI auto-cleans obvious crash/hi-hat overlaps and removes detector-generated snare/tom flams before writing the MIDI. Both cleanup options remain toggleable in advanced settings.

**Known limitations:**
- The ML model combines crash and ride into one cymbal class. Ride hits land in the Crash lane -- use Reclassify to move them. Timestamps are already correct.
- Tom classification is improved in Hybrid but the floor/mid/high split may need manual correction.
- Open and closed hi-hat are not distinguished. Set velocity below 40 on hi-hat notes to indicate open hits.
- v4.3.23 added a ride-toggle gating fix: turning the ride toggle OFF now correctly suppresses all phantom ride emissions (previously a small number could leak through the cymbal resolver on full-mix audio with bright cymbals).

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
| **v4.3.25** | Internal cleanup: relocated an experimental hi-hat detection feature from the wrong position in the processing pipeline to the correct position. Still testing its pros vs cons
| **v4.3.24** | An experimental hi-hat detection toggle from internal testing has been temporarily hidden while I validate it on more audio types.
| **v4.3.23** | Smoother crash detection -- Enhanced Detection now waits a beat before counting another crash, so a single big cymbal stops registering as several closely-spaced hits. Especially helpful on dense, fast tracks. Ride-toggle bug fixed -- if you turned the Ride toggle off but still saw a few ride notes appear (especially on full-mix songs with bright cymbals), those phantom rides are now correctly routed back to crash. |
| **v4.3.22** | MIDI Editor: reactive-note flashes now stay visible a touch longer after the playhead crosses each note. The previous 40 ms window sometimes felt like the flash appeared late and ended quickly, especially when the timing landed against the playback update rate. The flash window is now 50 ms -- still trailing-only (no flash before the playhead reaches the note), just a bit more visible time on the way out. |
| **v4.3.21** | MIDI Editor playback is smoother. The playhead now updates twice as often during playback (40 frames per second instead of 20), so it glides instead of stepping along the timeline. Reactive-note flashes no longer skip notes -- before, about 30-40% of notes wouldn't light up as the playhead crossed them, especially on busy sections. Now every note the playhead passes flashes exactly once, regardless of how fast playback is updating. Also cleaned up some leftover debug messages that were printing to the console during playback. |
| **v4.3.20** | Crash detection upgraded. Enhanced Detection now uses a different cymbal separator that finds many more crashes on tricky material -- fast songs, slow songs, sparse songs, dense songs. You'll spend less time fixing missed crashes in the MIDI Editor. Heads up on rides: while Enhanced Detection is on, ride hits aren't auto-detected -- if a hit should be a ride, switch it in the MIDI Editor (drag in Reclassify mode, or right-click for a lane picker). The built-in detector still handles ride when the toggle is off. Conversion runs faster too -- the new separator is about 7x quicker on CPU than the old one. First time you turn the toggle on, ParaKit downloads a one-time ~110 MB model file. After that it's cached and starts instantly. |
| **v4.3.19** | MIDI Editor: notes no longer flash white before the playhead reaches them. The reactive-note highlight used to start about 40 ms early and end 40 ms late, which was easy to spot at high zoom and could make precise edits feel a hair off. Now the highlight begins exactly when the playhead crosses the note time and fades 40 ms after -- no pre-trigger. Useful when you're zoomed in and lining up hits to the millisecond. *(Further refined in v4.3.21 and v4.3.22.)* |
| **v4.3.18** | Audio -> MIDI tab layout: column-balance follow-up to v4.3.17. The Enhanced Detection panel now sits in the wide left column with the rest of the detection settings, restoring the wide-left / narrow-right layout from earlier versions. The right column is no longer squashed by Enhanced Detection's longer status text. Existing button-row packing fixes from v4.3.17 remain intact. |
| **v4.3.17** | Audio -> MIDI tab: comprehensive layout restoration. Several v4.3 dev changes had drifted the tab's layout away from the v4.2 baseline. Browse / Clear / Check / Get Model / Reset rows are restored, the active-engine label is no longer width-capped, and the right column is properly filled. Detailed setup and troubleshooting guidance stays in the Help tab. |
| **v4.3.15** | Audio -> MIDI Detection Engine layout regression fix. Browse / Clear / Check / Get Model / Reset buttons render correctly again -- a packing bug had let the input Entry consume all horizontal space ahead of the LEFT-side buttons. The "active engine" status label is no longer truncated. Verbose Detection Engine helper text consolidated to one-liners with the detailed how-to content moved to the Help tab. |
| **v4.3.13** | Restoration of v4.3.x changes lost during a build incident: album art now displays in-game on Paradiddle charts again (cover files save as `album.<ext>` next to the .rlrr); Preview/Practice Track tab name shows correctly in the editor; speed slider on Preview/Practice Track applies live during playback (no need to stop and restart); note size sliders stay capped at the new tighter range (0.3x-1.0x, default 0.3x); Practice mode hit feedback shows just the PERFECT/GOOD/MISS label below the hit line -- no more flash rectangle around the lane. |
| **v4.3.12** | V-key vertical-drag removed from the MIDI Editor after persistent reliability issues. Reclassify mode already provides the same lane-change functionality and is the recommended path going forward. The status bar message now reads "Reclassify toggle: drag to change lane." Help tab updated with Reclassify-mode guidance. |
| **v4.3.11** | Practice game hit feedback cleanup -- the colored flash rectangle around the hit lane has been removed, and the PERFECT / GOOD / MISS label moved to just below the hit line for clearer feedback. |
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

*Created by Micah P.G. -- ParaKit v4.3.25 (dev preview) -- For the Paradiddle & Clone Hero Community*

