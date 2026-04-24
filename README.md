<h1 align="center">FXChainPlayer</h1>

<p align="center"><strong>A Windows desktop audio player with a full VST3 effect chain built into the playback engine.</strong></p>

<p align="center">
  <a href="https://github.com/akustikrausch/FXChainPlayer-Releases/releases/download/v0.35.8/FXChainPlayer-Setup-0.35.8.exe"><img src="https://img.shields.io/badge/Download-v0.35.8-0078D6" alt="Download v0.35.8"></a>
  <img src="https://img.shields.io/badge/platform-Windows%2010%2F11-0078D6" alt="Windows 10/11">
  <img src="https://img.shields.io/badge/VST3-supported-brightgreen" alt="VST3">
  <img src="https://img.shields.io/badge/80%2B%20formats-FLAC%20%C2%B7%20DSD%20%C2%B7%20MOD%20%C2%B7%20SID%20%C2%B7%20Chiptunes-blue" alt="80+ formats">
</p>

<p align="center"><em>Load your favorite plugins — EQs, compressors, reverbs, spatial processors, headphone correction — directly into the signal path and hear them in real time while you listen to music. No DAW required.</em></p>

<p align="center"><a href="https://github.com/akustikrausch/FXChainPlayer-Releases/releases/download/v0.35.8/FXChainPlayer-Setup-0.35.8.exe"><strong>⬇ Download FXChainPlayer-Setup-0.35.8.exe</strong></a></p>

---

## What's new in v0.35.8

Follow-up fixes on top of the v0.35 feature drop.

- **Gapless tracker→tracker crash fixed.** Queueing MOD / XM / S3M /
  IT modules back-to-back could crash after ~20 transitions due to
  a decoder/UI thread race around the libopenmpt module lifetime.
  Destroy and pattern-view read are now mutually exclusive — no
  more dangling-pointer deref.
- **VST3 per-slot wet/dry mix respected in offline export.** Setting
  a chain slot to 60 % wet and exporting to MP3 used to render as
  100 % wet because the mix buffer was sized to the real-time
  audio-device block. Exports now sound the same as real-time
  playback, regardless of device buffer size.
- **Playlist Mode preset now splits playlist + analyzer 50/50.** The
  preset sometimes left the analyzer covering the whole window with
  no playlist visible; fixed by matching explicit preferred heights
  on both rows.
- **Playlist column headers stay over their columns at every width.**
  A trailing fillWidth spacer in both the header and delegate rows
  absorbs leftover space deterministically past the ~1400 px
  breakpoint — header labels and data columns stay aligned. Also
  carries forward the v0.35.7 scroll-bar-reserve fix (header and
  delegate both reserve the 14 px overlay area).
- **Context-menu highlight readable across every menu.** All nine
  right-click menus (playlist, analyzer, peak meter, FX slot,
  transport, file browser, VST browser, empty areas) now use a
  shared styled component with a consistent soft-grey selection
  highlight — no more white-on-white text on any Windows theme /
  DPI combination.

