<h1 align="center">FXChainPlayer</h1>

<p align="center"><strong>A Windows desktop audio player with a full VST3 effect chain built into the playback engine — and a complete dual-deck DJ Mode.</strong></p>

<p align="center">
  <a href="https://github.com/akustikrausch/FXChainPlayer-Releases/releases/download/v0.46.2/FXChainPlayer-Setup-0.46.2.exe"><img src="https://img.shields.io/badge/Download-v0.46.2-0078D6" alt="Download v0.46.2"></a>
  <img src="https://img.shields.io/badge/platform-Windows%2010%2F11-0078D6" alt="Windows 10/11">
  <img src="https://img.shields.io/badge/VST3-16%20slots%20%C2%B7%20per--channel%20chains-brightgreen" alt="VST3 16 slots + per-channel chains">
  <img src="https://img.shields.io/badge/WASAPI-Shared%20%2B%20Exclusive-blueviolet" alt="WASAPI Shared + Exclusive">
  <img src="https://img.shields.io/badge/ASIO%202.3-Steinberg%20licensed-orange" alt="ASIO 2.3">
  <img src="https://img.shields.io/badge/DJ%20Mode-dual--deck%20%C2%B7%20vinyl%20scratch%20%C2%B7%20sync-ff5555" alt="DJ Mode beta">
  <img src="https://img.shields.io/badge/1500%2B%20formats-FLAC%20%C2%B7%20DSD%20%C2%B7%20MOD%20%C2%B7%20SID%20%C2%B7%20Game%20Music%20%C2%B7%20Apple%20Loops-blue" alt="1500+ formats">
</p>

<p align="center"><em>Load your favorite plugins — EQs, compressors, reverbs, spatial processors, headphone correction — directly into the signal path and hear them in real time while you listen to music. Pitch records like vinyl. Mix tracks across two decks with sync, hot cues, loops and Pioneer-DJM-style filter. No DAW required.</em></p>

<p align="center"><a href="https://github.com/akustikrausch/FXChainPlayer-Releases/releases/download/v0.46.2/FXChainPlayer-Setup-0.46.2.exe"><strong>⬇ Download FXChainPlayer-Setup-0.46.2.exe</strong></a></p>

<p align="center">
  <img src="screenshots/fx-chain-waveform-spectrum.png" alt="FXChainPlayer main view — expanded waveform with VST3 FX Chain (Enrage, beyerdynamic Headphone Lab) and the LED HiFi spectrum analyzer">
</p>

---

## Why VST3 in an audio player?

More reasons than you'd expect.

