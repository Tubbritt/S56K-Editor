# Maintaining this release repository

[Downloads](README.md) · [Release history](../CHANGELOG.md)

This repository contains **compiled releases, user documentation and artwork only**. Application source, build scripts, debugging files, private diagnostic reports and sample libraries do not belong here.

## A new release

1. Prepare and check a new versioned Windows ZIP, including its offline guide and licence notices.
2. Add a release-note page and update `CHANGELOG.md` with the actual changes and testing scope.
3. Create a GitHub Release with a version tag. Attach the Windows ZIP and its SHA-256 checksum as release assets.
4. Point the landing-page download link at those assets. Keep previous releases available for rollback.
5. Check the public download, checksum, guide links and screenshots after publication.

The repository includes a release-only upload workflow. It checks the reviewed ZIP against a fixed SHA-256 before attaching the ZIP and checksum to its existing release. For a later version, update its version, paths and expected digest together; it never builds the Editor or reads the private development repository.

Preview releases should remain marked as prereleases until their release criteria are met. Links to `/releases/latest` skip prereleases; use the explicit tag or release listing for previews.

## Repository presentation

Suggested About description:

> A modern Windows companion for AKAI S5000 and S6000 samplers. Remote control, sample and program transfers, and classic Akai disk-image libraries.

Suggested topics: `akai`, `s5000`, `s6000`, `sampler`, `windows`.

The ready-to-upload social graphic is [social-preview.png](../assets/artwork/social-preview.png), **1280 × 640**, under **1 MB**. Download the PNG, open the repository's [Settings](https://github.com/Tubbritt/S56K-Editor/settings), and use **Social preview → Edit → Upload an image**. The PNG stored in the repository does not by itself assign GitHub's social preview.

See [GitHub's social-preview instructions](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/customizing-your-repositorys-social-media-preview) for the current upload location. Social platforms may cache an earlier preview after an image changes.
