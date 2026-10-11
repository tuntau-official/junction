# Connections

A connection is how Junction reaches one database server (or, for SQLite, one file). Junction's drivers are built into the app — there is nothing extra to install, and `localhost` means *your* machine.

## Supported engines

| Engine | Default port | Notes |
|---|---|---|
| 🐘 PostgreSQL | 5432 | Schemas appear in the scope picker |
| 🐬 MySQL / MariaDB | 3306 | Cancelling a running query sends a real `KILL QUERY`, so a stuck query actually stops |
| 📦 SQLite | — | Pick a file; Junction can also create a new one |
| 🟥 SQL Server | 1433 | |
| 🍃 MongoDB | 27017 | Native protocol, no SQL dialect — queries are translated; exports page through a cursor |

## Adding a connection

1. On the connection screen, click **New connection**.
2. Choose the engine.
3. Enter host, port, database (optional for most engines) and credentials — or a file path for SQLite.
4. Click **Test**. Junction reports exactly what failed if it can't connect.
5. **Save**.

Organise connections into **folders**, and give each a **colour** and **emoji icon** — handy for telling production from staging at a glance.

## SSH tunnels

For a database that's only reachable from inside a network, enable **SSH tunnel** in the connection editor and enter the SSH host, port, user and either a password or a private key (with optional passphrase). Junction opens the tunnel itself when you connect — no separate `ssh -L` needed. The database host and port are then as seen *from the SSH server* (often `127.0.0.1`).

## TLS / SSL

Turn on **SSL/TLS** in the connection editor to encrypt traffic to the server. Use it for any database reached over the internet.

## Read-only connections

Tick **Read-only** in the connection editor and Junction refuses every write through it — table edits, write nodes on the canvas, DDL, and the AI assistant. Use it for production data you only want to look at.

Even on writable connections, destructive statements (`DROP`, `TRUNCATE`, `UPDATE`/`DELETE` without a `WHERE`) ask for confirmation while **Settings → Confirm dangerous actions** is on (the default).

## Where credentials are stored

Passwords, SSH passwords, keys and passphrases are encrypted with AES-256-GCM in your local data folder. The encryption key lives in your operating system's keychain (macOS Keychain, Windows Credential Manager, the Secret Service on Linux). Nothing is synced or uploaded. See [Privacy & security](privacy-and-security.md).

## Connection limits

The Free plan includes 3 connections; Pro is unlimited. See [Plans & licensing](plans-and-licensing.md).

## Troubleshooting

| Symptom | Likely cause |
|---|---|
| *Connection refused* | Wrong host/port, the server isn't running, or a firewall blocks it. For Docker, use the *published* port. |
| *Authentication failed* | Wrong user/password, or (Postgres) `pg_hba.conf` doesn't allow your host / auth method. |
| *Timed out* | The server isn't reachable from your network — you may need an SSH tunnel or VPN. |
| Works in another tool, not in Junction | Compare SSL settings and the exact host: `localhost` and `127.0.0.1` can differ (socket vs TCP). |

More in [Troubleshooting](troubleshooting.md).
