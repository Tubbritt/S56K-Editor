# Formats and compatibility

[Home](../README.md) · [User guide](USER_GUIDE.md) · [Auto Sample](AUTO_SAMPLER_GUIDE.md) · [Troubleshooting](TROUBLESHOOTING.md)

**Opening a file or image does not guarantee that every item inside it can be transferred.** The Editor checks the selected sounds and their dependencies before uploading and reports unsupported or ambiguous content.

## Computer files

| File | Send to RAM | Send to sampler disk |
|---|---|---|
| **WAV** | Supported mono/stereo audio is prepared as PCM16. Recognised Akai settings are preserved; unsafe or unsupported metadata is refused. | Copies the original file bytes; this does not guarantee the sampler can load every WAV encoding. |
| **AKP** | Native S5000/S6000 programs, with associated WAVs when Dependencies is on. | Program and associated files when requested. |
| **AKM** | Native S5000/S6000 Multis, with associated programs and samples when Dependencies is on. | Multi and associated files when requested. |
| **Other files** | Not supported as playable RAM objects. | Individual exact file copies may be possible; no promise of sampler compatibility. |

AKP and AKM files do not contain their sample audio. Keep associated files together in the same PC folder for dependency discovery.

### WAV details

- PC waveform input accepts mono/stereo PCM8, PCM16, PCM24, PCM32 or float32, including equivalent extensible headers. Compressed and surround WAVs are not supported.
- RAM preparation uses the original sample rate when representable, from 1 to 65,535 Hz. It does not resample the audio.
- Generic WAV loop import supports an integer root note and one forward loop with sufficient audio after the loop end. Fractional tuning/loop offsets and repeat counts are not supported by that conversion path.
- Recognised native Akai WAV metadata uses its own checks and is not treated as generic WAV metadata. Supported native v1/v2 settings include tuning, playback bounds/mode and zero or one supported loop, including supported fractional settings. Unrecognised native layouts are refused rather than silently discarded.
- **Export WAV copy** preserves supported native settings in full-range or normalized copies. A trim intersects and rebases playback bounds and intact loops. A cut loop is removed with a review before saving; looped playback is then disabled. A retained active loop needs 15 frames after its inclusive end. A trim leaving no playable audio or insufficient loop guard space is refused.
- PC waveform selection and normalisation apply to the exported copy. Sending to RAM uses the whole selected source file. PC playback does not apply pending edits or emulate Akai tuning and playback settings.

## Auto Sample sources and output

| Item | Supported in this preview |
| --- | --- |
| **Hardware source** | MIDI-controlled instrument connected to a computer MIDI output, with its audio connected to the computer interface's inputs. MIDI alone carries no audio. |
| **Plugin source** | Compatible **64-bit Windows VST3 instruments**. VST2, AU, AAX and 32-bit plugin bridging are not included. |
| **Audio devices** | ASIO with the manufacturer's installed 64-bit driver, or supported Windows audio devices. No interface drivers are bundled. |
| **Live VST3 audition** | Uses the selected audio-interface rate; Test Note supports 96 kHz as well as the export rates. |
| **Export** | Native S5000/S6000 **AKP + PCM16 WAV**, mono or stereo, at **44.1 or 48 kHz**. Auto Sample does not create AKM Multis. |
| **Mapping** | Up to **99 keygroups**, **1–4 velocity layers** per keygroup; program key ranges from **A0 (MIDI 21) to G9 (MIDI 127)**. |
| **Loops** | One sustained forward loop per recording, shared by stereo channels. Optional crossfade and crop-after-loop retain the required interpolation guard frames. |
| **Capture processing** | Trigger and silence detection, trimming, DC removal, normalization and sustain-loop search. Saved originals can be reprocessed while retained. |

These Auto Sample output restrictions are separate from the existing WAV-transfer
rules above. A 96 kHz audio device can be used for VST3 audition; it does not make
96 kHz an Akai Auto Sample export format.

**Accelerated rendering** asks the plugin to process faster than real time.
Actual speed depends on the instrument and computer. Plugins that need paced
processing may need this option disabled. Hardware capture follows real time.
Instruments requiring external devices, online services or real-time-only
behaviour may not work in accelerated mode. Plugin licensing and content access
remain the user's responsibility; no instruments or sample libraries are bundled.

