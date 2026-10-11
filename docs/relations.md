# Relations

A foreign key is a column that points at a row in another table — how a database says "this order belongs to that customer". Junction reads every foreign key and uses them in three places:

- the **relation graph** — a map of all tables and how they link;
- the **Join node** — the right join is suggested the moment you wire two tables together;
- the **AI assistant** — it knows how your tables connect when it writes SQL.

## The relation graph

Open it from the toolbar or with ⌘K → *Relations*. Every table is a node; every foreign key an edge, pointing from the referencing table to the referenced one (`order_items → orders`).

### Focus a neighbourhood

Pick a **from** table. Its neighbourhood lights up by distance — white, green, lime, amber, red as you go further out — while the rest fades back. Step the depth up or down and the view updates instantly; the layout never reshuffles while you explore. Tick **Filter selection** to hide everything outside the focus instead.

### Trace every route (Pro)

Add a **to** table and Junction enumerates **every join route** between the two, shortest first. Hover a route to highlight it on the map. Click **Build SQL from this route** and you get a ready-made query with every join filled in — on the canvas, so you can keep shaping it.

This is the fastest way to answer "how on earth do I get from `invoices` to `warehouses`?" in a schema you didn't design.

## Relations without foreign keys

Many applications never declare foreign keys in the database — the ORM knows the relations, the schema doesn't. You can always join such tables by hand (pick the columns on both sides and Junction builds the `ON`), but Junction can also learn them:

### Codebase inference (Pro)

Link a connection to your application's repository and Junction reads its models to infer the relations, then fuzzy-matches model names to real tables. Supported today:

| Framework | Where Junction looks |
|---|---|
| LoopBack 3 | `common/models/*.json` (`relations` blocks) |
| Laravel / Eloquent | Model classes (`hasMany`, `belongsTo`, …) |

Inferred relations appear in the graph and in join suggestions alongside real foreign keys. Junction only **reads** your code; it never writes to the repository.

Want another framework supported? [Open a feature request](https://github.com/tuntau-official/junction/issues/new?template=feature_request.yml).

## Cross-database queries (Pro)

On MySQL and PostgreSQL, routes and joins can span databases on the same server — Junction qualifies the table names for you.
