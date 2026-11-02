# Release history

[Home](README.md) · [Downloads](releases/README.md) · [User guide](docs/USER_GUIDE.md)

## 0.12.8 Auto Sample Preview — 2 November 2026

**MIDI Keyboard and PC Auto Sample join the Editor.** This release brings the additions developed since the public 0.11.1 preview into one Windows application.

### New features

- **Play from a MIDI keyboard connected to your PC.** Route it to the S5000/S6000 over USB, or to Auto Sample's selected external synth or loaded VST3 instrument. The computer-side route works without an Akai connected.
- **Capture hardware synths.** Select the computer's MIDI output and audio-interface inputs, then record a range of notes and up to four velocity layers automatically.
- **Host 64-bit VST3 instruments.** Open the instrument's editor, select a sound and render it into native S5000/S6000 files. Accelerated rendering is available where supported, with real-time rendering as an alternative.
- **Use ASIO or Windows audio.** Choose an installed manufacturer ASIO driver for hardware recording, live VST3 playing and take audition.
- **Work through four compact Auto Sample pages.** Connect; Map & Capture; Shape & Loop; Capture & Export. Rotary controls also accept typed values.
- **Shape and loop recordings.** Signal detection, trimming, DC removal, normalization, sustain-loop search within a percentage window, crossfades and optional crop after the loop are available.
- **Follow the instrument map while recording.** The current note/velocity is amber, completed takes are green and pending takes stay subdued. See elapsed time and an adapting estimate of time remaining.
- **Review, resume and reprocess.** Audition captured WAVs and their loops, pause after a take, resume an incomplete session, or reprocess retained recordings without capturing again.
- **Export a clean instrument folder.** The chosen folder receives the AKP and its WAVs directly. Working recordings and settings are managed separately. Completed working data is cleaned up only after verification, with an option to keep originals.
- **Transfer the finished sound.** Open the exported program in Files and send it with its sample dependencies to sampler RAM or disk.

### Improvements and fixes

- **Start Sampling** keeps the same label after a completed run or reopening the Editor. Page 4 identifies a previous export separately; saved settings remain available.
- Keyboard selection is remembered. Connecting waits for the instrument to become ready; Test Note changes to Stop Note while playing.
- LCD updates continue during keyboard input, and routine remote parameter changes preserve held MIDI notes. Longer USB jobs pause the Akai keyboard route.
- A delayed response from the Auto Sample component now releases held MIDI notes before the route recovers.
- VST3 Test Note works at 96 kHz and tolerates small differences in the interface's reported nominal rate. Exported Auto Sample WAVs remain at 44.1 or 48 kHz.
- Rapid audio-device stop/restart events are detected. Incomplete hardware takes are discarded and interrupted auditions report the problem.
- Reopening a copied or moved working project uses the selected folder, even when the original folder still exists.
- Open in Files waits for capture/export verification. Export-folder checks also protect working recordings when Windows paths use alternate names or letter case.
- Loop search handles additional sparse periodic sounds; saved loop audition follows the processed take's markers.
- Edited native Akai WAV exports preserve supported tuning, playback modes, fractional loop information and sample bounds. Trimming rebases the retained positions; unsafe or unsupported edits are refused with an explanation.
- Updated illustrated online/offline guides, printable manual and third-party notices.

The release executables passed **34 native Windows regression tests** and the Auto Sample UI smoke test. Additional local capture, MIDI, library and memory-error checks passed. These checks do not establish compatibility with every plugin, audio driver, sampler or library.

[Download and release notes](releases/v0.12.8-preview.md) · [Auto Sample guide](docs/AUTO_SAMPLER_GUIDE.md) · [Format limits](docs/FORMATS.md)

## 0.11.1 Preview — 26 October 2026

**First public Editor preview.** A standalone Windows x64 release for the AKAI S5000 and S6000.

- Live sampler display and familiar front-panel controls, recognised clickable LCD options, data adjustments and supported text entry.
- Computer and sampler file browsing; WAV, AKP and AKM transfers with dependencies; RAM and writable disk destinations.
- Supported S1000/S3000 disk-image libraries in ISO, NRG, BIN, CUE and IMG containers, with batch preparation and transfer.
- Waveform inspection, PC audition, selection and WAV-copy export.
- Per-file and overall transfer progress, stopping at a complete-file boundary, and optional upload read-back verification.
- Remembered file-picker folders and clearly grouped Akai image controls.
- Automatic LCD updates; screen capture and troubleshooting logs in Tools.
- **USB driver setup is available only in Tools.** Its former main-page button has been removed.
- Separate distribution from the firmware and Firmware Updater; illustrated online/offline guides and freeware/runtime notices included.

This preview follows private development and hardware testing of earlier builds. The small Tools-menu change and public package have passed software and offline GUI checks. The new Windows driver-assignment assistant still needs verification on a real Windows/sampler setup. See [release notes](releases/v0.11.1-preview.md) and [supported formats](docs/FORMATS.md).

Future releases will appear here with their additions, fixes and any relevant compatibility changes. Each GitHub Release carries its own versioned ZIP and checksum.
