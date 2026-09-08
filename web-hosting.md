# Hosting the web app

Jellyfin Music runs in any modern browser and can be installed like an app from Safari on iPhone and iPad, from Chrome or Edge on Android and desktop, and from Safari on the Mac. This guide covers building the bundle and putting it on ordinary shared web hosting managed with DirectAdmin (cPanel is the same idea).

## 1. Decide where it will live

The bundle is built for one exact location, its *base href*:

| You will open it at | Build with | Upload into |
|---|---|---|
| `https://music.example.com/` (subdomain) | `tool/build_web.sh /` | the subdomain's document root |
| `https://example.com/` (whole domain) | `tool/build_web.sh /` | `public_html/` |
| `https://example.com/music/` (folder) | `tool/build_web.sh /music/` | `public_html/music/` |

A bundle built for `/` does not work from `/music/` and vice versa: the page would look for `main.dart.js` in the wrong place and stay on the loading screen. A subdomain is the tidiest choice. Note that DirectAdmin creates subdomains as folders under `public_html/<name>/`, so the same files are also reachable at `https://example.com/<name>/` — only use the subdomain address, the other one has the wrong base href.

## 2. Build

```bash
tool/build_web.sh /           # or: tool/build_web.sh /music/
# → build/jellyfin-music-web.zip
```

The zip contains the site as it must appear on the server, including the hidden `.htaccess` (Apache settings) and `sw.js` (the offline cache). Ready-made zips for the root location are attached to each release of the public releases repository; anyone needing a folder location builds their own with the command above.

## 3. Upload with DirectAdmin

1. Sign in to DirectAdmin → **File Manager**.
2. Open the target folder (`domains/example.com/public_html`, or the subdomain / sub-folder from step 1). Create the sub-folder first if needed.
3. **Upload** `jellyfin-music-web.zip`, then use **Extract** on it (right-click or the ⋯ menu). Confirm that `index.html`, `main.dart.js`, `canvaskit/`, `.htaccess` and `sw.js` are now in that folder — turn on *Show hidden files* to see `.htaccess`.
4. Delete the zip.

FTP/SFTP works the same: unzip locally and upload the *contents* of `build/web` (hidden files included) into the folder.

Updating: build again, upload and extract over the old files (choose *overwrite*). Because `sw.js` changes with every build, installed apps pick the new version up on their next launch and switch to it the launch after that.

## 4. HTTPS (required)

Installable web apps, background caching and lock-screen controls only work on `https://`. In DirectAdmin: **Account Manager → SSL Certificates → Get automatic certificate from ACME Provider** (Let's Encrypt), tick the domain and the subdomain (or the wildcard), **Save**. Then **Domain Setup → your domain → Force SSL with https redirect** (the `.htaccess` also redirects to https as a fallback).

The Jellyfin server must be reachable over HTTPS too — see *Caveats*.

## 5. Check it works

- Open the address in a normal tab. The purple-to-blue loading screen should hand over to the app within a few seconds. If it stays on the loading screen, the base href does not match the folder (step 1).
- Headers and types (terminal, replace the host):
  ```bash
  curl -sI https://music.example.com/canvaskit/canvaskit.wasm | grep -i 'content-type'   # application/wasm
  curl -sI https://music.example.com/index.html | grep -i 'cache-control'                 # no-cache, no-store…
  curl -sI http://music.example.com/ | grep -i '^location'                                 # https://… redirect
  ```
- Service worker: Chrome/Edge → DevTools → **Application → Service Workers** shows `sw.js` as *activated*, and **Cache Storage** contains one `jellyfin-music-<build>` entry. Safari on the Mac → **Develop → Service Workers**. Or in the console: `navigator.serviceWorker.getRegistration().then(r => console.log(r && r.active && r.active.scriptURL))`.
- Installability: Chrome → DevTools → Application → **Manifest** shows the name, icons and no warnings; the address bar offers *Install*.
- Offline shell: switch off the network and reload — the sign-in page should still appear (the library itself needs the server).

## 6. Installing on iPhone and iPad

1. Open the address in **Safari** (Chrome, Edge and Firefox on iOS 16.4 or later can do this too).
2. Tap the **Share** button, then **Add to Home Screen**, then **Add**.
3. Open **Jellyfin Music** from the Home Screen. It runs full-screen with its own icon, keeps you signed in, and shows Now Playing on the Lock Screen and in Control Center.

On Android, Chrome shows an *Install* banner or **⋮ → Add to Home screen / Install app**. On the desktop, Chrome and Edge show an install icon in the address bar; Safari on macOS Sonoma has **File → Add to Dock**.

## Caveats

- **Your Jellyfin server must use HTTPS.** A page served over HTTPS is not allowed by browsers to talk to `http://` addresses. Give Jellyfin a certificate (Dashboard → Networking), put it behind a reverse proxy with one (Caddy, nginx, Traefik), or use a tunnel. Self-signed certificates must be trusted on each device first. Jellyfin allows cross-origin requests by default (Dashboard → Networking → CORS); a reverse proxy must pass those headers through.
- **Background audio on iPhone.** In the installed app, music keeps playing when the screen locks or you switch apps, with Lock Screen / Control Center controls (title, artwork, play/pause, next/previous, seek). iOS may still suspend the app after a long pause or under memory pressure; reopening it resumes. Crossfade timing can be less precise while the app is in the background.
- **No downloads in the browser.** The web version streams only; browsers cannot reliably keep gigabytes of audio. Use the Android or macOS app to listen offline.
- **Storage.** Your sign-in and settings are kept in the browser's storage for the site. Safari removes site data for pages that have not been opened in a week, but not for apps added to the Home Screen.
- **Fonts.** Text in scripts the bundled fonts do not cover (for example Japanese or emoji in a title) is rendered with fallback fonts that the browser downloads from Google Fonts on demand.
- **Headers to avoid.** Do not add `Cross-Origin-Opener-Policy` / `Cross-Origin-Embedder-Policy` headers: they block cover art and audio from your Jellyfin server.

Questions or problems: ashton@ashtoncable.ca
