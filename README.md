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
[Releases](../../releases/latest) page. The newest release is **1.2.0 (alpha)** for Android
and the web; macOS and iPhone/iPad app builds are still at 1.1.0 — see the note under the
table.

## Install

| Platform | File | How |
| --- | --- | --- |
| Android 7.0 or newer | `JellyfinMusic-x.y.z-release.apk` (latest release) | Download on the phone and open it; allow installs from your browser if asked. The APK is signed with a debug key, so Android will call it an unknown developer. |
| Web | `jellyfin-music-web.zip` (latest release) | Unzip onto HTTPS web hosting at the root of a domain or subdomain (the bundle is built for base href `/`) and open the address. Your Jellyfin server must be reachable over HTTPS, otherwise the browser blocks the connection. The web version streams only: no downloads and no offline mode. Hosting guide: [web-hosting.md](web-hosting.md). |
| macOS 12 or newer (Intel and Apple silicon) | `JellyfinMusic-1.1.0-macos.zip`, from the [1.1.0 release](../../releases/tag/v1.1.0) — see the note below | Unzip and move *Jellyfin Music.app* to Applications. The first launch is blocked by macOS because the app is not notarised: see [Opening on macOS](#opening-on-macos) below (one time, about 30 seconds). |
| iPhone and iPad | web app (nothing to download), or `JellyfinMusic-1.1.0-unsigned.ipa` from the [1.1.0 release](../../releases/tag/v1.1.0) | Easiest, and the only way to get 1.2.0 on iOS: open the hosted web version in **Safari**, tap **Share → Add to Home Screen**. The unsigned `.ipa` is for people who already sideload; it is **untested on real hardware**. See [iPhone and iPad](#iphone-and-ipad) below. |

> [!NOTE]
> **macOS and iPhone/iPad app builds are not part of 1.2.0.** Those two files have to be
> built on a Mac, and no Mac was available for this release, so 1.2.0 has Android and web
> builds only. Neither platform has been dropped: `JellyfinMusic-1.1.0-macos.zip` and
> `JellyfinMusic-1.1.0-unsigned.ipa` from the
> [1.1.0 release](../../releases/tag/v1.1.0) are still the newest builds for them, and both
> return once a Mac is available again. In the meantime, a Mac, iPhone or iPad can run the
> 1.2.0 web app in a browser or from the Home Screen.

The 1.2.0 release also contains `JellyfinMusic-1.2.0-release.aab`, the Google Play upload
bundle — a phone cannot install it, so ignore it unless you are publishing the app — and
`SHA256SUMS.txt` if you want to check a download.

## Signing in

Sign in with your server address (for a home server that is usually something like
`http://192.168.1.20:8096`), your Jellyfin username and password, or use Quick Connect.
Type `demo` as the server to explore the app with a built-in sample library.

## What it does

- Browse your library by album, artist, song, playlist, genre and favourites, with
  Continue Listening, Recently Played and Recently Added on the Library screen
- Sort Songs by title, artist, album, date added or length, with an A–Z rail on long lists
- Search across everything, with genre tiles and your recent searches before you type; a
  search result has the full menu, so a song can be queued, downloaded or added to a
  playlist without opening its album first
- Favourite songs, albums and artists with a heart, see them all on a Favourites page, and
  optionally keep every favourite downloaded
- Make and edit playlists from anywhere: add or remove songs, drag to reorder, rename and
  delete. Changes appear immediately and are undone with a reason if the server refuses
- Select several songs on any track list and play next, queue, favourite, download, add to
  a playlist or remove them together
- Full-screen player with synced lyrics, an up-next queue you can reorder, shuffle, repeat,
  a sleep timer, and Create Station from a song, album or artist
- Gapless playback and optional crossfade
- Lock-screen / notification controls, headset buttons and media keys in the browser
- Download for offline listening — an album, a playlist, an artist, a genre, your
  favourites, a selection of songs, one song or the whole library. The queue can be paused,
  resumed, cancelled and retried, a progress pill sits above the mini player, and it picks
  itself back up after the app is closed. Large downloads tell you how many songs and
  roughly how much space first. Downloads are an app feature: the web version streams only,
  and the 1.1.0 macOS and iOS builds do not have this queue
- A Downloads page showing what is transferring, what is paused and why, what failed with a
  retry, and everything on the device, plus Remove All Downloads
- Play with no server at all: the app opens, browses and plays offline from what you have
  downloaded, resumes the song it was on at the second it stopped, keeps lyrics beside
  downloaded songs, and reports what you played back to the server when it returns. An
  Offline Mode switch keeps it on downloads by choice (app builds only — a browser always
  needs the server)
- On Android, keep downloads on an SD card or USB drive when the device has one
  (Settings → Storage)
- Play on other Jellyfin devices in your home
- Light and dark themes, tinted from the album you are playing
- On a desktop-sized window: sidebar navigation, a player bar and a Now Playing side panel,
  with keyboard control (Space to play or pause, Escape to close, the arrows to seek while
  the player is open, Cmd or Ctrl with the arrows to change track or volume, Cmd/Ctrl+F to
  search)

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

The newest Mac build is the 1.1.0 one, in the [1.1.0 release](../../releases/tag/v1.1.0). It
does not have the 1.2.0 downloads queue, playlist editing or favourites. To use those on a
Mac today, open the 1.2.0 web app in a browser.

## iPhone and iPad

The way to run Jellyfin Music on an iPhone or iPad today is the **web app**:
open the hosted web version in Safari, tap **Share → Add to Home Screen**, and
launch it from the Home Screen. It runs full screen with its own icon, keeps
you signed in, and shows Now Playing on the Lock Screen. The 1.2.0 web bundle is
in this release, so iPhone and iPad get 1.2.0 through the browser. Like every
browser version it streams only — no downloads and no offline mode.

### Sideloading the unsigned .ipa

An unsigned `JellyfinMusic-1.1.0-unsigned.ipa` is attached to the
[1.1.0 release](../../releases/tag/v1.1.0) for people who already sideload
apps; there is no 1.2.0 `.ipa`. Like the Mac build, it is a 1.1.0 app: it does
not have the 1.2.0 downloads queue, playlist editing or favourites. It
**cannot** be installed by opening it directly: iOS only runs signed apps, so
you sign it yourself with [AltStore](https://altstore.io) or
[Sideloadly](https://sideloadly.io), which use your own Apple ID and install it
over USB or Wi‑Fi. With a free Apple ID the signature lasts 7 days (those tools
re-sign it while your computer is reachable) and you may have three sideloaded
apps at a time; a paid Apple Developer account signs for a year.

> [!WARNING]
> **The iOS build has never run on a real iPhone or iPad.** Everything
> specific to real hardware — background audio, Lock Screen and Control Centre
> controls, the local-network permission prompt,
> audio interruptions from calls, Bluetooth and CarPlay — is unverified and may
> simply not work. The web app is the supported route on iOS; treat the `.ipa`
> as experimental.

## Downloads on an SD card (Android)

If your phone or tablet has an SD card or a USB drive, **Settings → Storage** lets you choose
where new downloads are saved (the option only appears when such storage exists). You can move
existing downloads to the new location; songs on a card that is out of the device show as
unavailable until you put it back, re-download them or remove them.

## Not there yet

- No "Download over Wi‑Fi only" switch. The queue does hold itself back when the server
  cannot be reached and while Offline Mode is on
- Casting reaches other Jellyfin sessions only; AirPlay and Bluetooth are handled by your
  device, outside the app
- No CarPlay or Android Auto browse tree
- No play counts, "Most Played" or home shelves shown in the app — plays are still reported
  to the server, and Recently Played comes from the server's own history
- The web version has no downloads and no offline mode: a browser has no file system to
  keep the music, covers and library snapshot in

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
