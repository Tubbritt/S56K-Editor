# Maintaining this release repository

[Downloads](README.md) · [Changelog](../CHANGELOG.md)

This repository contains **compiled releases, user documentation and artwork only**. Application source, build scripts, debugging files, private diagnostic reports and sample libraries do not belong here.

## A new release

1. Prepare and check a new versioned Windows ZIP, including its offline guide and licence notices.
2. Write concise release notes and update `CHANGELOG.md` with the current version's changes. Keep development and validation records in the private repository.
3. Create a GitHub Release with a version tag, without a preview or prerelease label. Attach the Windows ZIP and its SHA-256 checksum as release assets.
4. Point the landing-page download link at those assets. Keep only the current version available publicly; archive previous downloads and release records privately before removing them.
5. Check the public download, checksum, guide links and screenshots after publication.

The repository includes a release-only upload workflow. It checks the reviewed ZIP against a fixed SHA-256, creates a draft release if the version has no release yet, and attaches the ZIP and checksum. Push the reviewed main commit and its matching version tag together; the workflow verifies that the tag points to that commit. It downloads the attached assets again and checks that they match the reviewed package. Published assets are verified on reruns rather than replaced. Verify the uploaded assets before publishing the draft. For a later version, update its tag, paths and expected digest together; it never builds the Editor or reads the private development repository.

Keep the version, download filename, manual and release links consistent throughout the repository. Public notes should describe what changed and how to use the application.

## Repository presentation

Suggested About description:

> A modern Windows companion for AKAI S5000 and S6000: MIDI keyboard, hardware/VST3 Auto Sample, remote control and library transfers.

Suggested topics: `akai`, `s5000`, `s6000`, `sampler`, `windows`.

The ready-to-upload social graphic is [social-preview.png](../assets/artwork/social-preview.png), **1280 × 640**, under **1 MB**. Download the PNG, open the repository's [Settings](https://github.com/Tubbritt/S56K-Editor/settings), and use **Social preview → Edit → Upload an image**. The PNG stored in the repository does not by itself assign GitHub's social preview.

See [GitHub's social-preview instructions](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/customizing-your-repositorys-social-media-preview) for the current upload location. Social platforms may cache an earlier preview after an image changes.
