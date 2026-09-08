# Jellyfin Music — Privacy Policy

**Effective date:** September 8, 2026
**Developer:** Ashton Cable · [ashtoncable.ca](https://ashtoncable.ca) · [ashton@ashtoncable.ca](mailto:ashton@ashtoncable.ca)

## The short version

- Jellyfin Music does **not** collect, store, sell or share any personal data. There are no analytics, no advertising, no tracking and no developer accounts.
- The app is only a **client**. Your music, listening history and account belong to the Jellyfin server you connect to, which you (or someone you trust) run yourself. The developer has no access to that server or anything on it.
- Everything the app keeps is stored **on your device** and can be removed by signing out, deleting downloads or uninstalling the app.

## What the app stores on your device

To work as a music player the app keeps the following on your device only:

- **Server connection details** – the address of your Jellyfin server, your username, and the session token your server issues when you sign in, so you stay signed in. Your password is used once to sign in and is not stored.
- **A device identifier** – a random string the app generates the first time it runs. Jellyfin requires clients to identify themselves with a device ID; it is not derived from your hardware and is never sent anywhere but your own server.
- **Preferences** – appearance, playback and download settings, and whether you have seen the welcome tour.
- **Downloads** – music files and cover images you choose to download for offline listening.

On Android, iOS and macOS this data lives in the app's private storage. On the web it lives in your browser's local storage for the site that hosts the app. Signing out removes the session token; deleting a download removes its files; uninstalling the app (or clearing site data in the browser) removes everything.

## What the app sends to your Jellyfin server

Jellyfin Music talks only to the server address you enter. Like any Jellyfin client it sends your sign-in details, requests for your library, search terms, the tracks you play and how far you have listened (Jellyfin's playback reporting, which powers "resume" and play counts on your server), download requests, and, if you use the Play On feature, remote-control commands for other Jellyfin devices on your account.

This traffic goes directly between your device and your server; the developer never sees it. Whoever operates the server controls that data. If the server is not your own, refer to its operator's privacy practices.

## Optional third-party service: lyrics

When your server has no lyrics for a song and **Online Lyrics** is switched on (it is on by default), the app asks [LRCLIB](https://lrclib.net), a free community lyrics database, for lyrics. Only the song's title, artist, album name and length are sent — no account details, identifiers or listening history. As with any internet request, LRCLIB's servers can see your IP address. You can turn this off at any time in **Settings → Playback → Online Lyrics**, after which the app makes no requests to anyone other than your Jellyfin server.

The built-in **demo library** (reached by entering `demo` as the server) loads sample cover images from the placeholder image service picsum.photos. No personal data is sent with those requests.

## Permissions

The app asks only for what playback needs: network access (to reach your server), the ability to keep playing in the background with a media notification / lock-screen controls, and permission to keep the device awake while playing. It does not request access to your location, contacts, camera, microphone, photos or files outside its own storage.

## Children

Jellyfin Music is not directed at children under 13 and, as described above, does not collect personal information from anyone.

## Security

Session tokens are kept in the app's private storage. Connections to your server use HTTPS when your server is configured for it; the developer recommends HTTPS whenever a server is reachable from outside your home network. Because no data is collected by the developer, there is no developer-side data to breach.

## Your choices and rights

Because the developer holds no data about you, there is nothing for the developer to access, correct or delete. Data held by your Jellyfin server is managed through the server itself. On your device you can sign out, delete downloads or uninstall the app at any time.

## Changes to this policy

If the app's behaviour changes in a way that affects privacy, this document will be updated and the effective date revised. The current version is always published alongside the app's releases.

## Contact

Questions about this policy or anything else important: email [ashton@ashtoncable.ca](mailto:ashton@ashtoncable.ca), visit [ashtoncable.ca](https://ashtoncable.ca), or open an issue on the [jellyfin-music-releases](https://github.com/AshtonCable/jellyfin-music-releases) repository. The current version of this policy is published at <https://ashtoncable.github.io/jellyfin-music-releases/privacy-policy.html>.

---

### Notes for app-store forms

- **Google Play Data safety:** the developer collects no user data and shares no user data. Sign-in credentials and the session token are stored on-device only and are sent solely to the user's own server. The optional lyrics lookup sends non-personal song metadata (title, artist, album, duration) to LRCLIB and can be disabled by the user.
- **Apple App Privacy:** "Data Not Collected". The app contains no third-party analytics or advertising SDKs and does not track users.
- This document describes the app's behaviour as built; it is not legal advice.
