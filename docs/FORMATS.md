# Formats and compatibility

[Home](../README.md) · [User guide](USER_GUIDE.md) · [Troubleshooting](TROUBLESHOOTING.md)

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
- Recognised native Akai WAV metadata uses its own checks and is not treated as generic WAV metadata. Unrecognised native layouts are refused rather than silently discarded.
- PC waveform selection and normalisation apply to **Export WAV copy**. Sending to RAM uses the whole selected source file.

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

This preview combines remote front-panel operation, PC waveform inspection, instrument transfers, sampler-disk management and supported legacy-image import. Dedicated graphical keygroup/effects editors, an indexed library and automatic loop finding are not included.

Windows 11 on Intel/AMD x64 with an IB-S56USB-equipped S5000/S6000 is the target configuration. Stock OS 2.14 and S56K Expanded Edition are the initial OS targets. Other operating systems, ARM Windows and every sampler expansion/media combination have not been established as supported.

Earlier development builds have been used with sampler hardware for transfers and selected legacy instruments. That experience does not establish every library or hardware combination. The new USB driver assistant has software and offline interface checks; Windows UAC and actual driver reassignment still need broader testing on real PCs.
