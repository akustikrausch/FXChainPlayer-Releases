<h1 align="center">FXChainPlayer</h1>

<p align="center"><strong>A Windows desktop audio player with a full VST3 effect chain built into the playback engine.</strong></p>

<p align="center">
  <a href="https://github.com/akustikrausch/FXChainPlayer-Releases/releases/download/v0.36.7/FXChainPlayer-Setup-0.36.7.exe"><img src="https://img.shields.io/badge/Download-v0.36.7-0078D6" alt="Download v0.36.7"></a>
  <img src="https://img.shields.io/badge/platform-Windows%2010%2F11-0078D6" alt="Windows 10/11">
  <img src="https://img.shields.io/badge/VST3-supported-brightgreen" alt="VST3">
  <img src="https://img.shields.io/badge/ASIO%202.3-Steinberg%20licensed-orange" alt="ASIO 2.3">
  <img src="https://img.shields.io/badge/800%2B%20formats-FLAC%20%C2%B7%20DSD%20%C2%B7%20MOD%20%C2%B7%20SID%20%C2%B7%20Game%20Music%20%C2%B7%20Apple%20Loops-blue" alt="800+ formats">
</p>

<p align="center"><em>Load your favorite plugins — EQs, compressors, reverbs, spatial processors, headphone correction — directly into the signal path and hear them in real time while you listen to music. No DAW required.</em></p>

<p align="center"><a href="https://github.com/akustikrausch/FXChainPlayer-Releases/releases/download/v0.36.7/FXChainPlayer-Setup-0.36.7.exe"><strong>⬇ Download FXChainPlayer-Setup-0.36.7.exe</strong></a></p>

---

## Why VST3 in an audio player?

More reasons than you'd expect.

