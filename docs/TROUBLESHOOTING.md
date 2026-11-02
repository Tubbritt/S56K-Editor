# Troubleshooting

[Home](../README.md) · [User guide](USER_GUIDE.md) · [Auto Sample](AUTO_SAMPLER_GUIDE.md) · [USB setup](USB_SETUP.md) · [Formats](FORMATS.md)

## The sampler is missing or Connect fails

Close ak.Sys, the Firmware Updater and other USB tools. Check the sampler's power, IB-S56USB card, cable and PC port. In the disconnected Editor, open **Tools → USB driver setup…** and follow the [USB guide](USB_SETUP.md). A working driver does not need reinstalling.

## The display is not updating

Open **SAMPLER** and keep the Editor visible. Updates pause during transfers, dialogs, active control gestures and when the window is minimised. A recoverable display-read error is retried automatically after a short delay. A lost USB connection still requires reconnecting.

Enabling the MIDI keyboard does not pause the LCD by itself. Very dense notes or controller traffic can reduce its update rate because keyboard events take priority. Transfers temporarily pause the Akai keyboard route as well.

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

## My edited native WAV has a warning about its loop

A trim that cuts through a native loop removes that loop and disables looped
playback in the exported copy. Review the warning before saving. To keep the
loop, adjust the trim so the entire loop and at least 15 frames after its
inclusive end remain. A trim with no remaining playable audio is refused.
Unsupported native metadata is also refused for edited export rather than
silently stripped. The original file is unchanged.

## The MIDI keyboard connects but I hear nothing

Check the destination in **MIDI KEYBOARD**. **Akai sampler - USB** needs a
connected sampler, a loaded playable program and the appropriate logical input
A/B and channel. Its sound comes from the sampler's audio outputs, not the PC's
speakers.

For **Auto Sample instrument**, choose a hardware MIDI output or load a VST3 in
**AUTO SAMPLE → CONNECT**. VST3 also needs an active computer audio output. A
hardware synth needs the correct receiving channel and an audio monitoring path;
the Editor does not automatically monitor its audio inputs. This route works
without an Akai connection.

Choose the keyboard explicitly if a saved input is unavailable. Close other
software holding an exclusive MIDI/audio device. Click **Connect** once and wait
for the ready status. **Disconnect** stops forwarding; closing the keyboard
window alone does not.

## Keyboard playing pauses or a note stays held

Auto Sample deliberately pauses manual keyboard input during automatic capture,
Test Note or an instrument/device change so played notes cannot enter a take.
Use **Stop note** to end a Test Note. The Akai route pauses during file transfers.
Play fresh notes once the route is ready again; delayed notes are discarded.

Use **Panic** to release held notes, then check the connection. Version 0.12.8
also releases a previously playable Auto Sample route before recovering from a
delayed helper response. A plugin that is itself unresponsive can still require
closing and reopening the Editor.

## ASIO is missing or VST3 playback crackles

Install your interface manufacturer's **64-bit Windows ASIO driver**, then open
**AUTO SAMPLE → CONNECT → Audio settings** and select ASIO and that interface.
Microsoft WinUSB is the sampler's USB driver; it is unrelated to the computer's
audio-interface driver. Neither the interface driver nor a VST3 instrument is
included with the Editor.

Enable the required output channels and try a 256- or 512-sample buffer. Increase
the buffer if playback still drops out. Check the plugin's CPU/disk use and close
other software that may hold the interface. Windows audio remains available.
Test Note follows the device rate, including 96 kHz; Auto Sample output files
remain at 44.1 or 48 kHz.

## A hardware capture has silence or stops unexpectedly

Connect both paths: computer MIDI output to the synth, and synth audio outputs
to the selected computer-interface inputs. MIDI alone carries no sound. Check
MIDI channel, input channel selection, physical input level and the meter with
one Test Note before capturing a full grid.

A trigger threshold above the sound's level can miss quiet velocity layers.
An end threshold too low for a noisy input may never detect silence. Increase
Note Time for a slow attack; trigger waiting does not postpone Note Off. Read the
notice under **Details…** for the specific failure.

