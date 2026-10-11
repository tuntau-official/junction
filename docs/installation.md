# Installation

Download the installer for your platform from the [latest release](https://github.com/tuntau-official/junction/releases/latest). The same files are also available from [junction.tuntau.com](https://junction.tuntau.com).

| Platform | File | Architecture |
|---|---|---|
| macOS | `Junction_<version>_universal.dmg` | Apple Silicon and Intel (one universal app) |
| Windows 10 / 11 | `Junction_<version>_x64-setup.exe` | x64 |
| Debian, Ubuntu, Mint, Pop!_OS… | `Junction_<version>_amd64.deb` | x86-64 |
| Any other Linux | `Junction_<version>_amd64.AppImage` | x86-64 |

## macOS

1. Open the `.dmg`.
2. Drag **Junction** onto the **Applications** folder.
3. Launch Junction from Applications or Spotlight.

The app is signed with an Apple Developer ID and notarized by Apple, so it opens without warnings. The first time Junction stores a connection password, macOS asks whether Junction may use the keychain — choose **Always Allow**.

## Windows

1. Run `Junction_<version>_x64-setup.exe`.
2. Follow the installer. Junction installs for the current user; no administrator rights are needed.
3. Launch Junction from the Start menu.

**"Windows protected your PC"?** Microsoft SmartScreen warns about installers it hasn't seen often yet. Click **More info → Run anyway**. You can verify the file first — see [Verifying a download](#verifying-a-download).

Junction uses Microsoft Edge WebView2, which is part of Windows 10 and 11. On the rare system without it, the installer downloads it for you.

## Linux

### Debian / Ubuntu (`.deb`) — recommended

```bash
sudo apt install ./Junction_<version>_amd64.deb
```

`apt` pulls in the required libraries (WebKitGTK 4.1 and friends) automatically. Junction appears in your application menu.

### AppImage — any distribution

```bash
chmod +x Junction_<version>_amd64.AppImage
./Junction_<version>_amd64.AppImage
```

AppImages need FUSE 2. If it won't start with an error about `libfuse.so.2`, install it (`sudo apt install libfuse2`, `sudo dnf install fuse-libs`, `sudo pacman -S fuse2`).

## Updates

Junction checks for updates in the background and shows a banner when one is ready. Click it to install; Junction restarts on the new version. You can also check manually in **Settings → About → Check for updates**.

Every update is signed, and Junction refuses to install anything whose signature doesn't match — an update can't be tampered with in transit.

- **macOS, Windows, `.deb`, AppImage** — all update in place.
- The **What's new** dialog after an update lists the changes; you can reopen it from **Settings → About**. Full notes for every version are on the [Releases page](https://github.com/tuntau-official/junction/releases).

> **Pro Perpetual licenses** include a year of updates at a time. When that window ends, Junction keeps working on the version you have; the update banner points you to an update extension. See [Plans & licensing](plans-and-licensing.md).

## Verifying a download

Each release includes `SHA256SUMS.txt`. Download it next to the installer, then:

```bash
# macOS / Linux
shasum -a 256 -c SHA256SUMS.txt --ignore-missing
```

```powershell
# Windows (PowerShell) — compare the output with the line in SHA256SUMS.txt
Get-FileHash .\Junction_<version>_x64-setup.exe -Algorithm SHA256
```

## Uninstalling

| Platform | Remove the app | Remove your data (optional) |
|---|---|---|
| macOS | Drag `Junction.app` from Applications to the Trash | `~/Library/Application Support/be.tuntau.junction/` and the keychain item `be.tuntau.junction` |
| Windows | Settings → Apps → Junction → Uninstall | `%APPDATA%\be.tuntau.junction\` |
| Linux (`.deb`) | `sudo apt remove junction` | `~/.local/share/be.tuntau.junction/` |
| Linux (AppImage) | Delete the `.AppImage` file | `~/.local/share/be.tuntau.junction/` |

Your data folder holds connections (with encrypted credentials), saved queries, settings and your license. Keep it if you plan to reinstall.
