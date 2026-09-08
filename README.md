<p align="center"><img src="icon.png" width="128" alt="Jellyfin Music icon"></p>

# Jellyfin Music

A Cupertino-style music player for your own [Jellyfin](https://jellyfin.org) server, for
Android, macOS, iPhone and iPad (as a web app) and the web. Made by
[Ashton Cable](https://ashtoncable.ca).

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
| macOS 12 or newer (Intel and Apple silicon) | `JellyfinMusic-x.y.z-macos.zip` | Unzip and move *Jellyfin Music.app* to Applications. The first launch is blocked by macOS because the app is not notarised: see [Opening on macOS](#opening-on-macos) below (one time, about 30 seconds). |
| iPhone and iPad | web app (nothing to download) | Open the hosted web version in **Safari**, tap **Share → Add to Home Screen**, then launch it from the Home Screen. There is **no `.ipa` in the releases** at the moment. See [iPhone and iPad](#iphone-and-ipad) below. |
| Web | `jellyfin-music-web.zip` | Unzip onto HTTPS web hosting at the root of a domain or subdomain (the bundle is built for base href `/`) and open the address. Your Jellyfin server must be reachable over HTTPS, otherwise the browser blocks the connection. The web version streams only, no downloads. Hosting guide: [web-hosting.md](web-hosting.md). |

## Opening on macOS

Apple only lets apps open without a warning when their developer pays for an Apple Developer
account and notarises every build. Jellyfin Music is signed but not notarised, so macOS blocks
it the first time you open it. You only have to do this once per version; after that it opens
like any other app.

**macOS 15 Sequoia and macOS 26**

1. Double-click *Jellyfin Music.app*. A message says *"Apple could not verify 'Jellyfin Music'
   is free of malware…"*. Click **Done** (not *Move to Trash*).
2. Open **System Settings → Privacy & Security** and scroll down to the **Security** section.
3. You will see *"Jellyfin Music" was blocked to protect your Mac.* Click **Open Anyway**.
4. Confirm with **Open Anyway** in the dialog that follows and enter your password or use
   Touch ID if asked.

**macOS 12, 13 and 14**

Right-click (or Control-click) *Jellyfin Music.app* and choose **Open**, then click **Open** in
the dialog. If that does not offer an Open button, use the System Settings steps above.

If macOS says the app is "damaged", the download was quarantined by the browser. Run
`xattr -dr com.apple.quarantine "/Applications/Jellyfin Music.app"` in Terminal and open it
again. The same steps are in the `READ ME FIRST` file inside the zip.

Sign in with your server address (for a home server that is usually something like
`http://192.168.1.20:8096`), your Jellyfin username and password, or use Quick Connect.
Type `demo` as the server to explore the app with a built-in sample library.

## What it does

- Browse your library by album, artist, song, playlist and genre; search across all of it
- Full-screen player with synced lyrics, an up-next queue you can reorder, shuffle and repeat
- Gapless playback and optional crossfade
- Lock-screen / notification controls and headset buttons
- Download albums and playlists for offline listening (Android and macOS); on Android you can
  keep downloads on an SD card or USB drive when the device has one (Settings → Storage)
- Play on other Jellyfin devices in your home
- Light and dark themes, tinted from the album you are playing
- On a desktop-sized window: sidebar navigation, a player bar and a Now Playing side panel

## iPhone and iPad

The way to run Jellyfin Music on an iPhone or iPad today is the **web app**:
open the hosted web version in Safari, tap **Share → Add to Home Screen**, and
launch it from the Home Screen. It runs full screen with its own icon, keeps
you signed in, and shows Now Playing on the Lock Screen.

**No `.ipa` is published.** Building one needs a Mac with Apple's iOS platform
tools installed, and installing one needs a signing tool such as AltStore or
Sideloadly plus your own Apple ID. If an unsigned `.ipa` is added to a future
release, it will be listed in the table above.

> [!NOTE]
> **iOS has not been tested on a real device.** There is no iPhone or iPad
> available to test on, only the simulator on a Mac, so anything specific to
> real hardware — background audio, Lock Screen controls, the local-network
> permission prompt, audio interruptions from calls — is untested and may not
> work. The web app is the supported route on iOS; treat native iOS as
> experimental.

## Downloads on an SD card (Android)

If your phone or tablet has an SD card or a USB drive, **Settings → Storage** lets you choose
where new downloads are saved (the option only appears when such storage exists). You can move
existing downloads to the new location; songs on a card that is out of the device show as
unavailable until you put it back, re-download them or remove them.

## Privacy

Jellyfin Music collects no personal data. The app talks only to the Jellyfin server you sign
in to and stores your sign-in token on your device. When your server has no lyrics for a song,
the song's title, artist, album and length are sent to [LRCLIB](https://lrclib.net) to look
them up; you can turn this off in Settings → Playback → Online Lyrics. Nothing else leaves your
device. The full policy is published at
[ashtoncable.github.io/jellyfin-music-releases/privacy-policy.html](https://ashtoncable.github.io/jellyfin-music-releases/privacy-policy.html)
and kept here as [PRIVACY.md](PRIVACY.md), [HTML](privacy-policy.html) and [PDF](privacy-policy.pdf).

## Support and feedback

Problems or ideas? Open an issue on this repository or email
[ashton@ashtoncable.ca](mailto:ashton@ashtoncable.ca).