See the [v0.35.8 release notes](https://github.com/akustikrausch/FXChainPlayer-Releases/releases/tag/v0.35.8) for the full list.

---

## What's in the v0.35 cycle

### Layout you can actually shape

- **Named layout presets.** Pick *Default*, *DJ Mode*, *Studio Mode*
  or *Playlist Mode* from *Settings → Display*, or save your own as
  *Custom*. The app restores your choice on every launch.
  - **Default** — sidebar playlist, FX chain, analyzer. The
    balanced view.
  - **DJ Mode** — full-width playlist, expanded transport docked at
    the bottom, no other panels. Pure deck focus.
  - **Studio Mode** — sidebar playlist with FX chain, parametric
    EQ, and the analyzer all visible. Everything reachable.
  - **Playlist Mode** — full-width playlist on top, analyzer
    beneath on full width. Library browsing with a visual companion.
- **Full-width playlist with split view.** Pressing `Shift+P` (or
  the chevron in the playlist header) expands the playlist to the
  full window width and hides FX / Analyzer for clean focus. Re-
  enable either from within full-width and they appear in a bottom
  half beneath the playlist — one panel takes the full width, both
  split it 50/50. Pressing `Shift+P` again smart-restores the
  panels you had before.
- **Playlist search.** `Ctrl+F` focuses an inline search field
  above the playlist. Live substring filter across title and
  path; clear with `Esc` or the X button.
- **Extended playlist columns.** Year, BPM, Key in addition to
  Bitrate, Rate, Size, Date on wide windows. Click any header to
  sort; click the ★ to sort by Favorites first.

### New formats and format handling

- **ZIP / RAR / LHA / LZX archives** at add-time — libarchive
  extracts the audio in-place. Matches how users actually store
  scene releases and demoscene packs.
- **Amiga retro-packers** (StoneCracker, Imploder, PackIce,
  CrunchMania) on MOD / XM / S3M / IT files — the ancient library
  handles the de-pack transparently. Drag a `.pp` or packed `.mod`
  onto the window and it just plays.
- **More tracker formats** — 30+ retro tracker formats now covered
  via libopenmpt 0.8.6 (DigiBooster, DigiTrakker, Imago Orpheus,
  Graoumf, Liquid Tracker, Octalyser, PolyTracker, UltraTracker,
  X-Tracker, Soundtracker Pro II, TCB Tracker, …).
- **SID song lengths (HVSC).** Drop the HVSC `Songlengths.txt` in
  the right spot (see *Settings → Library*) and SIDs play their
  actual authored duration from a database of 60 000+ tunes instead
  of the 180 s default.

### Tracker modules: pattern view, mutes, navigation

- **Live ProTracker-style pattern view** for `.mod` / `.xm` / `.s3m`
  / `.it` / all the historical trackers — highlighted row follows
  the audio, not the render-ahead. Right-click the analyzer to
  switch views.
- **Channel Scopes.** Per-channel oscilloscopes for trackers up to
  four channels; the view hides itself for higher channel counts
  where it would be illegible.
- **Instrument → Channel split view.** Shows one card per
  instrument with the channels currently triggering it and an
  aggregated VU — useful for XM / IT modules where the same
  instrument fires across several channels.
- **Channel mute on trackers.** Toggle channels inside the
  pattern view; ring-buffer is flushed so the mute is audible
  within one WASAPI buffer instead of a second later.
- **Pattern navigation with no lag.** "Next Pattern" / "Previous
  Pattern" now snap both the audio and the UI pattern counter
  within ~20 ms of the button press (was up to a second).

### Killer feature: Export through your VST3 chain

Every build includes full **batch export** through the VST3
effect chain to WAV (16-bit PCM / 24-bit PCM / 32-bit float) and
MP3 (128 / 192 / 320 kbps). Offline, faster-than-real-time,
sample-accurate. Right-click a track in the playlist →
*Export to format…* for a single file, or press `Ctrl+E` for the
batch dialog.

- **Bake headphone correction.** Apply Sonarworks / SoundID
  Reference / Beyerdynamic Headphone Lab / Morphit to a playlist
  and render it for on-the-go listening — no correction plugin
  needed on the destination device.
- **Bake spatial audio.** dearVR MONITOR / Waves Nx / Dolby
  Atmos Production Suite produce a binauralized stereo file you
  can listen to with any headphones, any app.
- **Loudness-normalized listening copies.** Compressor + limiter
  chain → uniform playback level, works everywhere afterward.
- **Format conversion with processing in one pass.** FLAC → MP3
  with EQ + dynamics + dither baked in, no DAW round-trip, no
  intermediate files.

In this release: **SID → MP3 export fixed** (Media Foundation
was not always initialized, causing silent failures; now
bootstrapped on demand). Unusual device sample rates
(88.2 / 96 / 192 kHz) are snapped to 32 / 44.1 / 48 kHz for the
MP3 encoder via r8brain (260 dB SNR).

### UI polish

- **Interactive graphic EQ.** 8 parametric bands rendered as a
  GPU-accelerated frequency-response curve. Click and drag bands
  directly on the curve, scroll-wheel for Q, `Shift` snaps to
  1/3 octaves and standard dB grid. Stereo-linked and mid/side
  modes. Pre/post FX chain placement.
- **Favorites tab** (★) alongside Playlist and Browse. `Ctrl+D`
  toggles favourite on the current track; the ★ column in the
  playlist reflects live state.
- **Drag-out to Explorer / Desktop.** Drag selected playlist rows
  out of the window to copy the underlying files.
- **File Info panel reorganised** — AUDIO + TRACKER MODULE /
  DSD STREAM / SID TUNE sections render first now; the song-info
  tag card (mostly empty for trackers and SIDs anyway) follows
  below, where it no longer pushes the technical data out of the
  visible area.
- **True file delete** via the Windows Recycle Bin (not just
  a playlist remove).
- **Arrow-key navigation** across playlist and file browser.
- **Status-bar** cleanup — output cluster (Mute / Volume / %) sits
  next to FX Bypass, before the navigation buttons; L / R peak
  meters, CPU bar and Volume % are all fixed-width so the row no
  longer jitters when a digit crosses a boundary.

### Reliability

- **Plugin crash isolation** per `(path, classID)` — a single
  crashing plugin in a multi-class shell like Waves WaveShell
  (600+ effects) doesn't take out the rest. Automatic safe mode
  after repeated failures.
- **Crash guard for file scanning** — scanning large folders
  with broken / malformed tracker files no longer blows up the
  app.
- **Playlist auto-recovery** on failed track load — player state
  clears, next track plays, export skips URL streams cleanly.
- **Session restoration** when the app is relaunched (crash or
  normal).

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
- **💎 Bake the effect chain into a file** — render any track or the whole playlist through the VST chain to WAV / MP3 / FLAC / OGG, faster than real-time. Take your processed audio anywhere. [Details above](#killer-feature-export-through-your-vst3-chain).

Up to **8 VST3 plugins in a serial chain**. Drag-and-drop reorder. Per-slot bypass and dry/wet. Smooth global chain mix. Native plugin GUIs. Everything runs at **64-bit double precision** end-to-end.

---

## Plays pretty much everything

FXChainPlayer is built for music listeners who don't want format juggling. Drop a folder with mixed FLAC, MP3, tracker files, C64 SIDs, and Game Boy chiptunes — it just plays.

### Lossless & Hi-Res

**FLAC**, **WAV**, **WavPack** `.wv`, **ALAC** (Apple Lossless), **APE** (Monkey's Audio), **TTA** (True Audio), **AIFF**, **Opus**, **W64** (Sony Wave64), **DSD** `.dsf` / `.dff` (DSD64/128/256/512).

### Lossy

**MP3**, **AAC**, **M4A** / **MP4** audio, **OGG Vorbis**, **WMA**, **MPC** (Musepack SV8), **AC-3**.

### Tracker modules (35+ formats via libopenmpt)

**MOD** (ProTracker), **XM** (FastTracker 2), **S3M** (ScreamTracker 3), **IT** (Impulse Tracker), **MPTM** (OpenMPT), **Digibooster Pro**, **Imago Orpheus**, **Graoumf Tracker**, **Liquid Tracker**, **Octalyser**, **PolyTracker**, **UltraTracker**, **Digitrakker**, **OctaMED**, **Farandole Composer**, **Epic MegaGames MASI**, **MadTracker 2**, **Galaxy Sound System**, **X-Tracker**, **Soundtracker Pro II**, **TCB Tracker**, and many more.

### Console chiptunes (via libgme)

- **GBS** — Nintendo Game Boy
- **SPC** — Super Nintendo (SPC700)
- **VGM / VGZ** — Sega Megadrive · 32X · Master System · Game Gear · Mega CD · SG-1000 · SC-3000 · BBC Micro · ColecoVision
- **AY** — ZX Spectrum · Amstrad CPC (AY-3-8910)
- **NSF / NSFE** — Nintendo Entertainment System
- **KSS** — MSX
- **HES** — PC Engine / TurboGrafx-16
- **SAP** — Atari 8-bit
- **GYM** — Sega Genesis / Mega Drive

### Retro / specialty

- **SID** — Commodore 64 (cRSID emulator, HVSC Songlengths support — 60 000+ tune durations built-in)
- **IFF 8SVX** — Amiga samples
- **MIDI** / **RMI** — SoundFont 2 (SF2) rendering via TinySoundFont, with Windows Media Foundation fallback
- **CUE sheets** — multi-track audio with proper track split and gapless playback
- **Packed / crunched Amiga files** — StoneCracker, Imploder, PackIce, CrunchMania unpacked transparently
- **ZIP / RAR / LHA / LZX archives** — audio extracted at add-time via libarchive

**80+ file extensions total.** If you throw something at it, chances are it plays.

---

## Pro features audiophiles and engineers actually use

### 🎛️ 8-band parametric EQ (built-in, pre/post FX chain)
FabFilter-style interactive graphic control on a GPU-accelerated frequency response curve. Click and drag bands directly on the curve, scroll-wheel for Q, Shift-snap to 1/3 octaves and standard dB values. RBJ biquad filters (peak, shelf, pass, notch). Stereo-linked and mid/side modes. Preset save/load. Toggle with `Q`. Zero latency, lock-free.

### 📊 Six real-time visualization modes
- **FFT Spectrum** — indigo hue-swept frequency analyzer, 200 log-bins
- **Spectrogram** — scrolling waterfall
- **Stereo Phase Scope** — Lissajous / goniometer with amplitude-brightening
- **VU Meter** — classic PPM L/R
- **LED HiFi** — 32-band segmented display
- **Frequency Landscape** — 3D waterfall

Plus dedicated **Channel Scopes** (per-channel oscilloscopes for trackers, L/R for stereo), a live **ProTracker-style Pattern View** for `.mod` / `.xm` / `.s3m` / `.it` playback, and the **SID Voices** view for Commodore 64 tunes.

### 🎚️ Studio Compare (A/B)
Dual-decoder synchronized A/B playback — load two files and switch between them sample-accurately with a 64-sample crossfade. Compare masters, codecs, headphones, plugin chains.

### 🎧 Built-in Bauer-style crossfeed
Smooth your stereo on headphones without a plugin slot. Continuous blend slider, proper gain + delay + lowpass filtering.

### 📼 Gapless playback
Next track is pre-loaded and swapped in sample-accurately across the decoder families that allow it (FLAC→MP3, MOD→XM, cross-format — all work). Mixed-format playlists play back cleanly end-to-end.

### 📁 Integrated file browser & smart-scan
Point it at your music library. Background SQLite cache for VBR durations, bitrates, cover art. Instant playlist building across folders. Breadcrumb navigation, library roots, "Play / Add All" context actions, Favorites tab for quick pinning.

### 💎 **Export through your VST3 chain — killer feature**

Route **any file or whole playlist** through your VST3 effect chain and render the result to disk. Faster-than-real-time, offline, sample-accurate. Right-click a track in the playlist → **Export to format…** for a single file, or **Ctrl+E** for the full batch dialog.

Export is included in every build — no separate "Pro" tier, no time-limited trial on the export path.

### 🛡️ Plugin crash protection
SEH-wrapped plugin process calls, automatic crash journaling, safe-mode after repeated failures, per-`(path, classID)` blacklist so a single crashing plugin in a multi-class shell (e.g. Waves WaveShell with 600+ effects) doesn't take out the rest. Auto-restart watchdog subprocess.

### ⚡ Performance
Native C++20, lock-free audio thread, GPU-accelerated rendering throughout (QSGGeometryNode — no QML Canvas anywhere). r8brain-free-src resampler (260 dB SNR, linear-phase). WASAPI shared or exclusive mode. ~50 MB RAM idle. Startup < 2 s.

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
- An audio output device (WASAPI — any built-in sound, USB DAC, or HDMI audio works)
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

The binaries use and statically/dynamically link the following open-source components (with full LGPL / BSD / MIT attribution in the About dialog inside the app): Qt 6, VST3 SDK, dr_libs, stb_vorbis, libopenmpt, libgme (Game Music Emu), cRSID, TinySoundFont, WavPack, Monkey's Audio SDK, libmpcdec, libtta++, r8brain-free-src, TagLib, SQLite, pugixml, MurmurHash3, nlohmann/json, spdlog, libarchive, ancient, zlib.

---

## Community

Join the FXChainPlayer Discord for questions, feedback, plugin recommendations, and bug reports: **<https://discord.gg/sfHBZFhG>**

## Links

- **Latest release:** https://github.com/akustikrausch/FXChainPlayer-Releases/releases/latest
- **Discord:** https://discord.gg/sfHBZFhG
- **Author:** [Andreas Wendorf / Akustikrausch](https://github.com/akustikrausch)

---

<p align="center"><em>Tools disappear. Music remains.</em></p>
