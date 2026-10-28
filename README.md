# ADVA MP Media Player

**English · [Русский](README.ru.md)**

ADVA Media Player is a Windows desktop music player built with Electron. It combines local audio playback with online music catalog integrations, a built-in equalizer, synchronized lyrics/subtitles, and a multilingual interface.

> **Project status:** This is an independent personal project. Updates may be irregular, and online integrations can stop working when third-party services change. Some UI issues and missing artwork may remain.

## Features

- **Local audio playback:** open MP3, WAV, OGG, FLAC, M4A, and AAC files.
- **Online music catalog:** integrations for YouTube Music, Zvuk, and Muzofond search.
- **Lyrics and subtitles:** currently supported in the integrated YouTube Music and Zvuk flows; availability depends on whether the provider supplies lyrics for a track.
- **Equalizer and playback controls:** volume, bass-related options, audio modes, shuffle, and repeat controls.
- **Library and local profile:** keep app settings and library data on the computer.
- **Themes and localization:** dark, black, and light themes. English is the default interface language; Russian localization is included. Japanese UI strings are also present in the current source, but behavior may vary between builds.

## Getting started

### For listeners

1. Open this repository's **Releases** page.
2. Download the Windows build that matches your needs. Use the **Setup** build for installation or **Portable** for a standalone portable package.
3. Launch ADVA Media Player and complete the initial local-profile and language setup.
4. Open **Music Catalog**, choose a provider, and search for a track or artist. Use the local-file command to play audio stored on your computer.

The main build on Electron 28. A separate build on the old Electron branch can be published separately. Use it only if it is clearly available in Releases and has been tested on your system.

### Connecting Zvuk

1. Open **Music Catalog → Zvuk → Connect account**.
2. Open the official Zvuk sign-in page from the connection window and sign in there.
3. Keep the connection window open; return to ADVA and click **“I signed in — connect account”**.
4. If connection succeeds, search for music in Zvuk.

The app is designed to read the service token only after the user explicitly completes the connection step. It does not intentionally save the account password. When Electron's OS-backed `safeStorage` is available, the token is encrypted before it is written to local app data. A token is still sensitive information: do not share it or your application-data folder. The integration does not bypass account, subscription, track-availability, regional, or rights-holder restrictions.

**YouTube Music:** a Google sign-in is not required by the current integration. Available tracks and playback can still vary by country, network, and changes to the third-party service.

## What the project uses

- **Electron** — desktop application runtime (Chromium + Node.js).
- **HTML, CSS, and JavaScript** — application interface.
- **`locales.js`** — interface strings and translations.
- **`sub.js`** — lyrics/subtitle support logic.
- **Python bridge executables** — separate helper processes for online music services.
- **`ytmusicapi` and `yt-dlp`** — used by the YouTube Music bridge.
- **`zvuk-music`** — used by the Zvuk bridge.
- **Electron `safeStorage`** — encrypts the stored Zvuk token when OS-backed encryption is available.

## Known limitations

- Online services may change their APIs, authentication flow, streaming behavior, or artwork URLs without notice.
- Track availability, full-length playback, and quality depend on each provider, the user's account, region, subscription, and rights-holder settings.
- Synchronized lyrics/subtitles are not available for every track and are currently integrated only with YouTube Music and Zvuk.
- Some icons or cover images may fail to load. Fixes and new releases are not guaranteed on a fixed schedule.
- The Windows 7 branch, if offered, uses an older Electron version

## Privacy and safety notes

- The app's local profile, settings, and library data are kept in the user's application-data area on the computer.
- Zvuk authentication tokens are sensitive. Keep the device account protected and do not publish logs or local data files that might contain session information.
- Use the online integrations in accordance with the relevant services' terms and local law.
- ADVA Media Player is an independent project and is not affiliated with Google, YouTube, Zvuk, Muzofond, or SberBank.
