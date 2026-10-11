# Privacy & security

Junction is a local application. Your databases, queries and results stay on your machine. There is no Junction account and no usage telemetry.

## What Junction stores, and where

Everything lives in your local data folder:

| OS | Folder |
|---|---|
| macOS | `~/Library/Application Support/be.tuntau.junction/` |
| Windows | `%APPDATA%\be.tuntau.junction\` |
| Linux | `~/.local/share/be.tuntau.junction/` |

It contains your connections, saved queries and blueprints, settings, and license key.

**Credentials** (database passwords, SSH passwords, keys and passphrases) are encrypted with AES-256-GCM in `secrets.enc`. The key that unlocks them is random, created on first run, and kept in your OS keychain — so copying the data folder to another machine does not copy usable credentials.

## What leaves your machine

Only these, and only as described:

| What | Sent to | When |
|---|---|---|
| Database traffic | Your database servers | When you connect and run queries |
| Update check | `junction.tuntau.com` | In the background, to see if a new version exists. Sends your platform and current version. |
| License check-in | `junction.tuntau.com` | Pro/Team only, every 2–4 weeks. Sends your license key and a random install ID — nothing about your databases. |
| AI assistant | **The endpoint you configured** | Only when you use the assistant. See [AI assistant](ai-assistant.md#what-leaves-your-machine). |
| Crash & bug reports | `junction.tuntau.com` | **Only when you click Send.** See below. |
| Links you click | Your browser | Buying a plan, opening the dashboard, the website |

License keys are verified offline with a cryptographic signature, so Junction works without internet. Every few weeks it briefly checks the key with our server, so revoked or shared keys eventually stop working and the 5-devices-per-seat limit holds. If a check can't get through, nothing changes for 60 days.

### Crash and bug reports

If Junction crashes, it writes a report to disk. On next launch it shows you **exactly** what would be sent — the error, a stack trace, app version and OS — and sends it only if you agree. Reports older than two weeks are discarded unsent.

**Help → Report a Bug…** works the same way, with your own description and an optional screenshot. **Redact screenshots** (Settings, on by default) blanks out table values before a screenshot is attached, so customer data doesn't end up in a bug report.

Reports go to Tuntau's own server — no third-party error tracker.

## Safety rails

- **Read-only connections** refuse every write, from every part of the app.
- **Dangerous-action confirmation** before `DROP`, `TRUNCATE` and unfiltered `UPDATE`/`DELETE`.
- **Staged edits** — table edits are only written when you commit them.
- The **AI assistant** asks before every write; the **MCP server** is read-only and bound to `127.0.0.1` with a per-session token.
- **Signed updates** — Junction verifies each update's signature and refuses tampered packages. macOS builds are signed and notarized by Apple.

## Reporting a vulnerability

Please **don't** open a public issue. See [SECURITY.md](../SECURITY.md).
