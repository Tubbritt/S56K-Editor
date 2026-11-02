# S56K Editor 0.12.8 Auto Sample Preview

**2 November 2026 · Windows 11 · Intel/AMD x64 · Freeware**

Play your sampler from a MIDI keyboard connected to the PC, and create new S5000/S6000 instruments by auto sampling hardware synths or 64-bit VST3 instruments inside the Editor.

**[Download the Windows ZIP](https://github.com/Tubbritt/S56K-Editor/releases/download/v0.12.8-preview/S56K-Editor-0.12.8-AutoSample-Preview-win64.zip) · [SHA-256](https://github.com/Tubbritt/S56K-Editor/releases/download/v0.12.8-preview/S56K-Editor-0.12.8-AutoSample-Preview-win64.zip.sha256) · [Complete changelog](https://github.com/Tubbritt/S56K-Editor/blob/v0.12.8-preview/CHANGELOG.md)**

## What's new since 0.11.1

- **MIDI Keyboard:** play the Akai over USB, an external MIDI synth or Auto Sample's loaded VST3. Computer-side instruments work without an Akai connected.
- **Integrated Auto Sample:** four pages for connection, note/velocity mapping, shaping/looping and capture/export. Record hardware through your audio interface or render a VST3 instrument on the PC.
- **ASIO support:** choose an installed manufacturer 64-bit driver, or use Windows audio.
- **Loop and shape:** signal detection, trimming, DC removal, normalization, loop-search regions, crossfading and optional cropping after the loop.
- **Visual capture progress:** follow the current note and velocity, completed/pending takes, elapsed time and estimated time remaining.
- **Clean native export:** your selected folder receives the AKP and its WAVs. Review and audition takes, resume incomplete sessions, reprocess retained originals and send the finished instrument to RAM or disk.
- **Native WAV editing:** edited exports retain supported Akai tuning, playback settings, loop information and sample bounds.

## Latest reliability fixes

Start Sampling keeps a consistent label, with the previous export identified separately. Copied projects use the selected folder; Open in Files waits for export verification. Test Note supports 96 kHz interfaces, quick audio-device interruptions are detected, and MIDI recovery releases held notes after a delayed response. Export-folder checks also protect working recordings under alternate Windows path names.

## Install or upgrade

1. Download the named Windows ZIP above and **extract all files into a new folder**.
2. Open **START_HERE.html** for the illustrated manual, then run **S56K-Editor.exe**. Keep the complete folder together, including **internal**.
3. For PC Auto Sample, select **AUTO SAMPLE**, choose Hardware or VST3, configure your devices and try a small instrument.
4. For sampler control and transfers, connect its **IB-S56USB card** using Microsoft **WinUSB**. Use **Tools → USB driver setup** if needed.

The Editor remembers previous settings and exports across launches. **Start Sampling** records a new run; **New patch** clears the name and review while keeping instrument, device, mapping and processing settings.

No ak.Sys installation or sampler firmware update is required. The firmware and Firmware Updater remain separate downloads. The previous public 0.11.1 release remains available for rollback.

## Guides and compatibility

- [Illustrated user guide](https://github.com/Tubbritt/S56K-Editor/blob/v0.12.8-preview/docs/USER_GUIDE.md)
- [MIDI Keyboard and Auto Sample](https://github.com/Tubbritt/S56K-Editor/blob/v0.12.8-preview/docs/AUTO_SAMPLER_GUIDE.md)
- [Printable PDF manual](https://github.com/Tubbritt/S56K-Editor/blob/v0.12.8-preview/docs/S56K-Editor-0.12.8-User-Guide.pdf)
- [USB setup](https://github.com/Tubbritt/S56K-Editor/blob/v0.12.8-preview/docs/USB_SETUP.md) · [Format limits](https://github.com/Tubbritt/S56K-Editor/blob/v0.12.8-preview/docs/FORMATS.md) · [Troubleshooting](https://github.com/Tubbritt/S56K-Editor/blob/v0.12.8-preview/docs/TROUBLESHOOTING.md)

Auto Sample creates AKP programs and mono/stereo PCM16 WAVs at 44.1 or 48 kHz. Hardware capture takes real time; accelerated VST3 speed and compatibility depend on the instrument and computer. The sampler's USB port does not carry audio. Sending an instrument to RAM is temporary: save it and its samples to disk when you want to keep it.

The release executables passed **34 native Windows regression tests** and the Auto Sample UI smoke test. Package contents and checksums were verified. Physical devices, plugins and libraries vary, so begin with a small capture or transfer and listen to the result.

Read the [licence](https://github.com/Tubbritt/S56K-Editor/blob/v0.12.8-preview/LICENSE.md), [disclaimer](https://github.com/Tubbritt/S56K-Editor/blob/v0.12.8-preview/DISCLAIMER.md) and [third-party notices](https://github.com/Tubbritt/S56K-Editor/blob/v0.12.8-preview/THIRD-PARTY-NOTICES.md). This repository distributes compiled applications, documentation and artwork; application source remains private.
