# Downloads

[Home](../README.md) · [Release history](../CHANGELOG.md) · [Manual](../docs/USER_GUIDE.md)

## S56K Editor 0.11.1 Preview

| Download | Contents |
| --- | --- |
| **[Windows x64 ZIP](https://github.com/Tubbritt/S56K-Editor/releases/download/v0.11.1-preview/S56K-Editor-0.11.1-Preview-win64.zip)** | Editor executable, illustrated offline guide, documentation, licence and third-party notices. |
| **[SHA-256 checksum](https://github.com/Tubbritt/S56K-Editor/releases/download/v0.11.1-preview/S56K-Editor-0.11.1-Preview-win64.zip.sha256)** | Check that the downloaded ZIP matches this release. |
| **[GitHub Release](https://github.com/Tubbritt/S56K-Editor/releases/tag/v0.11.1-preview)** | Versioned download assets and release notes. |

Extract into a new folder. Open **START_HERE.html**, then run **S56K-Editor.exe**. Keep the complete extracted folder together. This is a portable Windows x64 app; no separate runtime installation is required.

The firmware and standalone updater are [separate downloads](https://github.com/Tubbritt/S56K-Expanded-Edition/releases). They are not bundled here.

## Check a download

In PowerShell, run the following using the path to your downloaded ZIP:

```powershell
Get-FileHash -LiteralPath "$env:USERPROFILE\Downloads\S56K-Editor-0.11.1-Preview-win64.zip" -Algorithm SHA256
```

Compare its `Hash` with the `.sha256` file attached to the same release. Letter case does not matter. If they differ, download the ZIP again and do not use the mismatched copy.

GitHub also generates archives labelled **Source code** for every release tag. In this repository those archives contain the public documentation and artwork, **not the Editor's application source or its Windows executable**. Use the named Windows ZIP above.

[Read the 0.11.1 release notes](v0.11.1-preview.md) · [Licence](../LICENSE.md) · [Disclaimer](../DISCLAIMER.md)