- **🎧 Headphone surround & spatial audio** — Run binauralizers like **dearVR MONITOR**, **Waves Nx**, or **Dolby Atmos Production Suite** to turn stereo into a full spatial soundstage on any pair of headphones. No system-wide wrapper, no virtual audio cable.
- **🎚️ Headphone calibration & correction** — Use frequency-response plugins like **Sonarworks SoundID Reference**, **Beyerdynamic Headphone Lab**, **Waves Nx Virtual Mix Room**, or **Morphit** to flatten your specific headphone model to a neutral reference.
- **📻 Internet radio & streaming cleanup** — Load a compressor, EQ, de-esser, or multiband processor on poorly-mastered streams or dynamic-range-compressed "loudness war" tracks to tame them while you listen.
- **🔌 Plugin auditioning** — Want to hear how that new reverb, saturator, or tape emulation sounds on real music? Drop it in. No DAW boot-up, no empty session, no audio import.
- **🔊 Loudness normalization & limiting** — Keep playback levels consistent across tracks from wildly different sources (old CDs vs. modern streaming).
- **🏠 Room correction** — Apply convolution IRs or parametric EQ profiles to compensate for your listening room and speaker setup.
- **🅰️🅱️ A/B plugin comparison** — Quickly toggle effects in and out on familiar reference tracks to hear exactly how they color the sound.
- **♿ Accessibility** — Hearing aid profiles, frequency boosting, dynamic range compression, or custom EQ curves for listeners who need tailored audio processing.
- **🎛️ Mix referencing** — Drop your mix in, compare A/B against a reference master, hear your monitor chain on someone else's material.
- **🎚️ Per-channel chains for trackers, SIDs, multi-channel chiptunes** — Each channel of a `.mod` / `.xm` / `.it` / SID / NSF file gets its OWN VST3 chain. Reverb only on channel 1, LP filter only on the bass channel, distortion only on the lead. Configure once per file (CRC32-keyed auto-load), bake into the export.
- **💾 Bake the effect chain into a file** — render any track or the whole playlist through the VST chain to WAV / MP3 / FLAC / OGG, faster than real-time. Take your processed audio anywhere. [Details below](#export-through-your-vst3-chain).

Up to **16 VST3 plugins in a serial chain** (was 8 pre-v0.45.0). Drag-and-drop reorder. Per-slot bypass and dry/wet. Smooth global chain mix. Native plugin GUIs. Everything runs at **64-bit double precision** end-to-end.

---

## DJ Mode — beta

Press `D` (or click the DJ button in the status bar) to switch to a **dual-deck DJ console** built into the player. Drop tracks on Deck A and Deck B, mix with a real crossfader, and use everything you'd expect from a DJ rig.

- **Two decks side by side**, each with: per-deck waveform (overview + 10-second close-up), title / artist / BPM / Key / Camelot, 8 hot cues (numbered, persisted in SQLite, set / clear / colour-coded), Loop In/Out + Reloop, auto-loop chips (1/8 1/4 1/2 1 2 4 8 beats), beat-jump (`<<` `<` `>` `>>`), 3-band EQ (LO / MID / HI knobs, ±12 dB), gain knob, Play / Cue / Sync, SLIP / QUANT / BRAKE, and a **Pioneer-DJM-style filter knob** (sweep LP from 20 kHz down to 70 Hz on the left half, sweep HP from 20 Hz up to 17 kHz on the right half, magnetic dead-zone at the centre).
- **Crossfader** — four industry-standard curves (Linear / Smooth / Sharp / Hamster), 5 ms per-sample smoothing (no zipper noise), right-click snaps to centre.
- **Sync engine — Mixxx-style phase-lock.** Single-click SYNC = match BPM AND beat phase to master. Right-click SYNC = make THIS deck master. Octave-fold so 175 BPM follower against 87 BPM leader stays at perceived-equal speed (ratio folds to ~1.005).
- **Vinyl scratch on the waveform.** Click + drag the close-up OR overview waveform like a Pioneer-CDJ jog wheel. Newtonian-physics platter integrator with viscous + Coulomb friction. Forward + reverse. Release lets the slipmat catch the platter back to slider rate over τ ≈ 400 ms. Works in single-track mode AND DJ mode with the same physics.
- **Vinyl-spin while paused.** Even when audio is paused or stopped, dragging the waveform spins the platter in the dragged direction. Friction decays the platter back to 0. Like spinning a turntable when the motor is off.
- **Per-deck Pitch ⇄ Stretch toggle.** Disc icon = Pitch (vinyl turntable, pitch + tempo move together via 48-tap sinc resampler). Gauge icon = Stretch (Signalsmith phase-vocoder, pitch stays constant while tempo varies).
- **Per-deck Echo + Gater FX.** Tempo-locked beat-rate chips (1/4, 1/2, 1, 2, 4 beats). Auto-syncs to deck BPM × pitch ratio in real time.
- **Saved Loops + Smart Cueing.** Per-track named loop slots persisted across sessions. First-time-load auto-creates hot-cue 1 at the detected first downbeat. Quantize-seek snaps hot-cue jumps to the nearest beat.
- **Camelot wheel + harmonic-mix helper.** Per-deck Camelot key chip auto-derived from libkeyfinder's Krumhansl-Schmuckler analysis or ID3v2 TKEY tag. Cross-deck compatibility verdict (Match / Relative / Adjacent / EnergyLift / Discord) colour-coded for at-a-glance harmonic-mix assistance. The only clean-room MIT Camelot implementation in any DJ tool.
- **Dual audio output.** Three modes: single device (DJ Mode runs without cue), dual WASAPI device (Main + Cue on independent endpoints — works with any USB DAC + Bluetooth combo), or ASIO channel-pair (Main on 1+2, Cue on 3+4 of the same multi-out interface). Pre-listen cue mix balance knob.
- **Tracker DJing — unique to FXChainPlayer.** Drop a `.mod` onto Deck A, an MP3 onto Deck B, hit SYNC. The libopenmpt module-tempo engine + offline beat-detector consensus matches Protracker / Fasttracker / Impulse Tracker / 50+ tracker formats against modern dance productions accurately enough to mix demoscene tracks alongside MP3s on the same crossfader. **No other DJ tool can do this.**
- **MIDI controller support.** Hardware-detected mappings for Pioneer DDJ-FLX series, KORG nanoKONTROL2, Akai LPD8, Behringer X-Touch Mini, Mackie-Control, General MIDI. Ableton-style Learn Mode (`Ctrl+Shift+M`) for any other controller. Pitch / EQ / hot-cues / scratch jog-wheel / play / cue / sync / filter all mappable.

> **Beta status.** DJ Mode is feature-complete and stable for production use, but a few rough edges are still being polished — per-channel VST chain audio routing has a small async cache-build delay before plugins become audible (~5-30 sec depending on track length), and a few scratch-ergonomics edge cases are still being refined. The DJ MODE pill in the header carries a small "beta" marker as a signal to calibrate expectations vs the rock-solid single-track player.

---

## Plays pretty much everything

FXChainPlayer is built for music listeners who don't want format juggling. Drop a folder with mixed FLAC, MP3, tracker files, C64 SIDs, Game Boy chiptunes, Apple Loops or Wii game-music dumps — it just plays. **1500+ extensions across 17 categories** with a built-in searchable Format Library panel.

### Lossless & Hi-Res

**FLAC**, **WAV**, **WavPack** `.wv`, **ALAC** (Apple Lossless), **APE** (Monkey's Audio), **TTA** (True Audio), **AIFF**, **Opus**, **W64** (Sony Wave64), **DSD** `.dsf` / `.dff` (DSD64/128/256/512 — including DST-compressed `.dff` via vendored FFmpeg-DST decoder).

### Lossy

**MP3**, **AAC**, **M4A** / **MP4** audio, **OGG Vorbis**, **WMA**, **MPC** (Musepack SV8), **AC-3**.

### Tracker modules (50+ via libopenmpt 0.8.6 + 9 libxmp fallbacks)

**MOD** (ProTracker), **XM** (FastTracker 2), **S3M** (ScreamTracker 3), **IT** (Impulse Tracker), **MPTM** (OpenMPT), **Digibooster Pro**, **Imago Orpheus**, **Graoumf Tracker**, **Liquid Tracker**, **Octalyser**, **PolyTracker**, **UltraTracker**, **Digitrakker**, **OctaMED**, **Farandole Composer**, **Epic MegaGames MASI**, **MadTracker 2**, **Galaxy Sound System**, **X-Tracker**, **NoiseTracker**, **Ice Tracker**, **Composer 670** + 667, **SoundFX 1/2**, **Davey Taylor's Tracker**, **DSMI/Asylum AMF**, plus libxmp fallbacks for Funktracker (`.fnk`), Liquid Tracker (`.liq`), Magnetic Fields Packer (`.mfp`), AMOS Banks (`.abk`), Soundtracker 2.6 (`.st26`), Ice Tracker (`.ice`) and many more.

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

### Atari ST native (`.sndh` / `.ym3-6`)

Native YM2149 chip emulator + own SNDH-driver-execution under a vendored Musashi 68k emulator. Unlocks the entire ~25 000-file sndh.atari.org archive without UADE.

### PSF1 family (PlayStation OST)

PSF1 audio playback via own clean-room MIPS R3000A + PS1 SPU-1 emulator. PSF2/SSF/QSF/DSF/USF/GSF/2SF/SNSF infrastructure shipped (default-OFF, scaffold-quality — corpus polish in v0.47+).

### Amiga clean-room composer-named players (12 formats, NP-derived BSD-3)

**Hippel COSO** (`.hip` `.coso`), **Hippel-7V**, **Ben Daglish** (Last Ninja / Trap / Deflektor / Speedball), **David Whittaker** (Speedball / Lazy Jones / Glider Rider), **Fred Editor** (Frank Bros), **Ron Klaren / SoundFX-RK**, **Symphonie Pro 32-voice**, **Quartet Microdeal** (Atari ST 4-voice PCM), **SoundFactory**, **Mark II**, **Audio Sculpture**, **Digital Mugician 7-voice** (Pete Cooke). Plus **AMOS Music Bank** (every AMOS BASIC game 1990-95), **DeltaMusic 1+2**, **Art Of Noise**, **JamCracker**, **SoundFX v1+v2** (Saint Cinemaware), **BP SoundMon v2+v3** (Brian Postma), **Sidmon 1+2** (Tim Wright / Jeroen Tel), **Sonic Arranger** (Tower of Souls / Ambermoon / Albion), **MaxTrax** (LucasArts Indy/Monkey-Island), **TFMX** (Hülsbeck — Turrican / Apidya / Monkey Island Amiga), **RJP** (Bitmap Brothers — Chaos Engine / Cannon Fodder / Speedball 2 / Gods).

### Demoscene + retro synths

**AHX / HVL** (Hively Tracker), **`.v2m`** (Farbrausch V2 — `.kkrieger` / `.fr-08`), **`.s3m`** stuck-orchestral-hit fixes, **TIATracker** (Atari 2600), **Organya** (Cave Story), **GoatTracker** (C64), **SAP** (own clean-room 6502+POKEY), **ZxTracker** (Vortex Tracker II / Pro Tracker 3 / Sound Tracker), **MED Advanced** (OctaMED MMD0/1/2/3), **FutureComposer** (`.fc` / `.fc13` / `.fc14`), **MDX** (Sharp X68000 — own YM2151 OPM + MSM6258 ADPCM), **Euphony** (FM-TOWNS — own YM2612 OPN2 + dual register banks).

### MIDI / SoundFont

`.mid` / `.midi` / `.rmi` via TinySoundFont. Configurable SoundFont (drop a `.sf2` file in *Settings → Audio → MIDI SoundFont*; live `.sf2` audition by dragging the file onto the player).

### TFMX / RJP / TFE / PMD / FMP

**TFMX** — full Hülsbeck macro-engine clean-room (4-voice MDAT/SMPL pairs).
**RJP** — Bitmap Brothers RDAT/RSMP pairs (RJP0SMOD full audio; RJP1 detected, audio queued).
**TFE** (TFM Music Maker) — dual YM2203 OPN-FM via vendored ymfm BSD-3 + clean-room parser.
**PMD / FMP** — PC-98 (98fmplayer BSD-2 — Touhou-pre-Windows / Falcom / Compile).
**MSX** `.kss` (libkss ISC).
**SMS / PC-Engine / RGBDS Game Boy** `.sgc` / `.nsd` / `.gbr` (libnezplug Unlicense-OR-MIT-0).

### DOS Adlib (LGPL-2.1 AdPlug)

`.imf` / `.hsc` / `.rad` / `.d00` / `.dro` / `.rix` / `.rol` / `.mus` and ~50 more DOS / Sound Blaster / Adlib / OPL2/3 formats.

### Apple CAF + Sample-pack formats

**Apple CAF** dedicated decoder (PCM 8/16/24/32-bit BE/LE int/float, IMA4, AAC + ALAC via WMF MFTs, FLAC via dr_flac). Surfaces Logic-Pro Apple-Loops BPM tags from `mark[tmpo]+strg` chunks.
**REX / RX2 / RCY** sliced-loop sample-pack format (default-OFF, requires user-side Reason Studios REX SDK).

### Game music & sample-pack (~700 formats via vgmstream r2083)

**vgmstream is now DLL-linked + FFmpeg codecs ON by default** (since v0.46.0):

- **Apple `.caf`** — Logic Pro / GarageBand **Apple Loops** library
- **Nintendo** — BRSTM · BCSTM · BFSTM · BFWAV · DSP-ADPCM family · NUS3AUDIO · Switch Opus
- **Sony** — VAG · HPS · NUB · ATRAC3 / ATRAC9 (via FFmpeg) · AT3 / AT9
- **Microsoft** — XMA · XWMA (via FFmpeg)
- **CRI** — ADX · HCA · ACB / AWB containers
- **FMOD** — FSB (Multiple, including Vorbis + CELT via FFmpeg)
- **Square Enix** — SCD
- **Wwise** — WEM
- **vgmstream `.txtp`** text-playlists with effects
- **Multi-subsong navigation** API for game-OST archives

### Furnace + IFF SMUS

**Furnace `.fur` / `.dmf`** multi-chip tracker (Tier-A AY/YM2149 via real chip emulator; ~30 other chip families via band-limited soft-fallback synthesis).
**IFF SMUS** Amiga MIDI-style score with INS1 + 8SVX sample resolution.

---

## Audio engine

### WASAPI Shared / Exclusive + ASIO 2.3

**WASAPI** Shared and Exclusive modes are the default Audio Mode. The player picks the device's native sample rate — no system-wide resampling. **WASAPI Exclusive** bypasses the Windows audio engine for the bit-for-bit path; works on any USB DAC, built-in sound, or HDMI output, no ASIO driver required.

**ASIO 2.3** is also supported (Steinberg-licensed) for users with a compliant audio interface. Pick **ASIO** in *Settings → Audio → Audio Mode*. Round-trip latency depends on your audio interface and the buffer size the driver supports — see *Settings → Audio → Latency* for the driver's live in/out frame counts and total ms.

- **Output Pair routing** for multi-output interfaces — route the player's stereo to any pair (1-2, 3-4, …) up to the driver's reported total. Persisted across sessions.
- **Configure Driver button** opens the driver's hardware panel directly (e.g. RME TotalMix, MOTU CueMix, Apollo Console, ASIO4ALL settings).
- **Driver-reported latency readout** — in N / out N frames + total ms — refreshed live whenever the driver fires `kAsioLatenciesChanged`.
- **Sample-accurate visual playhead** (since v0.46.1) — the waveform playhead subtracts the backend's currently-queued frames (`IAudioClient::GetCurrentPadding()` on WASAPI, `ASIOGetLatencies()` on ASIO) so what you see is what you hear, not what's been written to the buffer 10-42 ms ago.
- **Output stage** — TPDF dither at canonical ±1 LSB peak (Lipshitz–Vanderkooy 1992) on every integer path, NaN/Inf guards, asymmetric clamps preserving the negative-rail code, full coverage of `ASIOSTInt16/24/32 LSB/MSB` and `Float64MSB`.
- **SEH-safe driver panel calls** + clean reset / latency-change handling so a misbehaving panel can't take out the host.

### Per-Channel VST Chains (since v0.45.0)

For every multi-channel format (tracker `.mod` / `.xm` / `.it` / `.s3m`, SID, NSF, SPC, GBS, every libopenmpt + libgme chip-emulator format), each separable channel can carry its **own dedicated VST3 chain** of up to 16 plugins.

- **Channel-tab navigation** — pick which channel you're editing
- **Per-channel chain editor** — full slot grid with plugin name, vendor, BYPASS pill, MIX slider, EDIT (open VST3 GUI), MOVE-LEFT / MOVE-RIGHT chevrons, REMOVE-X
- **Auto-load presets** — chain configurations are CRC32-keyed (filename + filesize) and auto-loaded on track-change for matching files
- **Manual save / load** — save the per-channel chain layout as a named preset (`%APPDATA%\Akustikrausch\FXChainPlayer\chain_presets\`)
- **Real-time playback** — pre-renders per-channel PCM into a 500 MB-budgeted cache, then routes audio through the per-channel chains live (cache build takes ~5-30 sec on first plugin add)
- **Export-path integration** — multi-track export renders each channel through its own chain to a separate file (filename template `<title> - <channelName>.<ext>`; e.g. `MyTrack - Voice 1.wav`, `Game OST - Square 1.flac`)
- **4 FX modes for export** — Master chain only / Per-channel chains only / Per-channel → master cascade / No FX

### Vinyl Scratch — Newtonian platter physics

Click + drag the waveform like a Pioneer-CDJ jog wheel. The mouse becomes your *fingertip* and applies torque proportional to slip; the platter has **real inertia** (`I = 0.030` ≈ Technics SL-1200GR with felt slipmat) and accelerates / decelerates accordingly.

- **Fully bidirectional** — forward drag = audio plays at drag velocity; backward drag = audio plays in reverse at drag velocity (up to 8 s into the past via a rolling output-history buffer)
- **All techniques emerge from one ODE** — baby / forward / chirp / tear / spinback all from `I·dω/dt = τ_finger − μ_v·(ω − ω_motor) − μ_c·sign(slip)`
- **Inertia-aware release ramp** — τ = `I/μ_v` ≈ 400 ms, calibrated against the SL-1200's 0→33⅓ RPM spin-up
- **Spin while paused** — flick the waveform on a paused track; the platter spins in the dragged direction and friction decays back to 0 (like spinning a turntable with the motor off)
- **Same physics in single-track AND DJ mode** for both the close-up scrolling waveform and the full-song overview strip

### Turntable Pitch Slider (Technics-style)

A vertical pitch fader on the right edge of the expanded waveform AND DJ-mode view. Selectable range (**±8 % / ±16 % / ±50 %**), **0 % center detent** (snaps to neutral within ±0.3 %), **33 ⇄ 45 RPM toggle**, and a per-deck **Pitch ⇄ Stretch toggle** (disc icon = vinyl-style pitch+tempo move together via 48-tap windowed-sinc; gauge icon = Signalsmith phase-vocoder time-stretch with constant pitch).

**At 0 % the slider's fast-path is bit-exact pass-through** — the resampler is bypassed entirely. Auto-resets to neutral on every track change.

### 64-bit double-precision signal path

Internal audio path is `double` end-to-end. Sample-rate conversion (when needed) uses **r8brain-free-src** (linear-phase, ~260 dB SNR per the manufacturer).

### BPM consensus + Camelot key detection

Multi-source BPM aggregator ranks candidates from up to eight signals (manual tap-to-confirm 100, CAF `mark[tmpo]` 99, MIDI Set-Tempo 99, libopenmpt tracker static 99, ID3v2/Vorbis/APEv2/MP4 tag 95, CUE `REM BPM` 95, offline beat-detector 95/80, filename regex 75-95) with octave-fold corroboration boost and contradiction cap. Display tier: ≥95 solid badge, 80-94 dimmed `~XXX` with reduced opacity, <80 hidden — never shows a guess as if verified. Click the BPM pill to verify by tap-along.

**Krumhansl-Schmuckler key detection** runs in the background scan thread for every file (8192-pt Hann-windowed FFT chromagram + 24-key Pearson correlation). Persisted in the SQLite cache. Every analysed file gets a Camelot wheel chip in the deck header AND in the playlist's Key column.

### MIDI controller input

RtMidi-6.0-based polling. Mackie-Control + General-MIDI defaults, plus built-in profiles for **KORG nanoKONTROL2**, **Akai LPD8**, **Behringer X-Touch Mini**, **Pioneer DDJ-FLX series**. Hot-plug auto-config matches 16 known controller name fragments. Ableton-style Learn Mode (`Ctrl+Shift+M`) for any other controller. Persistence in `%APPDATA%\Akustikrausch\FXChainPlayer\midi_mappings.json`.

50+ DJ-specific trigger targets mappable: pause / stop / toggle / exitLoop / unsync / tempoLock / pitchRange × 2 decks, hot-cue Set 1-8 × 2 decks, hot-cue Clear 1-8 × 2 decks, scratch start/end + scratch velocity × 2 decks (jog-wheel rotation), filter, echo/gater amount + beats, autoloop halve/double.

### Format Library — every supported format, in-app

A collapsible **Format Info** card in *File Info* (origin, era, codec, decoder library) for every track, and a full **Formats Library** modal panel with a per-category sidebar, search across name / extensions / platform / developer / decoder, and click-to-expand cards with the complete catalogue entry. The redesigned **Settings → File Associations** uses the same source-of-truth.

### 3-Band EQ (built-in modal dialog)

Low Shelf / Mid Bell / High Shelf with two draggable crossover-frequency handles on a live FFT spectrum and three Low/Mid/High gain knobs. RBJ-cookbook biquads with 5-ms coefficient ramping. Soft 0 dB detent on bipolar knobs. Toggle with `Q`.

### Real-time visualization (9 modes)

- **FFT Spectrum** — log-scale frequency analyzer with Hz axis labels (30 / 100 / 300 / 1k / 3k / 10k) and a 1-px peak-hold trail
- **Spectrogram** — scrolling waterfall
- **Stereo Phase Scope** — Lissajous / goniometer with amplitude-brightening
- **VU Meter** — classic PPM L/R
- **LED HiFi** — 32-band segmented display
- **Frequency Landscape** — 3D waterfall with cubic depth fog
- **Pulse Thread** (default since v0.39.0) — multi-octave audio-warped spine with audio-reactive starfield (GPU shader)
- **Chroma Drift** — 6 ribbons at parallax depths riding their own FBM flow fields with audio-driven domain warp + caustic sheen on energy peaks (GPU shader)
- **Studio LED** — smooth HSV-interpolated 3-zone gradient with per-LED diffuser/die SDF + halo bleed (GPU shader)

Plus dedicated **Channel Scopes** (per-channel oscilloscopes for trackers up to 4 channels), a live **ProTracker-style Pattern View** for `.mod` / `.xm` / `.s3m` / `.it` (and now libxmp formats too via the unified `IPatternSource` interface), and the **SID Voices** view for Commodore 64 tunes.

### Studio Compare (A/B)

Dual-decoder synchronized A/B playback — load two files and switch between them sample-accurately with a 64-sample crossfade. Compare masters, codecs, headphones, plugin chains.

### Built-in Bauer-style crossfeed

Smooth your stereo on headphones without a plugin slot. Continuous blend slider, proper gain + delay + lowpass filtering.

### Gapless playback

Next track is pre-loaded and swapped in sample-accurately across the decoder families that allow it (FLAC→MP3, MOD→XM, cross-format — all work).

### Integrated file browser & smart-scan

Point it at your music library. Background SQLite cache for VBR durations, bitrates, cover art, **BPM, Key, Camelot**. Instant playlist building. Breadcrumb navigation, library roots, "Play / Add All" context actions, Favorites tab.

### Export through your VST3 chain

Route **any file or whole playlist** through your VST3 effect chain and render the result to disk. Faster-than-real-time, offline, sample-accurate. Right-click a track in the playlist → **Export to format…** for a single file, or **Ctrl+E** for the full batch dialog.

Output formats:

- **WAV** — 16-bit, 24-bit PCM, 32-bit float
- **MP3** — 128 / 192 / 320 kbps CBR
- **FLAC** — 16-bit and 24-bit lossless (libFLAC, compression level 5)
- **OGG Vorbis** — q3 / q5 / q7 (≈ 112 / 160 / 224 kbps VBR via libvorbis)

Multi-tune containers (NSF / NSFE / SAP, multi-tune SIDs from HVSC, multi-subsong vgmstream archives) can optionally expand into one file per subsong via the **Export all subsongs** checkbox. **Multi-selection** support — Shift-click a range, Ctrl-click individual rows, then export only the selected subset. **Per-row subsong picker** for choosing exactly which tune from a 19-tune SID like `Commando.sid`. **4-mode FX-chain selector** — Master / Per-channel / Both (cascade) / None.

Export is included in every build — no separate "Pro" tier.

### Plugin crash protection

SEH-wrapped plugin process calls, automatic crash journaling, safe-mode after repeated failures, per-`(path, classID)` blacklist so a single crashing plugin in a multi-class shell (e.g. Waves WaveShell with 600+ effects) doesn't take out the rest. Auto-restart watchdog subprocess.

### Code-signed installer + DLLs

Every release is signed via Azure Trusted Signing — both the installer AND every shipped DLL (Qt, libopenmpt, vgmstream, FFmpeg, …) carry a counter-signature. Windows SmartScreen reputation builds quickly. WDAC + AppLocker DLL rules in enterprise environments allow the player without exception.

### Full keyboard accessibility

Every audio control reachable via Tab + Space / Enter / arrow keys. Output-pair, mode chips, device list all wired as standard radio groups. Settings panel, TransportBar, FileBrowser, FxChain bypass, Playlist tabs all wired. Hard CI gate (`qml_a11y_lint`) prevents regressions.

### Performance

Native C++20, lock-free audio thread, GPU-accelerated rendering throughout (no QML Canvas anywhere). Idle RAM ~50 MB, cold startup under 2 s on typical hardware. **81 CTest gates** run on every CI push to lock structural invariants against regression.

---

## What's new in v0.46.2

This is the **first public release in nine internal release cycles** since v0.37.2 (2026-04-28). It consolidates everything from v0.38.0 → v0.46.2 — a substantial body of new work across DJ Mode, format support, vinyl-scratch physics, per-channel VST chains, MIDI controllers, key detection, GPU visualisers, and a complete code-signing infrastructure. Highlights below grouped by theme rather than by release.

### 🎧 DJ Mode — entirely new (since v0.39.0, polished through v0.46.2)

The biggest single addition since v0.37.2. Press `D` to switch to a dual-deck DJ console with crossfader, hot cues, loops, sync engine, Pioneer-DJM-style filter, Echo + Gater FX, vinyl scratch on the waveform, dual audio output (separate Cue device or ASIO channel-pair), Camelot wheel + harmonic-mix verdict, and full MIDI controller support. Tracker DJing across `.mod` / `.xm` / `.it` / SID + MP3 on the same crossfader is unique to FXChainPlayer.

### 🎚️ Per-Channel VST Chains (since v0.45.0)

Each separable channel of multi-channel formats (trackers, SIDs, NSFs, SPCs, GBSs, …) can carry its own dedicated VST3 chain up to 16 plugins. Real-time playback via 500 MB-budgeted cache. Full export-path integration (4 FX modes: Master / Per-channel / Both cascade / None). CRC32-keyed auto-load presets. **VST3 chain limit lifted from 8 → 16 slots.**

### 🎹 Vinyl Scratch — Newtonian physics (since v0.38.2)

Full ODE-integrator platter physics for click-and-drag waveform scratching. Forward + reverse with bidirectional sinc-interp readback from an 8-second history ring. Pioneer-CDJ feel with Technics SL-1200 inertia + slipmat-friction restore. Works in single-track AND DJ mode on both close-up + overview waveforms. Even works while paused (spin a stopped platter, friction decays it back to 0).

### 📈 Format support — ~800 → 1500+ extensions

**Console emulators added (8):** Atari ST native (`.sndh` / `.ym3-6` via own YM2149 + Musashi 68k), PSF1 audio (own MIPS R3000A + SPU-1), TFE TFM Music Maker (dual YM2203 OPN-FM via vendored ymfm), MDX Sharp X68000 (own YM2151 OPM + MSM6258 ADPCM), Euphony FM-TOWNS (own YM2612 OPN2), MSX `.kss` (libkss), SMS / PC-Engine / RGBDS Game Boy (libnezplug), AHX / HVL Hively Tracker.

**Amiga clean-room composer-named players (12 + 6 base):** Hippel COSO/7V, Ben Daglish (Last Ninja / Speedball), David Whittaker, Fred Editor, Ron Klaren, Symphonie 32-voice, Quartet Microdeal, SoundFactory, Mark II, Audio Sculpture, Digital Mugician 7-voice, plus AMOS Music Bank, DeltaMusic, Art Of Noise, JamCracker, SoundFX, BP SoundMon, Sidmon, Sonic Arranger PWM, MaxTrax LucasArts, **TFMX Hülsbeck** (Turrican / Apidya / Monkey Island Amiga), **RJP Bitmap Brothers** (Chaos Engine / Cannon Fodder).

**Demoscene + retro:** TIATracker (Atari 2600), Organya (Cave Story), GoatTracker (C64), SAP (Atari 8-bit own clean-room 6502+POKEY), ZxTracker (Vortex Tracker II), MED Advanced (OctaMED MMD0/1/2/3), FutureComposer, Farbrausch V2 (`.v2m` — `.kkrieger` / `.fr-08`), Furnace `.fur` / `.dmf`, IFF SMUS Amiga MIDI-style score.

**DOS Adlib (LGPL-2.1 AdPlug):** ~50 DOS / Sound Blaster / Adlib / OPL2/3 formats — `.imf` / `.hsc` / `.rad` / `.d00` / `.dro` / `.rix` / `.rol` / `.mus`.

**vgmstream r2083 expansion (since v0.46.0):** vgmstream is now DLL-linked + FFmpeg codecs ON by default. Adds **ATRAC3 / ATRAC9** (Sony PSP/PS3/PS4/Vita), **XMA1 / XMA2** (Xbox 360 / Xbox One), **xWMA** (XAudio2 streaming), **FSB-Vorbis / FSB-CELT** (FMOD Sound Bank), **NUS3-Opus** (Switch Smash Bros.), **Speex** (older Bink Audio), **G.719** (Ericsson reference). +12 v0.45.3 newly-documented extensions (`.aea` `.afc` `.afs` `.baa` `.logg` `.sts` `.svs` `.utk` `.xwb` `.xwma`).

**Apple CAF (since v0.38.0):** Dedicated decoder replacing the v0.37.x vgmstream-routed path. Covers PCM 8/16/24/32-bit BE/LE int/float, IMA4, AAC + ALAC via WMF MFTs, FLAC via dr_flac. Surfaces Logic-Pro Apple-Loops BPM tags from `mark[tmpo]+strg` chunks.

**DST-compressed `.dff` (since v0.44.0):** Vendored FFmpeg's `libavcodec/dstdec.c` (LGPL-2.1+). Patent expired 2024. Direct Stream Transfer DSD finally plays natively.

**Tracker fallback hardening:** libxmp 4.7.0 added as 9-extension fallback for libopenmpt edge cases (Funktracker `.fnk`, Liquid Tracker `.liq`, Magnetic Fields Packer `.mfp`, AMOS Banks `.abk`, Soundtracker 2.6 `.st26`, Ice Tracker `.ice`, Davey Taylor's `.fmt` variant, AMS, GTK).

**Format Registry centralisation (since v0.43.6):** Single source of truth — every consumer (drag-drop, file browser, favourites, BPM probe, waveform skip, streamable detection) reads from `docs/user/FORMATS.md`. New formats need a single doc edit; the rest cascades automatically.

### 🎛️ MIDI controller input (since v0.38.0)

RtMidi-6.0 polling, hardware-detected mappings (Pioneer DDJ-FLX, KORG nanoKONTROL2, Akai LPD8, Behringer X-Touch Mini, Mackie-Control), Ableton-style Learn Mode (`Ctrl+Shift+M`), 50+ DJ-specific trigger targets including scratch jog-wheel sensors, hot-cue Set/Clear × 8 × 2 decks, filter, Echo/Gater amount + beats. Hot-plug auto-config across 16 known controller name patterns.

### 🎵 BPM consensus + Camelot key (since v0.38.2 / v0.43.7)

Multi-source BPM aggregator (8 sources, octave-fold corroboration), offline Krumhansl-Schmuckler key detection (background scan, persisted in SQLite), Camelot wheel chip per track + per deck, cross-deck harmonic-mix compatibility verdict (Match / Relative / Adjacent / EnergyLift / Discord). The only clean-room MIT Camelot implementation in any DJ tool.

### 📊 GPU shader visualisers (since v0.39.0)

Three new GPU visualisers — **Pulse Thread** (now the default, multi-octave audio-warped spine with audio-reactive starfield), **Chroma Drift** (6 ribbons at parallax depths riding FBM flow fields), **Studio LED** (smooth HSV-interpolated gradient with per-LED diffuser/die SDF). All three use `QSGTextureProvider` with proper lifecycle (60-Hz heartbeat, `itemChange(ItemSceneChange)` rebuild on DPI shift, no UAF on window-teardown).

### 🔊 Sample-accurate visual playhead sync (since v0.46.1)

The waveform playhead now subtracts the backend's currently-queued frames so the visible position matches what's actually being heard at the speakers — not what was written to the buffer 10-42 ms ago. WASAPI uses `IAudioClient::GetCurrentPadding()` per call; ASIO uses the cached `ASIOGetLatencies()`.

### 💪 Stability + bug fixes

- **Mid-track playback recovery (v0.43.6)** — single transient `read()=0` from dr_mp3 on bad MP3 frames no longer triggers a track-skip; 5×20ms retry budget recovers via the same retry pattern as the legacy DecoderThread.
- **AudioDecoder move-ops field-leak (v0.43.4)** — 7-month-old class of "format opens but plays silence after gapless transition" reports closed via the `check_decoder_move_ops` CTest gate scanning all 69 unique_ptr + 4 scalar fields across both move-ops.
- **Concurrency hardening (v0.43.3)** — `taglib_lock.h` + `libopenmpt_lock.h` + `iff8svx_lock.h` + `mf_lock.h` Meyers-singletons serialise format-CREATE across 5 racing threads (audio decoder + WaveformProvider + SmartScan worker + BpmDetector + KeyDetector). Closes a recurring bulk-add crash class.
- **TFMX + RJP rendering bug fixes (v0.46.0)** — clamp-not-mask in note dispatch (was folding high-transpose into wrong octaves on Hülsbeck files); DMAOn loop heuristic 256 → 8192 bytes (was killing Monkey choir + Turrican III orchestral hits as one-shot decay); RJP `currentInstrument = 1` default (every Bitmap-Brothers RDAT was producing peak=0.00 silence on bare-NOTE patterns).
- **DJ HP filter (v0.46.2)** — Cytomic-SVF canonical HP output formula corrected from buggy `v3 - k*v1 - v2` to canonical `in - k*v1 - v2`. Pre-fix the extra `-s2` term built up DC drift as the LP integrator state grew under real signal input.
- **Reverse-scratch first-25-samples-silence eliminated (v0.46.2)** — cursor primes at `writePos - sinc::kTapsHalf - 1` instead of `writePos`, so sample 0's kernel fits entirely inside the valid window. Single-track AND DJ-mode benefit equally.
- **Code signing for `.dll`s (v0.46.0)** — release.yml signing-filter expanded from `exe` to `dll,exe`. Critical for enterprise WDAC + AppLocker DLL-rule deployments.
- **DJ-Mode audio dropout root-cause kill (v0.43.7 build-fix #8)** — tracker EOF mid-track was silently flipping `playing.store(false)` in the per-deck worker loop with NO log line + NO recovery. Now auto-loops in DJ context (DJ context = "loop this track until I tell you otherwise") + every transition is logged.

### 🧪 Internal QA infrastructure

The CTest gate count grew from a handful in v0.37.2 to **81 active gates** in v0.46.2 — every fix-class lands with its own anti-regression gate. The full `dist/` ships with `check_decoder_move_ops` PASS, `check_dj_layout_invariants` PASS, `qml_boolean_wraps` PASS, `concurrency_invariants` PASS, plus 77 others — drift in ANY of them fails the CI build.

**See the [CHANGELOG](#changelog-since-v0372) below for the per-release detail.**

---

## Changelog since v0.37.2

The internal release cycle was 9 versions deep between the public v0.37.2 (2026-04-28) and the public v0.46.2 (2026-05-12). Each internal release is documented in detail in CLAUDE.md but the headline-feature shape per cycle:

- **v0.38.0** — Apple CAF dedicated decoder (replaces v0.37.x vgmstream PCM-only path that silently rejected AAC/ALAC). MIDI controller input (RtMidi). Mouse-wheel support on continuous controls.
- **v0.38.1** — Playlist sort + grouping overhaul (auto-group on multi-folder drops, Date-Added Session bucketing, Group-by selector). StatusBar message-color severity system. TFMX full re-write. RJP v1 full implementation. Apple CAF playback fixes (PCM duration, AAC/ALAC MFT setup). VST3 Browser search UX.
- **v0.38.2** — Vinyl-scratch on the waveform (Newtonian-physics rewrite). Pitch ⇄ Stretch toggle (Signalsmith phase-vocoder). VST3 unload-crash fix. AppData single-root consolidation. **BPM consensus engine + offline beat-detector.** CUE `REM BPM/KEY` support.
- **v0.38.3** — Cover-art cache (CRC32-keyed, 1024-entry LRU).
- **v0.39.0** — **DJ MODE.** Dual-deck console, crossfader (4 curves), sync engine (Mixxx-style phase-lock), 8 hot cues per deck, auto-loop chips, beat-jump, 3-band EQ per deck, Pioneer-DJM-style filter, dual audio output (single / dual WASAPI / ASIO channel-pair), Bluetooth-cue warning, BPM auto-sweep on DJ entry, tracker DJing. Three new GPU shader visualisers (Pulse Thread, Chroma Drift, Studio LED). Unified subsong navigation (SID + libgme + TFMX + RJP + multi-subsong vgmstream). UI-scale restart asymmetry root-fix. Bulk-add crash root-fix.
- **v0.40.0** — **rePlayer-Parität** — 800 → 1500+ extensions. AdPlug LGPL-2.1 (DOS Adlib MUS/IMF/HSC/RAD/D00/DRO/RIX/ROL + ~50). Hively/AHX BSD-3. libxmp 4.7.0 MIT (tracker fallback hardening). 98fmplayer BSD-2 (PC-98 PMD/FMP). Farbrausch V2 PD (`.v2m`). libnezplug Unlicense (SMS/PC-Engine/RGBDS GameBoy). libkss ISC (MSX). libayumi MIT (AY chip). psflib MIT (PSF/PSF2/SSF/QSF/DSF metadata). 7 clean-room ports: JamCracker, SoundFX 1+2, BP SoundMon 2+3, Sidmon 1+2, Sonic Arranger, MaxTrax. **Atari ST native** (`.sndh` / `.ym` family) with own YM2149 + Musashi 68k.
- **v0.41.0** — 9 NEW clean-room formats: TIATracker, Organya, GoatTracker, SAP (own 6502 + POKEY), ZxTracker, MED Advanced, FutureComposer, MDX (X68000 — own YM2151), Euphony (FM-TOWNS — own YM2612). 4 v0.40 finalisations (BP SoundMon synth chains, Sonic Arranger PWM, Atari ST $FF8800/$FF8802 latch trap, RJP1SMOD). **PSF1 audio playback** (own MIPS R3000A + PS1 SPU-1).
- **v0.42.0** — PS1 SPU Reverb finalised. REX SDK shipped. 3 NP-derived Amiga formats (AMOS Music Bank, DeltaMusic 1+2, Art Of Noise). **8 console-emulator scaffolds** (PSF2 R5900+SPU2 / SSF SH-2+SCSP / DSF Dreamcast SH-4+AICA / USF N64 R4300i / GSF GBA ARM7TDMI / QSF Capcom Z80+QSound / 2SF NDS / SNSF SNES wdc65816+S-DSP). NostalgicPlayer recon (4 missing formats identified for v0.43+).
- **v0.43.0** — **12 NP-derived clean-room Amiga composer-named players** fully wired (Hippel COSO/7V, Ben Daglish, David Whittaker, Fred Editor, Ron Klaren, Symphonie Pro 32-voice, Quartet Microdeal, SoundFactory, Mark II, Audio Sculpture, Digital Mugician 7-voice). Furnace Tier-B chip wiring. IFF SMUS sample playback. IPatternSource interface. DJ-Mode subsong UI strip. FileInfoProvider full coverage. 7-of-8 console-emulator scaffolds wired into dispatch.
- **v0.43.1 → v0.43.7** — DJ Mode polish across 7 build-fixes including: Pioneer-DJM-style HP/LP filter + Camelot wheel + harmonic-mix helper, scratch upgrades, MIDI completeness (50+ DJ trigger targets), key detection (Krumhansl-Schmuckler), Slip mode, Quantize-seek, Smart cueing, Saved (named) loops, Brake / vinyl-stop, Echo + Gater FX (tempo-locked beat-rate chips). Hot-cue persistence root-fix. BPM-fallback for beat-jump + autoloop on synth/chiptune formats. Mid-track playback recovery (5×20 ms retry budget). DJ deck-reload race shrink. Stream URL routing fixes. Format Registry centralisation. Concurrency hardening (taglib + libopenmpt + iff8svx Meyers-singleton mutexes). Generic IPatternSource for libxmp Pattern view. Format-Audit pass (10 format-class fixes incl. TTA SEH crash, IFF/8SVX VHDR off-by-four).
- **v0.44.0** — **DST decoder integration** (FFmpeg-LGPL `libavcodec/dstdec.c` thin extraction; patent expired 2024). **TFE chiptune playback** (TFM Music Maker — dual YM2203 OPN-FM via vendored ymfm BSD-3). UX responsiveness fixes (Add-All button compact mode, peak meter freeze on pause). Pulse-Thread analyzer dynamic particles + audio reactivity. Chroma-Drift "silence = flatline" fix. Studio-LED clean look. WSL 9P file-lock recovery infra.
- **v0.45.0 → v0.45.3** — **Per-Channel VST chain feature** (export-path complete v0.45.0 → real-time playback v0.45.0 Phase H.2 → per-channel chain UX wiring v0.45.3 hotfix #15). 8 → 16 VST3 slot expansion. Filename-coupled auto-presets (CRC32). Pulse-Thread default analyzer. Per-Channel VST Chain panel rebuild + bridge expansion. DJ Mode tons of bug fixes across hotfixes #1-#17 (DJ-Mode audio dropout, DJ Mode hot-cue + LIVE STATS rendering, scratch-while-pitched, DJ controls when not loaded, web-radio improvements). Multi-band BPM detector + late-bind wiring. On-play BPM auto-detect.
- **v0.46.0** — **Shared-libs migration** — vgmstream static→DLL + FFmpeg-gated codecs ON by default. Per-Channel VST Chains panel full rebuild (auto-open + slot-grid overlap + missing controls all fixed). Batch Export panel 5-defect rebuild ("0 active" counter + multi-selection + format-dropdown overflow + per-track subsong picker + 4-mode FX selector). DJ-Mode IFF/8SVX pitch UAF closure. **DJ-Mode IFF SMUS tempo divisor 64 → 128** (every SMUS file was playing at 2× intended speed). DJ-Mode scratch ergonomics (engage on press, palm-the-platter semantics). Code signing expansion (`exe` → `dll,exe` filter). Massive playback recovery (10 distinct format-playback failures from real-world session log). Layout-overhaul with MasterStatusBar. v0.46.0 QA Rundumschlag (8-parallel-sub-agent forensic audit + 25 coordinated fixes).
- **v0.46.1** — 8-fix coordinated push: Musashi dispatcher (ODR-collision closed before commit), TFMX envelope speed=0 fix, Sonic Arranger PWM lock, Furnace macro-engine infrastructure, **DSF AICA mix() audio path** (DSF/Dreamcast finally audible), **Visual-playhead audio-visual sync** (subtracts backend queued frames), **Vinyl-spin-while-paused gimmick**, DJ-Mode 4K layout redistribution.
- **v0.46.2** — DJ HP filter (Cytomic-SVF formula corrected). Reverse-scratch first-25-samples-silence eliminated (cursor offset). DJ MODE pill "beta" honesty marker. PerChannelChainPanel ON-button binding refresh. v0.46.1 #18.8 DJ-Mode 4K layout reverted to v0.46.0 baseline (per user preference).

---

## Download

**[⬇ Latest installer on GitHub](https://github.com/akustikrausch/FXChainPlayer-Releases/releases/latest)**

One installer, one click: `FXChainPlayer-Setup-X.Y.Z.exe` (Inno Setup). Full install with file associations, Start menu entries, uninstaller. All required Qt DLLs and the VST3 host process are included. **Both the installer and every shipped DLL are signed via Azure Trusted Signing.**

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

FXChainPlayer is a **VST3 host** (not VST2). Any 64-bit VST3 effect plugin should work.

There is no compatibility list, no certification, no allowlist. Any well-behaved 64-bit VST3 effect should load. Tested heavily with **FabFilter**, **Waves**, **iZotope**, **Sonarworks**, **Tokyo Dawn Labs**, **Valhalla DSP**, **Acon Digital**, **Softube**, **Kirchhoff-EQ**, **Pro-MB**, **Dear Reality dearVR**, **Beyerdynamic Headphone Lab** and many others. Multi-class plugin shells (e.g. Waves WaveShell with 600+ effects) are crash-isolated per `(path, classID)` so a single misbehaving effect can't take out the rest.

Instruments (VSTi) are filtered out automatically — FXChainPlayer is a playback tool, not a DAW.

---

## License

FXChainPlayer is proprietary software by **Andreas Wendorf (Akustikrausch)**.

The binaries use and statically/dynamically link the following open-source components (with full LGPL / BSD / MIT attribution in the About dialog inside the app): Qt 6, VST3 SDK, dr_libs, stb_vorbis, libopenmpt, libgme (Game Music Emu), cRSID, TinySoundFont, WavPack, Monkey's Audio SDK, libmpcdec, libtta++, r8brain-free-src, TagLib, SQLite, pugixml, MurmurHash3, nlohmann/json, spdlog, libarchive, ancient, vgmstream (ISC), libFLAC, libvorbis, libogg, zlib, AdPlug (LGPL-2.1), libhvl/Hively (BSD-3), libxmp (MIT), 98fmplayer (BSD-2), libnezplug (Unlicense-or-MIT-0), libkss (ISC), libayumi (MIT), psflib (MIT), Musashi 68k emulator (MIT), ymfm (BSD-3), Signalsmith Stretch (MIT), FFmpeg (LGPL — DST + AAC + ALAC + ATRAC9 + XMA via vgmstream-FFmpeg integration), RtMidi (MIT).

ASIO is a trademark and software of Steinberg Media Technologies GmbH. FXChainPlayer uses the Steinberg ASIO Interface Technology under license. The Steinberg ASIO SDK source code is NOT redistributed with this product.

---

## Community

Join the FXChainPlayer Discord for questions, feedback, plugin recommendations, and bug reports: **<https://discord.gg/sfHBZFhG>**

## Links

- **Latest release:** https://github.com/akustikrausch/FXChainPlayer-Releases/releases/latest
- **Discord:** https://discord.gg/sfHBZFhG
- **Author:** [Andreas Wendorf / Akustikrausch](https://github.com/akustikrausch)

---

<p align="center"><em>Tools disappear. Music remains.</em></p>
