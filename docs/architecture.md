# Architecture notes

> Draft. Everything here is a proposal to discuss, not a decision.

## Goals

- One workbook object where the grid, SQL queries and slides share the same data model
- Slides and sheets reference queries; they do not store copies of the data
- Works for a single person with a CSV file as well as a team on a shared database
- Plain-text, diff-friendly file format

## Layers

```
Connectors  ->  Data model (tables + queries)  ->  Views (grid, slides)
```

- **Connectors** bring data in: files first, databases and data lakes later.
- **Data model** holds tables and named queries. A query result can be shown as a grid, a chart or a table on a slide.
- **Views** only describe how to display a query; they hold no data of their own.

## Open questions

1. **Query engine.** An embedded engine such as DuckDB (including its WebAssembly build for the browser) is the leading candidate. To evaluate: file size limits in the browser, and how to push queries down to remote databases.
2. **Formulas.** How spreadsheet-style formulas interact with SQL tables: cell references over query results, or formulas as a layer on top of tables?
3. **File format.** Text-based and diff-friendly (for example a folder of YAML/JSON plus `.sql` files, or a single file). To decide: what is practical to open and share for non-technical users.
4. **Query builder.** Generates readable SQL that users can see and edit.
5. **Credentials and permissions.** Delegate to the underlying database wherever possible; decide where secrets are stored.
6. **Import and export.** `.xlsx` and `.pptx` interoperability, and how much is realistic for a first release.
7. **Platform.** Browser-only, desktop app, or both, and how much runs locally versus on a server.

## First milestone

Import a CSV/Parquet file, show it in a grid, run SQL on it, and present a chart that is a live query. Everything else follows from what we learn here.