- **🎧 Headphone surround & spatial audio** — Run binauralizers like **dearVR MONITOR**, **Waves Nx**, or **Dolby Atmos Production Suite** to turn stereo into a full spatial soundstage on any pair of headphones. No system-wide wrapper, no virtual audio cable.
- **🎚️ Headphone calibration & correction** — Use frequency-response plugins like **Sonarworks SoundID Reference**, **Beyerdynamic Headphone Lab**, **Waves Nx Virtual Mix Room**, or **Morphit** to flatten your specific headphone model to a neutral reference.
- **📻 Internet radio & streaming cleanup** — Load a compressor, EQ, de-esser, or multiband processor on poorly-mastered streams or dynamic-range-abusing "loudness war" tracks to tame them while you listen.
- **🔌 Plugin auditioning** — Want to hear how that new reverb, saturator, or tape emulation sounds on real music? Drop it in. No DAW boot-up, no empty session, no audio import.
- **🔊 Loudness normalization & limiting** — Keep playback levels consistent across tracks from wildly different sources (old CDs vs. modern streaming).
- **🏠 Room correction** — Apply convolution IRs or parametric EQ profiles to compensate for your listening room and speaker setup.
- **🅰️🅱️ A/B plugin comparison** — Quickly toggle effects in and out on familiar reference tracks to hear exactly how they color the sound.
- **♿ Accessibility** — Hearing aid profiles, frequency boosting, dynamic range compression, or custom EQ curves for listeners who need tailored audio processing.
- **🎛️ Mix referencing** — Drop your mix in, compare A/B against a reference master, hear your monitor chain on someone else's material.
- **💎 Bake the effect chain into a file** — render any track or the whole playlist through the VST chain to WAV / MP3 / FLAC / OGG, faster than real-time. Take your processed audio anywhere. [Details below](#-export-through-your-vst3-chain--killer-feature).

Up to **8 VST3 plugins in a serial chain**. Drag-and-drop reorder. Per-slot bypass and dry/wet. Smooth global chain mix. Native plugin GUIs. Everything runs at **64-bit double precision** end-to-end.

---

## Plays pretty much everything

FXChainPlayer is built for music listeners who don't want format juggling. Drop a folder with mixed FLAC, MP3, tracker files, C64 SIDs, Game Boy chiptunes, Apple Loops or Wii game-music dumps — it just plays. **800+ extensions across 14 categories** with a built-in searchable Format Library panel.

### Lossless & Hi-Res

**FLAC**, **WAV**, **WavPack** `.wv`, **ALAC** (Apple Lossless), **APE** (Monkey's Audio), **TTA** (True Audio), **AIFF**, **Opus**, **W64** (Sony Wave64), **DSD** `.dsf` / `.dff` (DSD64/128/256/512).

### Lossy

**MP3**, **AAC**, **M4A** / **MP4** audio, **OGG Vorbis**, **WMA**, **MPC** (Musepack SV8), **AC-3**.

### Tracker modules (50+ formats via libopenmpt 0.8.6)

Runtime-detected via `openmpt_is_extension_supported()` — new formats picked up by future libopenmpt patches just work, no source-code changes needed.

**MOD** (ProTracker), **XM** (FastTracker 2), **S3M** (ScreamTracker 3), **IT** (Impulse Tracker), **MPTM** (OpenMPT), **Digibooster Pro**, **Imago Orpheus**, **Graoumf Tracker**, **Liquid Tracker**, **Octalyser**, **PolyTracker**, **UltraTracker**, **Digitrakker**, **OctaMED**, **Farandole Composer**, **Epic MegaGames MASI**, **MadTracker 2**, **Galaxy Sound System**, **X-Tracker**, **Soundtracker Pro II**, **TCB Tracker**, **NoiseTracker**, **Ice Tracker**, **Composer 670**, **SoundFX 1/2**, **Davey Taylor's Tracker**, and many more.

### Console chiptunes (via libgme 0.6.4)

- **GBS** — Nintendo Game Boy
- **SPC** — Super Nintendo (SPC700)
- **VGM / VGZ** — Sega Megadrive · 32X · Master System · Game Gear · Mega CD · SG-1000 · SC-3000 · BBC Micro · ColecoVision
- **AY** — ZX Spectrum · Amstrad CPC (AY-3-8910)
- **NSF / NSFE** — Nintendo Entertainment System
- **KSS** — MSX
- **HES** — PC Engine / TurboGrafx-16
- **SAP** — Atari 8-bit
- **GYM** — Sega Genesis / Mega Drive

### Game music & Apple Loops (~700 formats via vgmstream r2083) — new in v0.36

- **Apple `.caf`** — Logic Pro / GarageBand **Apple Loops** library (no other player decodes this correctly)
- **Nintendo** — BRSTM · BCSTM · BFSTM · BFWAV · DSP-ADPCM family · NUS3AUDIO · Switch Opus
- **Sony** — VAG · HPS · NUB · ATRAC3 / ATRAC9 (FFmpeg-build) · AT3 / AT9
- **Microsoft** — XMA · XWMA
- **CRI** — ADX · HCA · ACB / AWB containers
- **FMOD** — FSB (Multiple)
- **Square Enix** — SCD
- **Wwise** — WEM
- **Bink** — BIK audio
- vgmstream `.txtp` text-playlists with looping / mixing / effects

Core build is **ISC-licensed and FFmpeg-free**. An opt-in CMake flag (`-DFXCHAIN_ENABLE_VGMSTREAM_FFMPEG=ON`) adds ATRAC9 / FSB-CELT / ALAC-in-CAF / FSB-Vorbis at the cost of bundled FFmpeg DLLs (LGPL).

### Retro / specialty

- **SID** — Commodore 64 (cRSID emulator, HVSC Songlengths support — 60 000+ tune durations built-in)
- **IFF 8SVX** — Amiga samples
- **MIDI** / **RMI** — SoundFont 2 (SF2) rendering via TinySoundFont, with Windows Media Foundation fallback
- **CUE sheets** — multi-track audio with proper track split and gapless playback
- **Packed / crunched Amiga files** — StoneCracker, Imploder, Pack-Ice 1.x / 2.1 / 2.31+, ByteKiller + ANC / JEK clones, JAM Packer, PowerPlayer Music Compressor, CrunchMania, PowerPacker, XPK family, DMS, and ~20 more (via ancient 2.3.0)
- **ZIP / RAR / LHA / LZX archives** — audio extracted at add-time via libarchive

**800+ file extensions total.** Open the in-app **Formats Library** panel (*File Info → Open Formats Library*) for the full searchable catalogue with one card per format showing platform, era, decoder library and technical details.

---

## Pro features audiophiles and engineers actually use

### 🔌 ASIO 2.3 + WASAPI Shared / Exclusive — new in v0.36

**ASIO 2.3** is now live (Steinberg ASIO Licensing Agreement signed April 2026). Sub-10 ms round-trip latency through your VST3 chain on any ASIO interface — RME, MOTU, Universal Audio, RME Babyface, Focusrite Scarlett, Steinberg UR, ASIO4ALL, you name it. Pick **ASIO** in *Settings → Audio → Audio Mode*.

- **Output Pair routing** for multi-output interfaces (RME UFX 30 outs, MOTU 16A, Apollo x16) — route the player's stereo to any pair (1-2, 3-4, …) up to the driver's reported total. Persisted across sessions.
- **Configure Driver button** opens the driver's hardware panel directly (RME TotalMix, MOTU CueMix, Apollo Console, ASIO4ALL settings).
- **Driver-reported latency readout** — in N / out N frames + total ms — refreshed live whenever the driver fires `kAsioLatenciesChanged`.
- **Studio-grade output stage** — TPDF dither at canonical ±1 LSB peak (Lipshitz–Vanderkooy 1992) on every integer path, NaN/Inf guards, asymmetric clamps preserving the negative-rail code, full coverage of `ASIOSTInt16/24/32 LSB/MSB` and `Float64MSB`. Mixed-bit-width channel groups (Int32 on analog, Int24 on ADAT, …) route correctly.
- **SEH-safe driver panel calls** + clean reset / latency-change handling so a misbehaving panel can't take out the host.

**WASAPI** Shared and Exclusive modes remain fully supported for users who don't have an ASIO interface — the player auto-picks the device's native sample rate, no system-wide resampling.

### 🎚️ Turntable Pitch Slider (Technics-style) — new in v0.36

A vertical pitch fader on the right edge of the expanded waveform view AND DJ-mode view. **±16 % range**, **0 % center detent** (snaps to neutral within ±0.3 %), and a **33 ⇄ 45 RPM toggle** below the slider — 45 plays the file at native rate, 33 plays it at 33⅓/45 = 0.7407× speed (literal Technics behaviour, both pitch and tempo drop together — no digital time-stretch artefacts).

The audio thread interpolates the ring buffer with a fractional sample-position increment + per-sample ratio ramp. Linear interpolation, no anti-aliasing filter — that's the authentic vinyl character. Pitch stage is BEFORE the VST3 chain, so plugins receive the pitched signal as if it were arriving from a real turntable. Auto-resets to neutral on every track change.

### 📚 Format Library — every supported format, in-app — new in v0.36

A new collapsible **Format Info** card in *File Info* (origin, era, codec, decoder library) for every track, and a full **Formats Library** modal panel with a per-category sidebar, search across name / extensions / platform / developer / decoder, and click-to-expand cards with the complete catalogue entry.

The redesigned **Settings → File Associations** uses the same source-of-truth — collapsible categories with `enabled/total` badges, search box, "Recommended" preset.

### 🎛️ 3-Band EQ (built-in modal dialog)

Low Shelf / Mid Bell / High Shelf with two draggable crossover-frequency handles on a live FFT spectrum and three Low/Mid/High gain knobs — classic hi-fi sweep from 7:30 through 12 o'clock (top, 0 dB) to 4:30. RBJ-cookbook biquads with 5-ms coefficient ramping (no clicks on knob moves). Soft 0 dB detent on bipolar knobs (snaps within ±0.3 dB). Toggle with `Q`.

### 📊 Six real-time visualization modes

- **FFT Spectrum** — indigo hue-swept frequency analyzer, 200 log-bins
- **Spectrogram** — scrolling waterfall
- **Stereo Phase Scope** — Lissajous / goniometer with amplitude-brightening
- **VU Meter** — classic PPM L/R
- **LED HiFi** — 32-band segmented display
- **Frequency Landscape** — 3D waterfall

Plus dedicated **Channel Scopes** (per-channel oscilloscopes for trackers, L/R for stereo), a live **ProTracker-style Pattern View** for `.mod` / `.xm` / `.s3m` / `.it` playback, and the **SID Voices** view for Commodore 64 tunes. Synthesised formats (SID / MIDI / libgme chiptunes) now show a live scrolling oscilloscope just like URL streams.

### 🎚️ Studio Compare (A/B)

Dual-decoder synchronized A/B playback — load two files and switch between them sample-accurately with a 64-sample crossfade. Compare masters, codecs, headphones, plugin chains.

### 🎧 Built-in Bauer-style crossfeed

Smooth your stereo on headphones without a plugin slot. Continuous blend slider, proper gain + delay + lowpass filtering.

### 📼 Gapless playback

Next track is pre-loaded and swapped in sample-accurately across the decoder families that allow it (FLAC→MP3, MOD→XM, cross-format — all work). Mixed-format playlists play back cleanly end-to-end.

### 📁 Integrated file browser & smart-scan

Point it at your music library. Background SQLite cache for VBR durations, bitrates, cover art. Instant playlist building across folders. Breadcrumb navigation, library roots, "Play / Add All" context actions, Favorites tab for quick pinning.

### 💎 Export through your VST3 chain — killer feature

Route **any file or whole playlist** through your VST3 effect chain and render the result to disk. Faster-than-real-time, offline, sample-accurate. Right-click a track in the playlist → **Export to format…** for a single file, or **Ctrl+E** for the full batch dialog.

Export is included in every build — no separate "Pro" tier, no time-limited trial on the export path.

### 🛡️ Plugin crash protection

SEH-wrapped plugin process calls, automatic crash journaling, safe-mode after repeated failures, per-`(path, classID)` blacklist so a single crashing plugin in a multi-class shell (e.g. Waves WaveShell with 600+ effects) doesn't take out the rest. Auto-restart watchdog subprocess.

### ♿ Full keyboard accessibility

Every audio control reachable via Tab + Space / Enter / arrow keys. Output-pair, mode chips, device list all wired as standard radio groups. Settings panel, TransportBar, FileBrowser, FxChain bypass, Playlist tabs all wired — NVDA / Narrator users get a working, labelled keyboard path. Hard CI gate (`qml_a11y_lint`) prevents regressions.

### ⚡ Performance

Native C++20, lock-free audio thread, GPU-accelerated rendering throughout (QSGGeometryNode — no QML Canvas anywhere). r8brain-free-src resampler (260 dB SNR, linear-phase). WASAPI shared or exclusive mode. ~50 MB RAM idle. Startup < 2 s.

---

## What's new in v0.36.7

First public update of the v0.36 cycle. Consolidates everything from v0.36.0 → v0.36.7 (eight internal builds) into one public release. Three headline additions, a redesigned audio path, hundreds of small fixes.

- **ASIO 2.3 — sub-10 ms latency through your VST3 chain.** Steinberg-licensed (April 2026), enabled by default. Output Pair routing for multi-output interfaces. Configure Driver button. Driver-reported latency readout. Studio-grade output stage with TPDF dither and asymmetric clamps across every integer path.
- **Game music + Apple Loops via vgmstream r2083.** ~700 formats — Apple CAF (Logic Pro / GarageBand Apple Loops library), CRI ADX/HCA, Nintendo BRSTM/BCSTM/BFSTM/DSP family, FMOD FSB, Square Enix SCD, Wwise WEM, Xbox XMA, Sony VAG/HPS/NUB. ISC-licensed, no FFmpeg in the default build.
- **50+ tracker formats — runtime-detected** via libopenmpt 0.8.6 (no hardcoded list). The ancient depacker upgraded to v2.3.0 — Pack-Ice 1.x / 2.1 / 2.31+, ByteKiller + ANC / JEK clones, JAM Packer, PowerPlayer Music Compressor, Vice / Vic2 Huffman.
- **Format Library — every supported format, in-app.** New collapsible Format Info card in *File Info* and a full Formats Library modal panel reachable from *File Info → Open Formats Library*. Settings → File Associations redesigned with collapsible categories, search, "Recommended" preset.
- **Turntable Pitch Slider (Technics-style).** ±16 % range, 0 % center detent, 33 ⇄ 45 RPM toggle. Linear-interpolation pitch in the audio thread for the authentic vinyl character. Auto-resets on every track change.
- **Output Device picker redesign.** Backed by a long-lived COM `IMMNotificationClient` listener — devices come and go, the list updates; Windows changes its default render endpoint, the system-default row tracks it. Green LIVE pill marks the row currently producing sound.
- **EQ refinements.** Reset actually moves the knobs back to 12 o'clock (was broken after first interaction). Soft 0 dB detent on bipolar knobs.
- **Test-locked correctness.** Three CTest gates run on every CI push — `test_asio_dither` (55 assertions), `test_audio_backend_types` (21 assertions), `qml_a11y_lint`. The previously-undetected DC-bias bug (≈ -0.5 LSB) would now fail the dither test by 50× the tolerance margin.
- **Qt 6.8.3 LTS upgrade.** Qt floor bumped from 6.5 to 6.8 (LTS until October 2027).
- **Many smaller fixes** — vgmstream sample-count bug (every game-music file silently produced 0 frames in v0.36.0), live waveform for synthesised formats, ASIO + MOD playback crash, vgmstream `.iff` regression, vgmstream race fix on mono sources, `.bnk`/`.txtp` rejection messages, output-device-picker click-drop, decoder short-read percentage in toast, plugin chain restoration ordering, UI scale immediate apply, TFMX gating, SmartScan dedup, log rotation.

See the [v0.36.7 release notes](https://github.com/akustikrausch/FXChainPlayer-Releases/releases/tag/v0.36.7) for the consolidated detail.

---

## What's new in v0.35.12

Three fixes.

- **Bulk folder drop into the playlist no longer runs the decoder
  twice per file.** Adding a folder of uncached mixed-format tracks
  (chiptunes + trackers + MP3s) used to open every file with two
  full decoder lifecycles back-to-back on the UI thread — once for
  the inline duration probe, once via the SmartScan scanner, which
  was meant to be a background worker but was actually synchronous.
  With twenty-plus files and heavy codecs (libgme, libopenmpt, MF
  MIDI fallback) that added up to forty-plus open/close cycles per
  second and on one test machine the heap didn't survive it — the
  app closed without leaving a crash dump, which is the signature
  of heap corruption or exhaustion severe enough to kill the dump
  writer too. A new `ingestInlineProbe` path reuses the first open's
  audio info and only runs TagLib for year / BPM / key, skipping
  the second open entirely. One decoder open per file now.
- **3-Band EQ knobs: 0 dB sits at 12 o'clock on all three knobs.**
  Classic hi-fi knob sweep from 7:30 through 12 o'clock (top, 0 dB)
  to 4:30. Previously the neutral position sat at 3 o'clock, which
  made the knob read as "almost maxed" at a glance.
- **"Clear Playlist" → "Clear All" in the confirmation dialog
  actually clears the playlist.** The button was wired through the
  playlist's filter proxy, and proxies don't expose `clear()` — so
  the click did nothing. Now routes through a dedicated signal to
  the source model and stops playback too, matching single-track
  removal.

Docs, help panel and third-party license list were updated in the
same pass to match the current 3-Band EQ.

---

## What's new in v0.35.11

Big round of UX polish — fifteen fixes, one feature rewrite.

- **3-Band EQ, rewritten from scratch as a modal dialog.** Low Shelf
  / Mid Bell / High Shelf with two draggable crossover-frequency
  handles on a live FFT spectrum, and three Low/Mid/High gain knobs.
  Opens with `Q` or from the status-bar EQ button — no more competing
  with FX or Analyzer for sidebar space. Replaces the old 8-band
  parametric EQ that had known usability issues. RBJ-cookbook biquads
  with 5-ms coefficient ramping — no clicks on knob moves.
- **Waveform-expand gets a flexible sub-panel strip below.** When the
  transport is expanded, press `P`, `E` or `A` to bring Playlist, FX
  Chain or Analyzer back in as a horizontal bar under the waveform.
  Any combination, share the strip width evenly. EQ stays out of the
  strip — its height needs a dialog anyway.
- **UI-scale change auto-restarts the app** (Qt 6.7 has no runtime
  scale API) — no more "Restart Now / Later" dialog, just click
  Apply in Settings and the app relaunches with the new scale.
- **Playlist column headers no longer vanish at full width.** After
  the v0.35.9 auto-fill-width change, the Title / Duration / Bitrate /
  Year / BPM / Key / ★ headers disappeared whenever the playlist
  auto-filled without explicit `Shift+P`. Every column-alignment
  binding now gates on `_effectiveFullWidth`, so headers follow the
  data cells regardless of how the panel ended up wide.
- **File Info dialog polish.** Auto-refreshes when the playlist
  advances to the next track (no stale-metadata state). Long ID3
  Copyright / Encoder / Composer tags cap at 260 px and elide with a
  tooltip (a specific MP3 with a 200-char genre chain was breaking
  the card border). The Genre pill in the header row now caps the
  same way. Duplicate inline ✕ next to the title removed — the
  floating ✕ in the top-right corner is the single close affordance.
- **Reset-View persists to settings.** Pressing the status-bar reset
  button (or `Ctrl+Shift+R`) now writes "Default" into the layout-
  preset file too, so the next app launch actually starts at Default.
  Previously the button appeared to "forget" its effect across
  restarts if you'd picked another preset.
- **Transport-position-aware waveform chevron.** When the transport
  bar is docked at the bottom, the orange Waveform/Close pill's
  chevron points UP on expand (because the waveform grows upwards
  into the window). Flips automatically based on the setting.
- **Plugin loading / unloading spinner renders clean status text.**
  The overlay that shows "Loading plugin..." / "Unloading plugin..."
  during VST loads was centering text in a live-repositioning Column
  that dropped glyphs off the baseline on some font fallbacks — card-
  based fixed layout now, no more garbled characters.
- **Inter-font-weight fallback hardening.** On systems where Inter is
  installed without the optional DemiBold (weight 600) variant, small
  text in the Add Files dialog ("Add N" button, type pills) rendered
  as garbled glyphs because Qt's fallback substitution failed
  visually. Switched to Bold (weight 700, reliable across every Inter
  install). Same change to the file-browser format pill and Play-All
  button.
- **Smaller fixes.** Playlist tabs always show separator lines.
  Status-bar info-icon hides when no file is loaded (click-to-nothing
  removed). Sidebar drag clamps against window width so the right
  stack can never be squeezed invisible. Single waveform-expand entry
  point (the big pill — the small chevron inside the waveform is
  gone). Gapless MOD→MOD tracker transitions don't blank the pattern
  view anymore (tracker provider re-binds on gapless swap). Right-
  click anywhere in the analyzer / pattern view opens the mode menu
  (was a 30-px corner hitbox).

See the [v0.35.11 release notes](https://github.com/akustikrausch/FXChainPlayer-Releases/releases/tag/v0.35.11) for the consolidated list.

---

## What's new in v0.35.10

Consolidated release notes for the whole v0.35 cycle up to v0.35.10
— every improvement listed below is still live in the current build.

### Playlist & library

- **Multi-select.** Click to select, `Ctrl+Click` to toggle, `Shift+Click`
  for a range, `Ctrl+A` selects everything. `Del` removes the whole
  selection in one pass. Works identically in the compact and the
  full-width playlist.
- **Favorites tab (★).** Click the star in any playlist row or
  browser entry to mark a favourite (or press `Ctrl+D` on the focused
  row). A Favorites tab appears next to Playlist / Browse as soon as
  the first one is added. Folder-level favourites cache the directory
  listing at add-time, so *Play All* on a folder works offline.
- **Playlist search.** `Ctrl+F` focuses an inline search field above
  the playlist. Live substring filter across title and path; clear with
  `Esc` or the ✕ button.
- **Full-width playlist with split view.** `Shift+P` (or the chevron
  in the playlist header) expands the playlist to full window width
  and snapshots the current FX / Analyzer state. Enable either from
  within full-width and they drop into a bottom half beneath the
  playlist — one panel takes the full width, both split it 50/50.
  `Shift+P` again smart-restores the panels you had before, or
  preserves what you just turned on if you customised the layout.
- **Auto-fill width when no right-side panel is visible.** Turn off
  FX, Analyzer and EQ while in sidebar mode and the playlist absorbs
  the freed space automatically (animated, 200 ms). Turn a panel back
  on and the playlist shrinks to sidebar width again. No more dark
  empty gap next to a 340-px sidebar.
- **Extended columns (Year / BPM / Key).** Three new sortable columns
  appear on windows ≥ 1400 px wide. Values come from ID3 / Vorbis tags
  first (Year, BPM, INITIALKEY), with filename-regex fallback scored
  by confidence — so `128 - 3A - Energy 52 - Café del Mar.mp3` parses
  correctly even with multiple BPM-shaped numbers in the name.
- **Sort by track index (folder grouping).** Click the `#` header in
  the extended view or right-click → *Sort by Track Index*. Files from
  the same source folder stay together; inside each folder they order
  by numeric prefix independent of separator (`01-` / `01 ` / `01.` /
  `01_` / `(01)`) and zero-padding.
- **★ sort column.** Click the star header in either the playlist or
  the file browser to float favourites to the top.
- **Drag-out to Explorer / Desktop.** Drag selected rows to any folder
  on your machine (or the desktop) to copy the underlying files.
  Multi-selection comes along if the dragged row is part of one;
  streams and CUE sub-tracks skip the drag.
- **Delete File… (Recycle Bin).** New context-menu entry in playlist
  and browser; confirms, then sends the file to the Windows Recycle
  Bin and refreshes playlist / favourites / scan cache in one cascade.
  The existing *Remove from Playlist* stays for pure list management.
- **Arrow-key navigation** across playlist and file browser —
  `↑` / `↓` / `Home` / `End` / `PgUp` / `PgDn` / `Enter`. The global
  Up = Volume-Up / Down = Volume-Down yields to the list while the
  list is focused.
- **Detail-text brightness slider.** *Settings → Interface* lets you
  scale the duration / bitrate / size / date text 60–130 % of the
  theme tertiary grey. Baseline grey bumped from 39 % to 50 %
  brightness too.
- **Sortable file browser.** Name / Format / Size / Date as clickable
  headers; directories always stay on top. Sort preference persists
  across restart. Sidebar drag respects the window width so the right
  stack can't be squeezed invisible on narrow monitors.

### Layout & recovery

- **Named layout presets** in *Settings → Display*:
  - **Default** — sidebar playlist, FX chain, analyzer. The balanced view.
  - **DJ Mode** — full-width playlist, expanded transport docked at
    the bottom, no other panels. Pure deck focus.
  - **Studio Mode** — sidebar playlist with FX chain, parametric EQ,
    analyzer. Everything reachable.
  - **Playlist Mode** — full-width playlist on top, analyzer beneath
    on full width. Library browsing with a visual companion.
  Save your own tweaks as *Custom*; *Reset to Factory Default* snaps
  the running UI live instead of just clearing the file. A small amber
  dot signals when the current view drifts from the saved preset.
- **Reset-View button in the status bar** (`rotate-ccw` icon, next to
  Settings) plus `Ctrl+Shift+R` shortcut. One click returns to the
  Default layout regardless of what state you were in — useful when a
  chain of toggles left panels hidden, the transport stuck expanded,
  or the playlist in a constellation that's hard to back out of.
- **Transport Bar position (Top / Bottom).** *Settings → Interface*.
  Applied live; persists across restart. Status bar still sits at
  the very bottom.

### Format support

- **ZIP / RAR / LHA / LZX archives at add-time.** Drag a `.zip` /
  `.rar` / `.lha` / `.lzh` / `.lzx` onto the playlist and FXChainPlayer
  unpacks every audio entry to a per-archive cache and drops them in.
  Subsequent adds hit the cache instead of re-unpacking. Entries
  older than 30 days are swept on startup. Via **libarchive 3.7.7**.
- **Amiga retro-packers** (StoneCracker SC/S3xx/S4xx, Imploder,
  PackIce, CrunchMania and ~20 more). Gepackte Tracker-Dateien werden
  beim Hinzufügen automatisch entpackt — via **ancient 2.1.x**.
  PowerPacker (PP20), XPK and MMCMP are handled inside libopenmpt
  and have worked since v0.33.
- **More tracker formats.** 30+ retro tracker formats via libopenmpt
  0.8.6 — DigiBooster, DigiTrakker, Imago Orpheus, Graoumf, Liquid
  Tracker, Octalyser, PolyTracker, UltraTracker, X-Tracker,
  Soundtracker Pro II, TCB Tracker, and more.
- **SID song lengths (HVSC).** Drop the HVSC `Songlengths.txt` in
  the right spot (see *Settings → Library*) and SIDs play their
  authored duration from a database of 60 000+ tunes instead of the
  180-second default.
- **MIDI SoundFont auto-pick.** Drop a `.sf2` next to
  `FXChainPlayer.exe`, in `{app}/soundfonts/`, in `{app}/data/`, or
  in `%APPDATA%/FXChainPlayer/soundfonts/` — next launch finds it
  automatically.

### Killer feature: Export through your VST3 chain

Every build includes full batch export through the VST3 effect chain
to WAV (16-bit / 24-bit PCM / 32-bit float) and MP3 (128 / 192 /
320 kbps). Offline, faster-than-real-time, sample-accurate.
Right-click a track in the playlist → *Export to format…* for a
single file, or press `Ctrl+E` for the batch dialog.

- **Bake headphone correction.** Apply Sonarworks / SoundID Reference
  / Beyerdynamic Headphone Lab / Morphit to a playlist and render it
  for on-the-go listening — no correction plugin needed on the
  destination device.
- **Bake spatial audio.** dearVR MONITOR / Waves Nx / Dolby Atmos
  Production Suite produce a binauralized stereo file you can listen
  to with any headphones, any app.
- **Loudness-normalized listening copies** via compressor + limiter
  chain.
- **Format conversion in one pass.** FLAC → MP3 with EQ + dynamics +
  dither baked in, no DAW round-trip, no intermediate files.

**Two export fixes shipped in v0.35.x:** per-slot VST3 wet/dry is
respected in offline export (was always 100 % wet because the mix
buffer was sized to the realtime device block), and SID → MP3 no
longer silently fails when Media Foundation hasn't been initialised
yet.

### Tracker & SID pattern views

- **Live ProTracker-style pattern view** for MOD / XM / S3M / IT and
  all the historical trackers — highlighted row follows the audio,
  not the render-ahead. Right-click the analyzer to switch views.
- **Channel Scopes.** Per-channel oscilloscopes for trackers up to
  four channels; hidden automatically above that.
- **Instrument → Channel split view.** One card per instrument with
  the channels currently triggering it and an aggregated VU — useful
  for XM / IT modules where the same instrument fires across several
  channels.
- **Channel mute.** Click any channel header in the pattern view to
  mute it; right-click a header to un-mute everything. Ring-buffer is
  flushed on toggle so the mute is audible within one WASAPI buffer
  (~21 ms) instead of a second later.
- **Pattern navigation with no lag.** *Next Pattern* / *Previous
  Pattern* snap both audio AND the UI pattern counter within ~20 ms.
- **Pattern view stays populated across gapless transitions.** The
  tracker provider re-binds on every track change, so MOD→MOD /
  XM→XM auto-next no longer leaves the view empty.
- **Right-click works anywhere in the pattern / SID / Scopes view** —
  used to be a 30×30 corner hitbox, now the whole area accepts
  right-clicks for the mode menu while left-clicks still reach the
  view's own interactive elements.
- **SID Voices:** per-voice mute (1 / 2 / 3), chip-model toggle
  (6581 / 8580 / auto), filter bypass. Full voice-header is clickable
  for mute (was a tiny badge). Filter-state row is labelled as a live
  readout of the SID registers, not a control. Tooltips explain when
  the chip-model and filter toggles are actually audible (many tunes
  don't route through the filter at all).
- **Hi_Fi_Sky and friends start instantly** — the 3 s of silence and
  two clicks during cRSID's chip-setup phase are gone. Soft-start
  ramp + EMA-based sustained-signal detector.

### File Info panel

- **AUDIO + TRACKER MODULE / DSD STREAM / SID TUNE sections render
  first**, above the song-info tag card. For trackers the tag card
  is often empty anyway — the technical data you came for is now
  above the fold.
- **Floating ✕ close button in the top-right corner** (matches the
  About panel) — always visible, no scrolling to the bottom to close.
- **No more duplicate sample list for MOD / XM / S3M / IT.** TagLib
  synthesised the "comment" field from sample names, which then
  rendered once unformatted above the formatted SAMPLES box and
  once in the box. Skipped for tracker formats now.

### Reliability

- **Gapless tracker→tracker crash fixed.** A decoder/UI-thread race
  around the libopenmpt module lifetime could crash the app after
  ~20 back-to-back MOD / XM / S3M / IT transitions in a playlist.
  Destroy and pattern-view read are now mutually exclusive.
- **Plugin crash isolation per `(path, classID)`** — a single
  crashing plugin in a multi-class shell like Waves WaveShell (600+
  effects) doesn't take out the rest. Automatic safe mode after
  repeated failures.
- **Crash guard for file scanning** — scanning large folders with
  broken / malformed files no longer blows up the app.
- **Playlist auto-recovery** on failed track load — player state
  clears, next track plays, export skips URL streams cleanly.
- **Session restoration** on relaunch (crash or normal).
- **Restart-from-app.** *About → Quick Access → Restart Application*.
- **Firewall-friendly first-run update prompt.** On the very first
  launch the app asks yes/no whether to check for updates on startup,
  before any network request fires — so the firewall prompt appears
  while the welcome popup is still in focus.

### Small refinements

- **Interactive graphic EQ.** 8 parametric bands as a GPU-accelerated
  frequency-response curve. Click and drag bands directly on the
  curve, scroll-wheel for Q, `Shift` snaps to 1/3 octaves and the
  standard dB grid. Stereo-linked and mid/side modes. Pre/post FX
  chain placement.
- **Context-menu highlight readable everywhere.** Nine right-click
  menus (playlist, analyzer, peak meter, FX slot, transport, file
  browser, VST browser, empty areas) routed through a shared styled
  component — soft grey highlight, no more white-on-white text on
  any Windows theme / DPI combination.
- **Status bar cleanup.** Output cluster (Mute / Volume / %) sits
  next to FX Bypass, before the navigation buttons. L / R peak
  meters, CPU bar and Volume % are all fixed-width so the row
  doesn't jitter when digits cross a boundary. Info-icon next to
  the track name hides when nothing is loaded — the cell used to
  accept clicks that did nothing.
- **Playlist tabs** (Playlist / Favorites / Browse) always show the
  separator lines — a previous revision faded them depending on the
  active tab, which read as "divider here but not there".
- **Single waveform-expand entry point.** The big orange "Waveform"
  pill with text label is the only visible expand control now — the
  small chevron-down inside the waveform itself is gone. `T` and
  double-click on the waveform still work as hidden shortcuts.
- **Chevron tooltip** on the playlist header explains that FX and
  Analyzer dock below the full-width playlist.
- **Gradient pass.** Subtle top-lit gradients on primary CTAs (Play
  button, Add to Playlist, Update Now, active tab pills). Peak / CPU
  meters pick up zone-aware gradients. Play button back to solid blue
  accent with gradient overlay for depth.

### Architecture note

v0.35.x introduced an "any-visible-region-must-have-content" invariant
for the main window layout. Toggle combinations that used to leave
340-px sidebars next to empty black panes or waveforms stuck at 20 px
now animate into usable states automatically. The full state-space
analysis lives in `docs/dev/LAYOUT_UX_PLAN_v0.35.9.md` in the source
tree for developers curious about the design.

---

## Download

**[⬇ Latest installer on GitHub](https://github.com/akustikrausch/FXChainPlayer-Releases/releases/latest)**

One installer, one click: `FXChainPlayer-Setup-X.Y.Z.exe` (Inno Setup). Full install with file associations, Start menu entries, uninstaller. All required Qt DLLs and the VST3 host process are included.

### Auto-update

FXChainPlayer checks GitHub Releases for new versions and offers one-click install with SHA-256 verification. Toggle in *Settings → Updates*.

---

## System Requirements

- **Windows 10** or **Windows 11**, 64-bit
- ~100 MB disk space
- An audio output device (WASAPI — any built-in sound, USB DAC, or HDMI audio works; ASIO 2.3 supported on any compliant interface)
- Optionally: a VST3 plugin folder with your favorite effects

---

## Supported plugins

FXChainPlayer is a **VST3 host** (not VST2). Any 64-bit VST3 effect plugin should work. Tested heavily with:

- **FabFilter** (Pro-Q 3/4, Pro-C 2, Pro-L 2, Saturn 2, …)
- **Waves** WaveShell (including multi-class shells)
- **iZotope** Ozone, RX, Nectar
- **Sonarworks** SoundID Reference
- **Tokyo Dawn Labs** (Nova GE, Kotelnikov, Proximity)
- **Valhalla DSP** (VintageVerb, Room, Supermassive)
- **Acon Digital**, **Softube**, **Kirchhoff-EQ**, **Pro-MB**, **Dear Reality dearVR**, **Beyerdynamic Headphone Lab**, and many others.

Instruments (VSTi) are filtered out automatically — FXChainPlayer is a playback tool, not a DAW.

---

## License

FXChainPlayer is proprietary software by **Andreas Wendorf (Akustikrausch)**.

The binaries use and statically/dynamically link the following open-source components (with full LGPL / BSD / MIT attribution in the About dialog inside the app): Qt 6, VST3 SDK, dr_libs, stb_vorbis, libopenmpt, libgme (Game Music Emu), cRSID, TinySoundFont, WavPack, Monkey's Audio SDK, libmpcdec, libtta++, r8brain-free-src, TagLib, SQLite, pugixml, MurmurHash3, nlohmann/json, spdlog, libarchive, ancient, vgmstream (ISC), zlib.

ASIO is a trademark and software of Steinberg Media Technologies GmbH. FXChainPlayer uses the Steinberg ASIO Interface Technology under the Steinberg ASIO Licensing Agreement signed by Akustikrausch (Andreas Wendorf, April 2026). The Steinberg ASIO SDK source code is NOT redistributed with this product.

---

## Community

Join the FXChainPlayer Discord for questions, feedback, plugin recommendations, and bug reports: **<https://discord.gg/sfHBZFhG>**

## Links

- **Latest release:** https://github.com/akustikrausch/FXChainPlayer-Releases/releases/latest
- **Discord:** https://discord.gg/sfHBZFhG
- **Author:** [Andreas Wendorf / Akustikrausch](https://github.com/akustikrausch)

---

<p align="center"><em>Tools disappear. Music remains.</em></p>
