<h1 align="center">FXChainPlayer</h1>

<p align="center"><strong>A Windows desktop audio player with a full VST3 effect chain built into the playback engine.</strong></p>

<p align="center">
  <a href="https://github.com/akustikrausch/FXChainPlayer-Releases/raw/main/downloads/FXChainPlayer-Setup-0.33.6.exe"><img src="https://img.shields.io/badge/Download-v0.33.6-0078D6" alt="Download v0.33.6"></a>
  <img src="https://img.shields.io/badge/platform-Windows%2010%2F11-0078D6" alt="Windows 10/11">
  <img src="https://img.shields.io/badge/VST3-supported-brightgreen" alt="VST3">
  <img src="https://img.shields.io/badge/80%2B%20formats-FLAC%20%C2%B7%20DSD%20%C2%B7%20MOD%20%C2%B7%20SID%20%C2%B7%20Chiptunes-blue" alt="80+ formats">
</p>

<p align="center"><em>Load your favorite plugins — EQs, compressors, reverbs, spatial processors, headphone correction — directly into the signal path and hear them in real time while you listen to music. No DAW required.</em></p>

<p align="center"><a href="https://github.com/akustikrausch/FXChainPlayer-Releases/raw/main/downloads/FXChainPlayer-Setup-0.33.6.exe"><strong>⬇ Download FXChainPlayer-Setup-0.33.6.exe</strong></a></p>

---

## What's new in v0.33.6 (April 2026)

- **New download location.** The installer is now served directly from this project repository rather than from a release page. The download button above points at the current file. The in-app update check has been adjusted to match; from v0.33.6 onward, updates install through the app's built-in updater as usual.
- **One-time manual step for v0.33.5 and older users.** Because the download URL changed, the in-app update check in v0.33.5 and earlier can no longer see this release. Please download v0.33.6 once using the button above and run the installer. After that, the built-in updater works again for all future versions.

Earlier in v0.33.5:

- **Update check display fixed.** The About panel no longer briefly shows *"Up to date"* before the update banner appears.
- **Log folder size bounded** to at most two files (current + previous session).

Earlier in v0.33.4:

- **Per-track export from the playlist.** Right-click → *Export to format…* opens the render dialog with just the selected track.
- **Export progress in the status bar**, visible while a render is running.
- **Clearer errors when a track fails to play.**
- **Tracker Pattern view fixed.** The view rendered as a black panel in earlier builds.
- **Channel Scopes is hidden for tracker modules with more than 4 channels** while a dedicated multi-channel layout is in development.

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
- **SGC** — Sega SG-1000
- **GYM** — Sega Genesis / Mega Drive

### Retro / specialty

- **SID** — Commodore 64 (cRSID emulator, HVSC Songlengths support — 60 000+ tune durations built-in)
- **IFF 8SVX** — Amiga samples
- **MIDI** / **RMI** — SoundFont 2 (SF2) rendering via TinySoundFont, with Windows Media Foundation fallback
- **CUE sheets** — multi-track audio with proper track split and gapless playback

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

Plus dedicated **Channel Scopes** (per-channel oscilloscopes for trackers, L/R for stereo) and a live **ProTracker-style Pattern View** for `.mod` / `.xm` / `.s3m` / `.it` playback.

### 🎚️ Studio Compare (A/B)
Dual-decoder synchronized A/B playback — load two files and switch between them sample-accurately with a 64-sample crossfade. Compare masters, codecs, headphones, plugin chains.

### 🎧 Built-in Bauer-style crossfeed
Smooth your stereo on headphones without a plugin slot. Continuous blend slider, proper gain + delay + lowpass filtering.

### 📼 Gapless playback
Next track is pre-loaded and swapped in sample-accurately across the decoder families that allow it (FLAC→MP3, MOD→XM, cross-format — all work). Mixed-format playlists play back cleanly end-to-end.

### 📁 Integrated file browser & smart-scan
Point it at your music library. Background SQLite cache for VBR durations, bitrates, cover art. Instant playlist building across folders. Breadcrumb navigation, library roots, "Play / Add All" context actions.

### 💎 **Export through your VST3 chain — killer feature**

Route **any file or whole playlist** through your VST3 effect chain and render the result to disk. Faster-than-real-time, offline, sample-accurate. Right-click a track in the playlist → **Export to format…** for a single file, or **Ctrl+E** for the full batch dialog.

This is what most audio players can't do. Some concrete use cases:

- **Bake your headphone correction into a file.** Apply Sonarworks / SoundID Reference / Beyerdynamic Headphone Lab / Morphit to a playlist and render it for on-the-go listening on a phone or portable player — no need for the correction plugin on the destination.
- **Loudness-normalized listening copies.** A compressor + limiter chain applied to an inconsistent album → uniform playback level, works on any device afterward.
- **Mastering test prints.** Run a master through your client's playback chain (their EQ curve, their monitoring profile) and A/B the result outside the DAW.
- **Spatial-audio baked captures.** dearVR MONITOR, Waves Nx or Dolby Atmos Production Suite produce a binauralized stereo file you can listen back to with any headphones, any app.
- **Format conversion with processing in one pass.** Convert FLAC → WAV / MP3 / OGG while simultaneously applying EQ, dynamics and dither — no DAW round-trip, no intermediate files.
- **Demo / preview versions.** Apply saturation, tape emulation or a creative chain to a track for a quick demo render.

Export is included in every build — no separate "Pro" tier, no time-limited trial on the export path.

### 🛡️ Plugin crash protection
SEH-wrapped plugin process calls, automatic crash journaling, safe-mode after repeated failures, per-`(path, classID)` blacklist so a single crashing plugin in a multi-class shell (e.g. Waves WaveShell with 600+ effects) doesn't take out the rest. Auto-restart watchdog subprocess.

### ⚡ Performance
Native C++20, lock-free audio thread, GPU-accelerated rendering throughout (QSGGeometryNode — no QML Canvas anywhere). r8brain-free-src resampler (260 dB SNR, linear-phase). WASAPI shared or exclusive mode. ~50 MB RAM idle. Startup < 2 s.

---

## Screenshots

> *Coming soon — main window, FX chain, spectrum analyzer, tracker pattern view.*

---

## Download

**[⬇ Latest release on GitHub](https://github.com/akustikrausch/FXChainPlayer-Releases/raw/main/downloads)**

Two distribution options:

- **Installer** — `FXChainPlayer-Setup-X.Y.Z.exe` (recommended). Full install with file associations, Start menu entries, uninstaller.
- **Portable ZIP** — `FXChainPlayer-vX.Y.Z.zip`. Unpack anywhere, run. Stores settings in the app folder.

Both include all required Qt DLLs and the VST3 host process.

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

The binaries use and statically/dynamically link the following open-source components (with full LGPL / BSD / MIT attribution in the About dialog inside the app): Qt 6, VST3 SDK, dr_libs, stb_vorbis, libopenmpt, libgme (Game Music Emu), cRSID, TinySoundFont, WavPack, Monkey's Audio SDK, libmpcdec, libtta++, r8brain-free-src, TagLib, SQLite, pugixml, MurmurHash3, nlohmann/json, spdlog.

---

## Links

- **Latest release:** https://github.com/akustikrausch/FXChainPlayer-Releases/raw/main/downloads
- **Author:** [Andreas Wendorf / Akustikrausch](https://github.com/akustikrausch)

---

<p align="center"><em>Tools disappear. Music remains.</em></p>
