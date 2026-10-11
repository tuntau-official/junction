<div align="center">

# 🔀 Junction

**A visual SQL studio — draw queries as node graphs, see every route between your tables, and keep the SQL in sync.**

[**Download**](https://github.com/tuntau-official/junction/releases/latest) ·
[Documentation](docs/README.md) ·
[Website](https://junction.tuntau.com) ·
[Report a bug](https://github.com/tuntau-official/junction/issues/new/choose)

[![Latest release](https://img.shields.io/github/v/release/tuntau-official/junction?label=latest&color=22c55e)](https://github.com/tuntau-official/junction/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/tuntau-official/junction/total?color=3b82f6)](https://github.com/tuntau-official/junction/releases)
![Platforms](https://img.shields.io/badge/platforms-macOS%20%C2%B7%20Windows%20%C2%B7%20Linux-6b7280)

<!-- Screenshots: drop PNGs (~1600px wide, dark theme) into assets/ and uncomment.
![The blueprint canvas — a query as a node graph, with its SQL alongside](assets/canvas.png)
-->

</div>

---

Junction is a desktop database studio by [Tuntau](https://tuntau.com). Instead of typing queries, you draw them: drop a table on the canvas, wire a filter or a join onto it, and Junction compiles the picture into real SQL for your database — SQL you can always see, edit and run. Type or paste SQL instead, and the graph rebuilds itself.

Everything runs on your machine. Native drivers, no cloud account, no telemetry. Your credentials are encrypted locally, your license key verifies offline (with a short check-in every few weeks), and the AI assistant talks only to the model *you* configure.

## Highlights

- **Blueprint canvas** — every SQL construct is a typed node: joins, filters, aggregates, window functions, CASE, CTEs, unions, DML and DDL. Canvas and SQL stay in two-way sync. Pins are coloured by SQL type, so a type mismatch is visible before you run anything. → [Blueprints](docs/blueprints.md)
- **Relations graph** — every foreign key as a map. Pick a *from* and a *to* table and Junction lists **every join route** between them; turn one into a query with one click. → [Relations](docs/relations.md)
- **Codebase linking** — ORMs often don't store foreign keys in the database. Point Junction at your repository and it infers the relations from your models.
- **Browse & edit safely** — tabbed table browsing, inline edits staged behind a commit bar, read-only lock per connection, confirmation before anything destructive.
- **AI assistant, bring your own model** — any OpenAI-compatible endpoint (OpenAI, Ollama, LM Studio, Azure, LiteLLM…). It inspects your real schema, verifies its answers, and asks before every write. → [AI assistant](docs/ai-assistant.md)
- **MCP server** — let Claude, Cursor and other MCP clients query your databases through Junction, read-only and token-gated. → [MCP server](docs/mcp-server.md)
- **Procedures & functions as blueprints** — author server-side routines on the canvas, preview the exact `CREATE`, dry-run with mock parameters in a rolled-back transaction.
- **Learning built in** — guided tutorials, a searchable knowledge book and a safe example database to practise on.

<!--
| | |
|---|---|
| ![Route tracing](assets/routes.png) | ![AI assistant](assets/assistant.png) |
| **From → to routes** — every join path between two tables | **AI assistant** — your model, your schema, your approval |
-->

### Supported databases

| Engine | Notes |
|---|---|
| 🐘 PostgreSQL | |
| 🐬 MySQL / MariaDB | Cancelling a query sends a real `KILL QUERY` |
| 📦 SQLite | A file on disk, no server needed |
| 🟥 SQL Server | |
| 🍃 MongoDB | Native protocol; queries are translated |

All server engines can connect through an **SSH tunnel**.

## Install

Grab the installer for your platform from the [**latest release**](https://github.com/tuntau-official/junction/releases/latest):

| Platform | File |
|---|---|
| macOS | `Junction_<version>_universal.dmg` — signed & notarized |
| Windows | `Junction_<version>_x64-setup.exe` |
| Debian / Ubuntu | `Junction_<version>_amd64.deb` |
| Other Linux | `Junction_<version>_amd64.AppImage` |

Step-by-step instructions, first-launch warnings and checksum verification: **[Installation guide](docs/installation.md)**.

Junction updates itself. Every update is cryptographically signed and checked before it installs.

## Plans

Junction is **free to use** — no account, no time limit. Pro unlocks unlimited connections, route tracing, the AI assistant, codebase linking, cross-database queries and migration tools. Every install starts with a **14-day Pro trial**, no credit card.

See [Plans & licensing](docs/plans-and-licensing.md) and current prices on [junction.tuntau.com](https://junction.tuntau.com).

## Documentation

| | |
|---|---|
| [Installation](docs/installation.md) | Install, update, uninstall, verify downloads |
| [Getting started](docs/getting-started.md) | Your first connection and your first query, in five minutes |
| [Connections](docs/connections.md) | Engines, SSH tunnels, read-only mode, where credentials live |
| [Blueprints](docs/blueprints.md) | The canvas, nodes, typed pins, scripts, `.jbpl` files |
| [Relations](docs/relations.md) | The relation graph, route tracing, codebase inference |
| [AI assistant](docs/ai-assistant.md) | Configure your model, what it can and can't do |
| [MCP server](docs/mcp-server.md) | Connect Claude, Cursor and other MCP clients |
| [Plans & licensing](docs/plans-and-licensing.md) | Free vs Pro, trials, seats, activating a key |
| [Privacy & security](docs/privacy-and-security.md) | What stays local, what (rarely) leaves, and how to report a vulnerability |
| [Troubleshooting](docs/troubleshooting.md) | Common problems and how to fix them |

The app also ships its own **knowledge book** (Learning → Knowledge book) with a full SQL primer and a reference for every node.

## Feedback & support

- **Bugs and feature requests** → [open an issue](https://github.com/tuntau-official/junction/issues/new/choose). In the app, *Help → Report a Bug…* sends a report with optional, redacted screenshot straight to us.
- **Questions, help** → [hello@tuntau.com](mailto:hello@tuntau.com)
- **Licensing & billing** → [sales@tuntau.com](mailto:sales@tuntau.com)
- **Security issues** → please don't open a public issue; see [SECURITY.md](SECURITY.md).

## About this repository

Junction is commercial, closed-source software. This repository holds the public documentation, release notes and installers, and the issue tracker. Release notes for every version are on the [Releases page](https://github.com/tuntau-official/junction/releases).

© Tuntau. All rights reserved.
