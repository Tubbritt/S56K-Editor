# Changelog

[Home](README.md) · [Downloads](releases/README.md) · [User guide](docs/USER_GUIDE.md)

## 0.12.9 — 22 November 2026

Improved USB connection handling during idle periods and LCD updates.

- Keeps the connected sampler awake through WinUSB where supported, restoring the previous device policy when the connection closes.
- Recovers from specific LCD-read timeouts and stalls, checking communication before continuing.
- Keeps the session open when the sampler cleanly refuses an LCD request, allowing a later screen update.
- Pauses LCD polling during Windows sleep and allows time to settle after resume.
- Adds USB operation and recovery details to troubleshooting logs.
- Stops safely when a command's result is uncertain, without automatically repeating file writes, MIDI events or parameter changes.
- Updates the online, offline and PDF guides with USB setup and troubleshooting information.

MIDI Keyboard, PC Auto Sample, ASIO, instrument export and library management remain included. Supported file formats are unchanged.

[Download and release notes](releases/v0.12.9.md) · [USB setup](docs/USB_SETUP.md) · [Troubleshooting](docs/TROUBLESHOOTING.md)