The AKP and referenced WAVs are written directly into the selected export folder.
Internal working recordings, plugin state and recovery files are kept separately;
see [recording retention and recovery](AUTO_SAMPLER_GUIDE.md#keep-recordings-for-later-reprocessing).
Keep exported AKP/WAV files together. A project on the PC can exceed sampler RAM,
but the instrument must fit available memory when loaded into RAM.

## MIDI keyboard routing

A computer MIDI input can control the Akai over its USB card, or Auto Sample's
selected external MIDI output / loaded VST3. The Auto Sample instrument route
works without a connected sampler. The Editor does not install a virtual MIDI
port for other Windows applications, and sampler USB does not carry audio.

The Akai route pauses during file transfers. Auto Sample's instrument route
pauses during capture, Test Note and instrument/device changes. Late events are
discarded rather than played afterward; held notes are released when changing
routes. See the [MIDI setup guide](AUTO_SAMPLER_GUIDE.md#play-from-a-midi-keyboard).

## Library images

| Container | Supported layouts |
|---|---|
| **ISO / BIN / IMG** | Raw 2,048-byte data sectors, or validated 2,352-byte Mode 1 / Mode 2 Form 1 sectors. The extension alone does not identify the disc contents. |
| **CUE + BIN** | One supported data track in one local BINARY file. Includes supported 2,336-byte Mode 2 Form 1 layouts. Keep both files together and open the CUE. |
| **NRG** | Supported Nero v1/v2 DAO/TAO containers with one validated data track. |

Supported mixed audio/data layouts import only their validated data track. Audio-only discs, ambiguous data-track choices, multisession, Form 2 and subchannel-bearing layouts remain unsupported.

The reader supports known S1000/S3000 program and sample records in Akai volumes, including supported CD3000 layouts. It also browses supported native WAV/AKP/AKM files in ISO9660/Joliet folders.

A firmware BIN is not a library image. The Editor does not install firmware.

### Legacy conversion

The Editor prepares supported legacy programs and samples into S5000/S6000 AKP/WAV files. It retains supported settings and reports conversions that cannot preserve a source feature. Listen to the result, particularly tuning, envelopes, release behaviour and loops.

Known limits include:

- **Legacy Multis, effects records, drum settings, cue/take lists, direct-to-disk recordings and legacy OS files** are not imported as playable instruments by this workflow.
- Active finite-loop dwell and multiple-loop behaviour that cannot be represented safely remain unsupported.
- Missing sample data, malformed active ranges and unresolved references remain errors.
- Equivalent sample copies can be reused within a batch only when their complete prepared content and settings agree. Similar names or identical audio alone are not enough.
- Different sounds with the same name are given unique destination names only when their program references can be resolved. Truly ambiguous source references stop preparation.

A disc can have readable volumes alongside skipped or damaged parts. Read **Image notices** and the transfer review. Missing source data cannot be recreated by the Editor.

## Size and destination limits

| Limit | Meaning |
|---|---|
| **WAV file input: 256 MiB** | Per source WAV; decoded working audio is limited to 512 MiB. |
| **Disk upload: smaller than 256 MiB** | Per individual nonempty file, not the total library. |
| **AKP/AKM: 1 MiB** | Per parameter file. |
| **RAM transfers** | Must fit the sampler's available sample memory. Program/object memory can also run out. |
| **New RAM names** | 1–20 printable ASCII characters, excluding reserved filename characters, leading/trailing spaces and a trailing dot. |

Image-to-disk batches can exceed sample RAM because their files are written to disk without loading the complete library into RAM. Capacity estimates still depend on media condition, free space and filesystem overhead.

## Release scope

This preview combines remote front-panel operation, MIDI keyboard routing, PC waveform inspection, instrument transfers, sampler-disk management, supported legacy-image import and integrated hardware/VST3 Auto Sample. Automatic loop finding is available for Auto Sample recordings. Dedicated graphical keygroup/effects editors and an indexed library remain outside this release.

Windows 11 on Intel/AMD x64 is the target computer configuration. Remote control and transfers require an IB-S56USB-equipped S5000/S6000 with Microsoft WinUSB; stock OS 2.14 and S56K Expanded Edition are the OS targets. PC Auto Sample and its instrument keyboard route do not require the sampler to be connected. Other operating systems, ARM Windows and every sampler expansion/media combination have not been established as supported.

Earlier development builds have been used with sampler hardware for transfers and selected legacy instruments. Version 0.12.8 passed 34 native Windows regression tests and its UI smoke test. Automated fixtures do not establish every sampler, audio interface, ASIO driver, plugin or library combination. Start with a small instrument on your setup; Windows driver-selection choices can vary between installations.
