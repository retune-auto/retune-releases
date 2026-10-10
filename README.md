<p align="center"><img src=".github/retune-icon.png" width="128" alt="Retune"></p>

# Retune releases

Signed builds of Retune, the Android head-unit launcher for the 2009 Lexus IS350, built on Chassis.

Each [release](https://github.com/retune-auto/retune-releases/releases) holds two files, published by CI when Retune is released:

- `retune-<version>.apk`, the signed app.
- `manifest.json`, which Retune reads to update itself.

There's no source code here.

## How Retune updates

Retune checks [the newest release's manifest](https://github.com/retune-auto/retune-releases/releases/latest/download/manifest.json) shortly after it starts, and every few hours after that.

When the manifest lists a newer build number, Retune downloads the APK in the background. It keeps the APK only if the file matches the manifest's SHA-256 checksum. Settings → Updates then shows the release and what's new in it. Installing waits until the car is parked, and Android asks for one confirmation.

Releases numbered 0.x are previews. They're marked as pre-releases, which Retune's update check skips.

## Installing by hand

An update must be signed with the same key as the Retune it replaces. If Retune was installed from a laptop (a debug build), uninstall it, then install an APK from here once. Every update after that arrives on its own.

To check a download by hand, compare it with the manifest:

```sh
shasum -a 256 retune-<version>.apk
```
