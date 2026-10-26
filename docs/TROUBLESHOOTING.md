# Troubleshooting

[Home](../README.md) · [User guide](USER_GUIDE.md) · [USB setup](USB_SETUP.md) · [Formats](FORMATS.md)

## The sampler is missing or Connect fails

Close ak.Sys, the Firmware Updater and other USB tools. Check the sampler's power, IB-S56USB card, cable and PC port. In the disconnected Editor, open **Tools → USB driver setup…** and follow the [USB guide](USB_SETUP.md). A working driver does not need reinstalling.

## The display is not updating

Open **SAMPLER** and keep the Editor visible. Updates pause during transfers, dialogs, active control gestures and when the window is minimised. A recoverable display-read error is retried automatically after a short delay. A lost USB connection still requires reconnecting.

The display uses the sampler's native LCD resolution. **Tools → Save LCD image…** saves its latest received frame; it is not a higher-resolution render.

## A program says a sample is missing

A file on the PC is different from a sound already loaded in sampler RAM. Enable **Dependencies: ON** and keep the program and associated WAVs together in the same PC folder. Multis also need their AKP programs. With dependencies off, the referenced sounds must already be in RAM under the expected names.

For image imports, read the notices and dependency error. The image may contain multiple different candidates or genuinely missing data. Renaming a source at random will not repair its references.

## A transfer reports an existing or ambiguous name

Existing sampler contents are protected against silent replacement. Use a new destination folder, a different valid RAM name, or a sampler session without conflicting objects.

Within a batch, matching shared files can be combined and resolvable different-content collisions receive unique names. Multiple source samples with the same reference name but different prepared content remain ambiguous. That is different from several programs correctly sharing one sample.

## A legacy image opens, but an instrument cannot be sent

Opening the catalogue only establishes that its directory can be read. Preparation also checks sample data, program settings, loops and dependencies. Read the exact error and [format limits](FORMATS.md). An incomplete or damaged image needs an intact copy; unsupported content is not silently converted with missing settings.

For BIN/CUE libraries, keep the files together and open the CUE. Do not rename an unsupported file extension to make it appear supported.

## Transfers seem slow

The original USB hardware limits performance. A library of many small files also needs more checks than one large WAV.

The progress window separates **Sending**, **Verifying**, and **Checks / preparation**. With **Tools → Verify uploads by reading back** on, each uploaded file is also returned for comparison. Turning it off can reduce total time, but removes that returned-content comparison. It does not increase the underlying sending rate.

## I stopped a transfer, but some sounds remain

**Stop after current file** completes the active file before stopping. Completed files stay in RAM or on disk. A failed operation may also leave partial objects/files or new folders. Inspect the destination and log before retrying; there is no automatic rollback or resume.

## My waveform edit was not sent

Selection and **Normalise** affect **Export WAV copy**. Export the edit, select that new WAV and send it. **Send to RAM** uses the whole selected file. **PC Play** plays through the PC's audio output.

## What are the old import folders?

Early versions created prepared-instrument folders under `%LOCALAPPDATA%\S56K Editor\Imported Images`. Current image transfers do not create or use them.

If that location exists, **Tools → Review legacy import folders…** opens it in Explorer. Keep or move anything you need, then remove unwanted files yourself. The Editor never deletes them automatically.

## How do I check the download?

Use the checksum file attached beside the ZIP on the [release page](https://github.com/Tubbritt/S56K-Editor/releases/tag/v0.11.1-preview). In PowerShell, run this against the ZIP you downloaded, adjusting the path if needed:

```powershell
Get-FileHash -LiteralPath "$env:USERPROFILE\Downloads\S56K-Editor-0.11.1-Preview-win64.zip" -Algorithm SHA256
```

Its Hash must match the supplied ZIP checksum. `SHA256SUMS.txt` inside the extracted package covers the individual files. A checksum confirms matching bytes, not universal compatibility or a guarantee against bugs.

## Reporting a problem

1. Save **Tools → Save troubleshooting log…** after the failure.
2. Note the Editor version, sampler model/OS, Windows version and whether you were using RAM, disk or an image.
3. Describe the steps and include the exact error or a screenshot. For image issues, include the container type and affected item name if you can share them.
4. Review the log before sharing: it can contain local paths and filenames. Do not upload sample audio, complete commercial libraries or other material you do not have permission to share.

The log contains no sample audio and is never uploaded automatically. Report issues at [S56K Editor issues](https://github.com/Tubbritt/S56K-Editor/issues).

[Disclaimer](../DISCLAIMER.md) · [Licence](../LICENSE.md)
