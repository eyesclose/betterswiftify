<div align="center">

<img src="packaging/icons/swiftify-256.png" width="120" alt="betterswiftify icon">

# BetterSwiftify

**a spotify desktop player, the way i want to use it.**

material 3 expressive · cover-driven themes · personal dj mix · no electron

[![release](https://img.shields.io/github/v/release/eyesclose/betterswiftify?style=for-the-badge&color=6750a4&labelColor=1d1b20)](https://github.com/eyesclose/betterswiftify/releases/latest)
[![downloads](https://img.shields.io/github/downloads/eyesclose/betterswiftify/total?style=for-the-badge&color=6750a4&labelColor=1d1b20)](https://github.com/eyesclose/betterswiftify/releases)
[![build](https://img.shields.io/github/actions/workflow/status/eyesclose/betterswiftify/prebuilt.yml?branch=main&style=for-the-badge&label=build&labelColor=1d1b20)](https://github.com/eyesclose/betterswiftify/actions/workflows/prebuilt.yml)
[![license](https://img.shields.io/github/license/eyesclose/betterswiftify?style=for-the-badge&color=6750a4&labelColor=1d1b20)](LICENSE)

[![qt quick](https://img.shields.io/badge/Qt_Quick-6.10+-41cd52?style=for-the-badge&logo=qt&logoColor=white&labelColor=1d1b20)](https://www.qt.io)
[![rust core](https://img.shields.io/badge/core-rust-dea584?style=for-the-badge&logo=rust&logoColor=white&labelColor=1d1b20)](spotify-core)
[![english](https://img.shields.io/badge/ui-english_·_русский-6750a4?style=for-the-badge&labelColor=1d1b20)](#whats-different)

**[download](#install)** · **[first launch](#first-launch)** · **[good to know](#good-to-know)** · **[build from source](#build-from-source)** · **[upstream](https://github.com/swiftify-org/swiftify)**

<br>

<img src="docs/screenshots/showcase-home.png" alt="betterswiftify home with dj mix, pinned playlists and the current track" width="880">

</div>

<br>

this is my personal fork of [swiftify](https://github.com/swiftify-org/swiftify), not a separate project built from scratch. i keep what i use, add what i miss, and remove what feels like clutter to me. it follows my preferences, not a plan to be the right client for everyone.

the foundation is still c++ and qt quick, with a rust core built around [librespot](https://github.com/librespot-org/librespot). no electron, no bundled web browser.

<div align="center">
<table>
  <tr>
    <td width="50%"><img src="docs/screenshots/showcase-lyrics.png" alt="fullscreen player with synced lyrics"></td>
    <td width="50%"><img src="docs/screenshots/showcase-player.png" alt="fullscreen artwork and playback controls"></td>
  </tr>
  <tr>
    <td align="center"><sub>synced lyrics on a cover-colored background</sub></td>
    <td align="center"><sub>just the artwork, the track and the controls</sub></td>
  </tr>
</table>
</div>

## what's different

<table>
  <tr>
    <td width="33%" valign="top">

### 🧹 less clutter
local-file management, playlist-link collections and extra connect-device settings are gone. fullscreen visualizers are switched inside the fullscreen player.

</td>
    <td width="33%" valign="top">

### 🎨 cover-driven themes
the whole interface follows the current artwork. light and dark presets, including aurora and desert bloom, plus optional matugen.

</td>
    <td width="33%" valign="top">

### 🎧 personal dj mix
one button builds up to 40 tracks from your mixes, favourites, recent listening and top tracks, artists spaced apart.

</td>
  </tr>
  <tr>
    <td valign="top">

### 🔁 librespot or soloist
pick the player in settings → audio quality. librespot hands over to spotify's official soloist client if an audio key is refused.

</td>
    <td valign="top">

### 🌍 english and русский
live language switching, translated dialogs and errors, dates and numbers in the chosen language.

</td>
    <td valign="top">

### 🔐 less login friction
encrypted logins with automatic vault unlock on macos and windows, plus signed in-app updates.

</td>
  </tr>
</table>

and the rest of a proper player: search, saved songs, playlists, pinned playlists, synced lyrics, an equalizer, a sleep timer, media keys, optional discord activity and listening stats.

## install

> [!IMPORTANT]
> you need **spotify premium** and **your own spotify client id**, see [first launch](#first-launch). downloads come from this repository's releases; upstream downloads are a different build.

<div align="center">

[![macos apple silicon](https://img.shields.io/badge/macos-apple_silicon-6750a4?style=for-the-badge&logo=apple&logoColor=white&labelColor=1d1b20)](https://github.com/eyesclose/betterswiftify/releases/latest)
[![macos intel](https://img.shields.io/badge/macos-intel-6750a4?style=for-the-badge&logo=apple&logoColor=white&labelColor=1d1b20)](https://github.com/eyesclose/betterswiftify/releases/latest)
[![windows](https://img.shields.io/badge/windows-x64_setup-6750a4?style=for-the-badge&logo=windows&logoColor=white&labelColor=1d1b20)](https://github.com/eyesclose/betterswiftify/releases/latest)
[![linux](https://img.shields.io/badge/linux-x86__64_zip-6750a4?style=for-the-badge&logo=linux&logoColor=white&labelColor=1d1b20)](https://github.com/eyesclose/betterswiftify/releases/latest)

</div>

| platform | download | installation |
| --- | --- | --- |
| macos · apple silicon | `macos-aarch64.dmg` | open the image and drag the app to applications |
| macos · intel | `macos-x86_64.dmg` | same, but soloist is unavailable on intel macs |
| windows · x64 | `windows-x86_64-setup.exe` | run setup; it adds shortcuts and an uninstaller, no administrator access needed |
| linux · x64 | `linux-x86_64.zip` | extract it and run `./Swiftify/bin/swiftify` |

the filenames also include the version number. a published release can lag behind the code while builds finish.

> [!NOTE]
> macos builds are not notarized and windows builds are not authenticode-signed, so the os may ask you to approve the first launch. linux packages bundle qt but still need the host's audio and system libraries: alsa, pulseaudio or pipewire-pulse, glib and dbus.

the other zip files are portable builds and update payloads. `.json` and `.sig` files are update metadata, not installers. keep a portable installation's files together.

## first launch

you need a spotify premium account for librespot playback, and a client id from your own spotify developer app for the library, playlists and search.

1. open the [spotify developer dashboard](https://developer.spotify.com/dashboard) and create an app. select the web api if asked.
2. add this exact redirect uri in the app's settings:

   ```text
   http://127.0.0.1:8898/login
   ```

3. copy the client id into swiftify and choose **connect library**. the client secret is not needed.
4. choose **connect playback** and finish the spotify login in your browser.
5. pick something to play.

use the same spotify account for the library and playback if you want personalized mixes to match. the spotify api can restrict some playlists or library operations; swiftify cannot grant permissions that spotify does not provide.

### if librespot cannot play

you can also choose soloist yourself: **settings → audio quality → play music through → soloist**. the lossless section appears there once it is active.

some accounts, particularly newer ones, are refused the audio keys librespot needs. swiftify detects that refusal and switches to **[spotify soloist](https://developer.spotify.com/documentation/soloist)**. an ordinary network error or an unavailable track does not trigger the switch.

to set it up:

1. open **settings → account → spotify soloist** and choose **install soloist**.
2. create your own key in the [soloist dashboard](https://developer.spotify.com/dashboard/soloist).
3. paste the key into swiftify and press enter.
4. once, open the official spotify app on the same network and select the device named **swiftify**. this pairs soloist with your account.
5. return to swiftify and press play.

pairing is saved. you do not need to repeat it on every launch or open spotify every time you use swiftify. each user needs their own soloist key; none is included with this app.

soloist is downloaded directly from spotify, not bundled or redistributed. official builds exist for linux x86_64/arm, apple silicon macos and x86_64 windows. builds expire after 90 days; swiftify refreshes its managed download after 80 days and when an expired build exits.

manual installations also work: put the executable on your path, use `SWIFTIFY_SOLOIST` to point to it, or use [the shell installer](tools/install-soloist.sh) / [the powershell installer](tools/install-soloist.ps1). a key can also be supplied through `SOLOIST_API_KEY` or the `soloist/api-key` file in the system configuration directory.

## good to know

<details>
<summary><b>dj mix is not spotify ai dj</b></summary>
<br>

the button on home assembles a local queue using the music available to your account. it removes duplicate and unplayable tracks, avoids immediately replaying the current song, and tries to space artists apart. **new dj mix** builds another queue.

it is not spotify's ai dj algorithm, has no announcer, and does not create a playlist on your account. spotify does not expose an official api for controlling ai dj. if personalized playlists are unavailable, swiftify falls back to your library and listening history. a failed or cancelled request leaves your existing queue alone.

</details>

<details>
<summary><b>themes and fullscreen playback</b></summary>
<br>

choose **settings → appearance → colours → cover colors** to let the interface follow the playing cover. palettes are cached and calculated off the ui thread; they fade between tracks and fall back to the default palette when artwork is missing.

matugen is optional. it generates a material-style palette from an image, usually your wallpaper. swiftify can follow its json output; you do not need it to use the built-in themes.

the fullscreen player's sound panel has its own visualizer switch. the global visualizer setting still takes priority.

scrolling vertically over a playlist or genre shelf still moves the page. use a horizontal trackpad gesture, shift + mouse wheel, or the horizontal scrollbar to move through the shelf itself.

</details>

<details>
<summary><b>soloist audio and lossless</b></summary>
<br>

soloist supports lossless playback up to **24-bit / 44.1 khz** with premium, according to [spotify's documentation](https://github.com/spotify/soloist). availability also depends on the account and region. its current api cannot set or verify the delivered quality, so swiftify does not pretend that a local switch can enable it.

the lossless information section appears when the soloist backend is selected. the 96/160/320 kbit/s setting controls librespot, not soloist.

on macos and windows, soloist outputs directly to the system, outside the rust audio pipeline. rust-side equalizer, spectrum analysis, tempo and pitch processing do not apply to that output. linux with pipewire can route soloist through swiftify for the equalizer and visualizers; `SWIFTIFY_SOLOIST_ROUTE=off` disables that route. soloist playback also does not use swiftify's librespot crossfade.

</details>

<details>
<summary><b>saved logins</b></summary>
<br>

spotify logins stay in an encrypted vault outside the application directory. macos can remember its unlock password in keychain; windows uses user-scoped dpapi encryption. new installations create a random vault password automatically.

if you already have a password-protected vault, enter its old password **once** to migrate. subsequent launches unlock automatically when secure storage is available. linux keeps the manual password flow. a locked keychain, denied access or a changed macos signing identity can require manual unlock again.

reinstalling the app does not require deleting your data. see [vault storage and recovery](docs/credential-vault.md) before moving or resetting the credential files.

</details>

<details>
<summary><b>discord and listening stats</b></summary>
<br>

discord activity is optional and off by default. create an app in the [discord developer portal](https://discord.com/developers/applications), then paste its application id into **settings → account → discord rich presence**. no bot token is needed. discord's desktop app and activity-sharing permission must be enabled. this is rich presence, not spotify's linked-account activity or listen along.

the stats page can use local listening history or a public [stats.fm](https://stats.fm) profile. local history stays on your computer and can be exported as csv. its collection can be disabled in settings.

</details>

<details>
<summary><b>updates and restarting</b></summary>
<br>

release builds can check for updates and install them while nothing is playing. both automatic checking and installation can be disabled under **settings → about → updates**. system-package installations should use their package manager instead.

the player remembers the last track, position and queue, but restores them **paused**. opening the app should not start music by itself.

</details>

## build from source

you need git, a c++20 compiler, **qt 6.10 or newer**, qcoro for qt 6, cmake 3.24+, ninja and a current stable rust toolchain from [rustup](https://rustup.rs).

qt needs the base, declarative, shader tools and websockets modules. linux also needs the pulse/alsa and openssl development packages. the first configure downloads corrosion and the interface/icon fonts, with pinned versions or hashes.

```sh
git clone https://github.com/eyesclose/betterswiftify.git
cd betterswiftify
```

<details>
<summary>macos</summary>

install apple's command line tools and the dependencies through homebrew. install rust separately if it is not already available.

```sh
xcode-select --install
brew install cmake ninja qtbase qtdeclarative qtshadertools qtwebsockets qcoro6

cmake -S . -B build -G Ninja -DCMAKE_BUILD_TYPE=Release -DBUILD_TESTING=OFF
cmake --build build --parallel
open build/swiftify.app
```

this is a local, ad-hoc-signed build. for a self-contained package with qt bundled, use [the macos release script](tools/build-macos-portable.sh) with `QT_ROOT_DIR` pointing to your qt kit. it produces both a disk image and the updater zip.

</details>

<details>
<summary>linux</summary>

for arch-based systems:

```sh
sudo pacman -S --needed git cmake ninja rust pkgconf \
  qt6-base qt6-declarative qt6-shadertools qt6-wayland qt6-websockets \
  qcoro libpulse alsa-lib openssl

cmake -S . -B build -G Ninja -DCMAKE_BUILD_TYPE=Release \
  -DBUILD_TESTING=OFF -DCMAKE_INSTALL_PREFIX="$HOME/.local"
cmake --build build --parallel
cmake --install build
```

make sure `~/.local/bin` is on your path. a [pkgbuild](packaging/arch/PKGBUILD) is also included if you prefer a package-managed installation.

on debian or ubuntu, the [debian build script](tools/build-debian.sh) can install distro dependencies:

```sh
./tools/build-debian.sh --install-deps
```

install rust, cmake and ninja first. the script has compatibility patches for older system qt versions and modifies the checkout; a qt 6.10+ build remains the preferred configuration.

linux integration includes mpris/media keys, the system tray and pausing before sleep. `-DSWIFTIFY_DESKTOP_INTEGRATION=OFF` disables the pulse/desktop integration pieces for development builds.

</details>

<details>
<summary>windows</summary>

install git, cmake, ninja, rust and a qt kit with shader tools and websockets. the recommended combination is **visual studio 2022** with the desktop c++ workload and **qt 6.10.3 msvc2022_64**, matching the release workflow.

from powershell in the repository root:

```powershell
.\tools\build-windows.ps1 -QtPath 'C:\Qt\6.10.3\msvc2022_64'
```

the script builds dependencies, installs the app and deploys the required qt/runtime libraries. its default destination is `%LOCALAPPDATA%\Programs\Swiftify`:

```powershell
& "$env:LOCALAPPDATA\Programs\Swiftify\bin\swiftify.exe"
```

matching mingw kits are supported through `-MingwPath`, but older mingw headers lack windows media controls. use msvc if you want the complete feature set. if powershell blocks the script, a process-local override is available:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\tools\build-windows.ps1
```

the setup executable is built with inno setup 6 through [the installer packager](tools/package-installer.py). the github actions workflow handles that step for releases.

</details>

### run the tests

for a manual cmake build, configure with testing enabled, then build and run:

```sh
cmake -S . -B build -DBUILD_TESTING=ON
cmake --build build --parallel
ctest --test-dir build --output-on-failure
python3 tests/check_translations.py .
python3 tests/check_update_tools.py
```

## command line

only one instance runs at a time. launching another copy passes the command to the running player, which makes these useful for desktop shortcuts:

| option | action |
| --- | --- |
| `--immersive` | open the fullscreen player |
| `--play-pause` | toggle playback |
| `--next` | next track |
| `--previous` | previous track |
| `--stats` | open listening stats |

## troubleshooting

- **login does not return to the app:** check the redirect uri above and make sure port `8898` is not occupied.
- **“the update download url was refused” after a repository rename:** install the current version from [releases](https://github.com/eyesclose/betterswiftify/releases/latest) once. older builds cannot follow the renamed api address to fetch their own fix. keep the data directory; a manual app replacement does not require deleting your logins or settings.
- **spotify refuses the audio key:** configure soloist rather than repeatedly reconnecting librespot.
- **soloist is not listed in spotify:** check that both devices are on the same network and that a firewall is not blocking discovery. pairing from the desktop app on the same computer can help.
- **the vault asks again after migration:** secure storage was unavailable or access was denied. on macos, changing the build's signing identity can also break keychain trust.
- **personalized playlists are missing:** that feed uses an internal spotify interface and can change or be unavailable for an account. the ordinary library and dj mix's library fallback do not require it.

## about this fork

report fork-specific problems in [this repository's issues](https://github.com/eyesclose/betterswiftify/issues), with your os, app version and playback backend. leave api keys and tokens out of logs and screenshots.

this is a personal fork, so features and fixes follow what i use. if you want to propose a larger change, open an issue before writing it. upstream remains the source of the original player and most of its interface; please don't send fork-specific bug reports there.

thanks to [the original swiftify project](https://github.com/swiftify-org/swiftify), [librespot](https://github.com/librespot-org/librespot), [spotify soloist](https://developer.spotify.com/documentation/soloist) and the libraries behind the app. the material 3 expressive direction comes from upstream, with inspiration from [end-4](https://github.com/end-4).

## license

gpl v3 or later, see [LICENSE](LICENSE). betterswiftify is a fork of [swiftify](https://github.com/swiftify-org/swiftify) and keeps its license.
