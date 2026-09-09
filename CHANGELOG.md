# Changelog

## 1.2.0 (alpha) — 2026-09-09

Still pre-release alpha software: unfinished, under active development, some
features may not work as expected yet.

Downloads, playlists and offline listening are the point of this release.

**Downloads are a queue now.** Download an album, a playlist, an artist, a
genre, your favourites, a selection of songs, one song, or the whole library
— the button is wherever a set of songs is. Cancel a download mid-transfer,
pause and resume the queue, retry what failed. One song that will not download
no longer abandons the album around it; the item is marked as having songs
missing and offers to fetch just those. A song that belongs to two downloaded
items is fetched once and survives removing either. The queue picks itself
back up after the app is killed, and a progress pill above the mini player
says how far along it is. Before anything large starts, the app says how many
songs and roughly how much space, and says plainly when it will not fit.

**A Downloads page worth opening**: what is transferring with a cancel, what
is paused and why, what failed with a retry, and everything on the device.
Plus keep-an-item-updated, reclaim unused files, and Remove All Downloads.

**Playlists can be edited.** Make one from anywhere. Add or remove songs one
at a time, or select several and act on the lot. Drag to reorder, rename,
delete. Every change shows immediately and is rolled back with a reason if the
server refuses it.

**Favourites**: a heart on songs, albums and artists, a Favourites page, and
an option to keep every favourite downloaded automatically.

**Offline is a first-class mode.** The app opens, browses and plays with no
server at all — the last catalogue it saw is kept on disk, downloaded covers
render from disk, nothing is ever streamed while the server is out of reach,
and songs you have not downloaded are skipped rather than throwing an error.
It even opens on the song it was last playing, at the second it stopped, with
no server to ask. Lyrics fetched while online are kept beside the songs they
belong to, so a downloaded album still sings along on a plane. Anything you
play offline is reported to the server when it comes back, so play counts and
resume positions are not lost. An Offline Mode switch stays on downloads by
choice, and a quiet bar says which of the two is happening.

**Everyday things**: sort Songs by title, artist, album, date added or length;
an A–Z rail on long lists; multi-select on any track list; Create Station from
a song, album or artist; Recently Played on the Library screen; recent
searches; save the queue as a playlist or clear it; disc headings on
multi-disc albums; a downloaded mark on every song row; a full menu on every
search result, so a song found by searching can be queued, downloaded or put
in a playlist without opening its album first; and one banner that confirms
what you just did instead of leaving it silent.

Fixes, all of them reproducible before this release:

- Play and Shuffle on the Songs page acted on the couple of hundred songs
  scrolled past rather than the library, and tapping a row stopped playback
  dead at the end of what had loaded
- Pressing the seek bar and dragging the player away froze the playhead for
  the rest of the session
- Clear in the queue brought every cleared song back when shuffle was
  switched off
- The Now Playing sheet always claimed to be playing from an album
- The volume slider in the Now Playing sheet snapped back when released
- A failed download hid every confirmation for the next six seconds
- Bare arrow keys changed the volume instead of scrolling a list, and nothing
  in the app was reachable by keyboard
- Pull-to-refresh on the Albums grid replaced the grid with a spinner
- A playlist made on another device never appeared until sign-out
- The lock screen fetched artwork over the network for downloaded albums and
  claimed a full buffer from the first frame
- Right-clicking an album tile in a grid did nothing
- Typing in Search threw the caret to the end of the field
- Trying to delete a playlist you do not own signed you out of the app

Found and fixed by reading this release back before it shipped:

- Removing several songs at once from a track list deleted nothing and said
  it had; removing songs from a playlist could delete the wrong ones, because
  the ids a playlist row carries change every time the list is read
- A download that hit a moment's trouble spent all three of its attempts at
  once, so a one-second hiccup failed the song for good and five of those
  paused the whole queue
- "Not enough space" could not be recovered from: removing every download and
  pressing Resume paused on storage again with nothing on the device
- An item that skipped songs said "Downloaded", and asking for it again did
  nothing
- Music played offline was only ever reported to the server if the server
  came back during the same run of the app
- Picking a song nothing can play left the previous one audible under the new
  one's title, and a stream that failed never told the app the server was gone
- Cached covers were never deleted, never counted in Storage Used, and
  survived Remove All Downloads
- The offline library, downloads and pending plays were keyed by server
  alone, so two accounts on one device shared them
- The multi-select bar could not be used at all on a phone: every verb sat
  behind the tab bar and the mini player
- Starting or finishing a download threw away every open page — scroll
  positions, selections, a playlist's Edit mode
- "Keep Favourites Downloaded" stopped following as soon as you had
  downloaded Favourites by hand, and switching it off deleted every one of
  them without asking
- Favourites disappeared from the Library screen and the sidebar whenever the
  server did — the one list a phone full of downloads is for
- Offline Mode was offered in the sample library and in the browser, where it
  could only empty the app
- Opening a Genre or Artist page fetched every song in it to fill a menu, and
  every cover on screen checked the disk on every frame

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
