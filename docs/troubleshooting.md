# Troubleshooting

## Installing

**Windows: "Windows protected your PC"**
SmartScreen is cautious about installers it hasn't seen often. Click **More info → Run anyway**. To be sure the file is genuine, [verify its checksum](installation.md#verifying-a-download).

**Linux: AppImage won't start, mentions `libfuse.so.2`**
Install FUSE 2: `sudo apt install libfuse2` (Debian/Ubuntu), `sudo dnf install fuse-libs` (Fedora), `sudo pacman -S fuse2` (Arch). Or use the `.deb` if your distribution supports it.

**Linux: blank or white window**
Usually a GPU/compositor issue in WebKitGTK. Try launching with `WEBKIT_DISABLE_DMABUF_RENDERER=1`, and if that doesn't help, `WEBKIT_DISABLE_COMPOSITING_MODE=1`.

**macOS: keeps asking for keychain access**
Choose **Always Allow** when macOS asks whether Junction may use its keychain item. If you previously chose *Deny*, open Keychain Access, search for `be.tuntau.junction`, and delete the item — Junction creates a new one (you'll need to re-enter connection passwords).

## Connecting

See the table in [Connections → Troubleshooting](connections.md#troubleshooting). In short: check host and port, check whether the server allows your IP, and use an SSH tunnel for databases behind a firewall. **Test** in the connection editor reports the driver's exact error.

## Updating

**No update banner, but a new version is out**
Use **Settings → About → Check for updates**. If it reports an error, check that `junction.tuntau.com` is reachable from your network (corporate proxies sometimes block it). You can always install a new version over the old one from the [Releases page](https://github.com/tuntau-official/junction/releases) — your data is kept.

**"Your update coverage has ended"**
Pro Perpetual licenses include updates for a year at a time. Junction keeps working on your current version; an update extension unlocks newer ones. See [Plans & licensing](plans-and-licensing.md).

## Licensing

**Key won't activate**
Paste the whole key, starting with `JUNCTION-`, without extra spaces or line breaks. If it still fails, mail the key and the error to [sales@tuntau.com](mailto:sales@tuntau.com).

**"License couldn't be verified online for over 60 days"**
Junction checks your key with our server every few weeks. Connect to the internet (and make sure `junction.tuntau.com` isn't blocked by a proxy or firewall), then restart Junction — your plan comes back immediately.

**Lost your key**
It's in your account dashboard (**Settings → License → Manage billing**) and in the purchase email from `no-reply@junction.tuntau.com`.

## Starting fresh

To reset Junction completely, quit it and remove the data folder (see [Privacy & security](privacy-and-security.md#what-junction-stores-and-where)). This deletes your connections, saved queries and settings — your license key is in the purchase email if you need to re-activate.

## Still stuck?

- In the app: **Help → Report a Bug…** — includes the details we need, and you see everything before it's sent.
- [Open an issue](https://github.com/tuntau-official/junction/issues/new/choose) on GitHub.
- Email [hello@tuntau.com](mailto:hello@tuntau.com).
