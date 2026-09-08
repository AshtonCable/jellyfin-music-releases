<p align="center"><img src="icon.png" width="128" alt="Jellyfin Music icon"></p>

# Jellyfin Music

A Cupertino-style music player for your own [Jellyfin](https://jellyfin.org) server, for
Android, macOS and the web. Made by [Ashton Cable](https://ashtoncable.ca).

> [!WARNING]
> **Pre-release alpha software.** Jellyfin Music is unfinished and under continued
> development. Expect rough edges: some features may not work as expected yet, things
> will change between releases, and you may need to sign in again after updating.
> Please report anything broken on the [issues](../../issues) page.

This repository only holds **downloadable builds**. Grab the latest version from the
[Releases](../../releases/latest) page.

## Install

| Platform | File | How |
| --- | --- | --- |
| Android 7.0 or newer | `JellyfinMusic-x.y.z-release.apk` | Download on the phone and open it; allow installs from your browser if asked. |
| macOS 12 or newer (Intel and Apple silicon) | `JellyfinMusic-x.y.z-macos.zip` | Unzip, move *Jellyfin Music.app* to Applications, then right-click → Open the first time (the app is not notarised yet). |
| Web | `jellyfin-music-web.zip` | Unzip onto any static web host and open the URL. It must be served over HTTP, not opened as a file. |

Sign in with your server address (for a home server that is usually something like
`http://192.168.1.20:8096`), your Jellyfin username and password, or use Quick Connect.
Type `demo` as the server to explore the app with a built-in sample library.

## What it does

- Browse your library by album, artist, song, playlist and genre; search across all of it
- Full-screen player with synced lyrics, an up-next queue you can reorder, shuffle and repeat
- Gapless playback and optional crossfade
- Lock-screen / notification controls and headset buttons
- Download albums and playlists for offline listening (Android and macOS)
- Play on other Jellyfin devices in your home
- Light and dark themes, tinted from the album you are playing
- On a desktop-sized window: sidebar navigation, a player bar and a Now Playing side panel

## Privacy

The app talks to the Jellyfin server you sign in to and stores your sign-in token only on
your device. When your server has no lyrics for a song, the song's title, artist, album and
length are sent to [LRCLIB](https://lrclib.net) to look them up; you can turn this off in
Settings → Playback → Online Lyrics. Nothing else leaves your device.

## Privacy

Jellyfin Music collects no personal data; everything stays on your device and your own
Jellyfin server. The full policy is in [PRIVACY.md](PRIVACY.md), also available as
[HTML](privacy-policy.html) and [PDF](privacy-policy.pdf).

## Feedback

Problems or ideas? Open an issue on this repository.
