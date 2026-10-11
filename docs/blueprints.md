# Blueprints

A **blueprint** is a SQL query drawn as a node graph. It isn't a separate thing from the SQL — it's the same tree shown two ways, always in sync. Rewire a node and the SQL regenerates; type or paste SQL and the graph rebuilds.

## Why draw a query?

- **No syntax to remember.** The structure *is* the syntax — you can't forget a comma or misplace a clause.
- **Every value is picked, not typed.** Tables, columns and types come from your live schema, so a misspelt column is impossible.
- **You can see the data flow.** Which table feeds which filter, where a join branches — readable at any zoom.
- **Safe experimentation.** Change a join type or add a Log node and see exactly how the SQL changes.
- **It teaches SQL.** The SQL pane shows what every node compiles to.

SQL still wins for quick one-off tweaks — and you never have to choose. Paste a query someone sent you and it becomes nodes; anything the parser can't express is kept verbatim as a **SQL node** rather than dropped.

## Adding nodes

- **Right-click** the canvas (or press **A**) for the node catalog, opened where your pointer is. It's searchable and grouped: operators, aggregates, your database's own function set, statements, tables, and your own stored functions.
- **Drag a wire** off a pin and release on empty canvas — Junction offers only the nodes that fit there and wires the new one up in the same gesture.
- **Drag a table** from the sidebar.

The catalog only shows what your database supports, so you're never offered a node that can't compile.

## What can be a node?

Practically all of standard SQL:

| Group | Nodes |
|---|---|
| Sources | Table (`FROM`), hand-written SQL, CTE reference, switch database (`USE`) |
| Shaping rows | Filter (`WHERE`), Pick columns (`SELECT`), Join, Union / Intersect / Except, `CASE`, computed column, `CAST` |
| Aggregating | Aggregate (`GROUP BY` + `COUNT`, `SUM`…), Window functions |
| Ordering | Sort (`ORDER BY`), Limit |
| Writing data | Insert, Update, Delete, Truncate |
| Schema | Create / alter / rename / drop table, columns, views, indexes, constraints, databases, `GRANT` |
| Flow & debugging | Log (show intermediate rows), Explain, Begin / Commit transaction, Set / Get variable, Reroute, Frame |
| Routines | Entry, Return, Convert — for procedure and function blueprints |

Each node is documented in the in-app **Knowledge book → Nodes, explained**.

## Typed pins

Every pin is coloured by its SQL type, and wires take that colour — a number flowing into a text slot is visible before you run anything. Connect two incompatible types and Junction inserts a **Convert** node carrying the right `CAST` for your database.

## Transactions

A **Begin** node hands out a transaction; every step that should belong to it is wired to its *trans* pin; a **Commit** (or rollback) node ends it. Membership is the wiring — a statement can't silently fall outside the transaction. Nodes inside one show a small ⇄ badge, and the SQL compiles to a real `BEGIN … COMMIT`.

## Multi-statement scripts

A script with several statements becomes several **islands** on the canvas, run top to bottom. Each shows its step number; move an island up to run it earlier. Use **Set / Get variable** nodes (or drag a variable from the variables panel on the left) to pass values between statements.

## Procedures and functions

**+ → Procedure editor / Function editor** opens a canvas with an **Entry** node (add parameters on it — each becomes a typed pin) and a **Return** node.

- **Deploys as** shows the exact `CREATE PROCEDURE` / `CREATE FUNCTION` that will run.
- **Test** dry-runs the body with mock parameter values inside a rolled-back transaction and reports the result — nothing is saved while you iterate.
- Paste an existing `CREATE PROCEDURE` / `CREATE FUNCTION` and it becomes a blueprint.
- Functions you create show up as callable nodes in the catalog.

## Working comfortably

- **Zoom out** and nodes collapse to icon + name chips, so big queries read as a dataflow diagram.
- **Reroute points** — double-click a wire to add a draggable bend point.
- **Frames** — group and label related nodes.
- **Undo / redo** (⌘Z / ⌘⇧Z) covers every canvas edit, and the history survives restarting the app.
- **Space + drag** pans with any mouse button.

## Saving blueprints

| Format | What's in it | Use it when |
|---|---|---|
| `.jbpl` | The graph itself — every node, wire, colour and frame — with the SQL derived from it | You want the blueprint exactly as you drew it |
| `.sql` | Plain SQL, with the layout, view and frames tucked into a comment block | You want a file any tool can run, and Junction can still reopen as a canvas |

Any `.sql` file — even one Junction never saw — opens straight onto the canvas.