An audio-device stop or restart during recording discards the unfinished take.
Completed recordings remain available for **Resume project**. Restore the device
and confirm its input/rate settings before retrying; do not change devices during
a run.

## Accelerated VST3 sampling sounds wrong

Turn off **Accelerated rendering** and try a small capture with paced processing.
Some instruments rely on disk streaming, real-time behaviour, external devices
or services. Check that the correct preset is loaded and give its samples time
to load before starting. Plugin-specific licensing and content must be working
outside capture too. VST2 and 32-bit instruments are not hosted by this release.

## The exported sound is not looped or cropped as expected

Enable **Auto Loop** on **03 SHAPE & LOOP**, choose a sustained region inside the
held note, and enable **Crop after loop** if wanted. **Audition loop** on page 4
only changes review playback; it does not create a loop.

For existing recordings, change processing and choose **Reprocess recordings**,
then export the new revision. Inspect the **Export WAV copy** review and the exported
files, not only the original recording. Crop after loop retains a small guard
area required by the sampler. Read any loop-search warning and audition the result;
evolving or noisy sounds may need a different search region or no loop.

## A previous patch appears when I reopen the Editor

The Editor remembers its settings and previous export independently of the
executable. Opening a fresh copy of the app therefore does not clear them.
Page 4 identifies the previous export. **Start Sampling** always records a new
run; it does not automatically resume that old project. **New Patch** clears the
name and review while keeping the current instrument and setup choices.

## I cannot find the working recordings, or export asks to replace files

The export folder contains the AKP and its WAVs. Working recordings and recovery
information live separately under `%LOCALAPPDATA%\S56K\Editor\AutoSampleWork`.
Choose **Resume project** to open retained work. Completed working data is eligible
for cleanup on normal close only after the export and working inventory verify;
incomplete or failed sessions stay available.

To keep original recordings for later reprocessing, enable **Details… → Keep
working recordings after closing** before closing. If they have already been
cleaned up, the exported AKP/WAVs remain, but a new capture is needed to recreate
the original working recordings.

When different files already occupy the export names, choose **Keep existing**,
select another export folder and use **Export files**. Recording again is not
necessary. Approve **Replace existing files** only when you want to replace those
exports. **Open in Files** is unavailable until recording and export verification
finish.

## What are the old import folders?

Early versions created prepared-instrument folders under `%LOCALAPPDATA%\S56K Editor\Imported Images`. Current image transfers do not create or use them.

If that location exists, **Tools → Review legacy import folders…** opens it in Explorer. Keep or move anything you need, then remove unwanted files yourself. The Editor never deletes them automatically.

## How do I check the download?

Use the checksum file attached beside the ZIP on the [release page](https://github.com/Tubbritt/S56K-Editor/releases/tag/v0.12.8-preview). In PowerShell, run this against the ZIP you downloaded, adjusting the path if needed:

```powershell
Get-FileHash -LiteralPath "$env:USERPROFILE\Downloads\S56K-Editor-0.12.8-AutoSample-Preview-win64.zip" -Algorithm SHA256
```

Its Hash must match the supplied ZIP checksum. `SHA256SUMS.txt` inside the extracted package covers the individual files. A checksum confirms matching bytes, not universal compatibility or a guarantee against bugs.

## Reporting a problem

1. Save **Tools → Save troubleshooting log…** after the failure.
2. Note the Editor version, Windows version and the feature in use. For transfers, include the sampler model/OS and RAM, disk or image destination. For Auto Sample, include hardware or VST3 source, plugin version, audio driver, sample rate and buffer size.
3. Describe the steps and include the exact error or a screenshot. For Auto Sample, include the notice from **Details…**. For image issues, include the container type and affected item name if you can share them.
4. Review the log before sharing: it can contain local paths and filenames. Do not upload sample audio, complete commercial libraries or other material you do not have permission to share.

The log contains no sample audio and is never uploaded automatically. Report issues at [S56K Editor issues](https://github.com/Tubbritt/S56K-Editor/issues).

[Disclaimer](../DISCLAIMER.md) · [Licence](../LICENSE.md)
