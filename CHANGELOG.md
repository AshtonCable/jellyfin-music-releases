# Changelog

## 1.1.0 (alpha) — 2026-09-08

Still pre-release alpha software: unfinished, under active development, some
features may not work as expected yet.

- Smoother animations and much lower CPU and GPU use on desktop and web: bars
  and panels on wide layouts are painted opaque instead of live-blurred, and
  animations stop when nothing on screen is changing
- Android: choose where downloads are stored — internal storage, an SD card or
  a USB drive (Settings → Storage, shown only when the device has such
  storage). Existing downloads can be moved; songs on a card that is out of
  the device are marked unavailable and can be re-downloaded or removed
- Installable web app: add it to the Home Screen from Safari on iPhone and
  iPad or install it from Chrome and Edge, with an offline app shell. New
  hosting kit: `tool/build_web.sh`, an Apache `.htaccess` and
  `docs/web-hosting.md`. The web version streams only; downloads stay in the
  Android and macOS apps
- Clear loading, empty and error states everywhere, with a Retry button
  instead of a blank page or a false "nothing here", and pull-to-refresh on
  the library lists
- Keyboard control on desktop and in the browser: Space to play or pause,
  Escape to close, arrows to seek and change the volume, Cmd or Ctrl with the
  arrows to change track, Cmd or Ctrl+F to search
- Long press or right click a song for Play Next, Add to Queue, Go to Album
  and Go to Artist; a sleep timer; and removing a download now asks first
- Screen-reader labels and larger touch targets on the player controls,
  readable tab labels, and support for large system text
- Signing out asks for confirmation, and an expired session returns you to
  sign-in with an explanation instead of a wrong password message
- Downloaded music can be browsed and played with the server unreachable
- Settings → About: Support email, Privacy Policy and Check for Updates rows
- macOS: the download zip now includes "READ ME FIRST - Opening on macOS.txt"
  with the first-launch steps for macOS 15 and 26 (System Settings → Privacy
  & Security → Open Anyway), replacing the outdated right-click → Open advice
- iOS: build tooling for an unsigned .ipa (`tool/build_ios_unsigned.sh`),
  a branded launch screen and the local-network permission text. Untested on
  real hardware (Simulator only), so iOS stays experimental and the web app
  is the supported route on iPhone and iPad
- Privacy policy: notes on the web version's fallback fonts, downloads kept
  on removable storage, and the developer contact for store listings

## 1.0.0 (alpha) — 2026-09-08

First public pre-release. Alpha quality: unfinished, under active development,
some features may not work as expected yet.

- Splash screen and first-run tour, sign-in with Quick Connect
- Library, Albums, Artists, Songs, Playlists, Genres, Downloads, search
- Now Playing with synced/full lyrics (server or LRCLIB), reorderable queue, casting
- Gapless playback and optional crossfade
- Media notification / lock-screen controls
- Offline downloads on Android and macOS
- Desktop layout with sidebar, player bar and Now Playing panel
- Light and dark themes
