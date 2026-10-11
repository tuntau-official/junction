# Getting started

Five minutes from first launch to your first query.

## 1. Try the example database

No database at hand, or don't want to experiment on a real one? On the connection screen, load the **example bookstore database** — a SQLite file with 7 related tables (books, authors, customers, orders…). It's a private copy: break it as much as you like.

The **Learning** button in the toolbar opens guided tutorials that use it — *Your first canvas* is a good start.

## 2. Connect your own database

Click **New connection**, pick the engine, fill in host, port, database and credentials, then **Test** and **Save**. Details per engine, SSH tunnels and read-only mode: [Connections](connections.md).

A coloured dot on each connection card shows its health. Junction polls in the background, so a red dot means the server is unreachable right now.

## 3. Find your way around

| Area | What it's for |
|---|---|
| **Sidebar** | Connections, then the structure of the active one: tables, views, functions, procedures |
| **Scope picker** | Which database / schema you're working in |
| **Tabs** | Table browsers, blueprints, SQL scripts, the relation graph — as many as you like |
| **Toolbar** | New tab (`+`), assistant, Learning, MCP status, settings |
| **⌘K / Ctrl+K** | The command palette — jump to any table, run any action, switch connection |

## 4. Browse and edit a table

Click a table in the sidebar. Its rows open in a tab with filtering, sorting and paging. Double-click a cell to edit it; add or delete rows from the toolbar.

Edits are **staged** — nothing is written until you click **Commit** in the pending-changes bar. Destructive statements ask for confirmation first, and connections marked read-only refuse writes altogether.

## 5. Build a query on the canvas

1. Open a new **Blueprint** tab (`+` → Blueprint).
2. Drag a table from the sidebar onto the canvas.
3. Drag a wire off its output pin and release on empty canvas — Junction suggests what fits: Filter, Join, Pick columns, Aggregate…
4. Watch the **SQL pane** update with every change.
5. Press **⌘R / Ctrl+R** to run.

Prefer typing? Paste any SQL into the SQL pane — the canvas rebuilds itself from it. Read [Blueprints](blueprints.md) for the full picture.

## 6. Find how two tables connect

Open the **Relations** graph, pick a *from* table and a *to* table, and Junction lists every join route between them. Click **Build SQL from this route** to get a ready-made query. See [Relations](relations.md).

## Keyboard shortcuts worth knowing

| Shortcut (macOS / Windows & Linux) | Action |
|---|---|
| ⌘K / Ctrl+K | Command palette |
| ⌘R / Ctrl+R | Run the active query or script |
| ⌘S / Ctrl+S | Save the current query or blueprint |
| ⌘Z, ⌘⇧Z / Ctrl+Z, Ctrl+Shift+Z | Undo / redo on the canvas (history survives restarts) |
| A, or right-click the canvas | Node catalog |
| Space + drag | Pan the canvas |
| Del | Delete selected nodes |
| Esc | Close panels and dialogs |

## Next steps

- [Blueprints](blueprints.md) — everything the canvas can do
- [AI assistant](ai-assistant.md) — ask questions about your data in plain language
- [Plans & licensing](plans-and-licensing.md) — what's in Free and what Pro adds
