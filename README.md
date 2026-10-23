# Spreadshow

An open-source workbook for working with data: a spreadsheet you can query with SQL, and slides that stay connected to the numbers behind them.

> **Status: early and experimental.** The architecture is still being defined and there is nothing to install yet. Ideas and feedback are very welcome.

## The idea

Spreadsheets and slide decks are great tools, but data usually gets copied from one into the other and goes out of date. Spreadshow tries to keep everything together:

1. **Connect** a data source: a CSV or Parquet file, a database, a data lake.
2. **Explore** it in a spreadsheet-style grid, with SQL or a visual query builder that shows the SQL it generates.
3. **Present** the results as slides that point to the data instead of holding a copy, so they stay up to date and readers can filter and explore.

A workbook is stored as plain text files, so it can be versioned and compared with git.

## Who it might help

Anyone who works with numbers and wants to understand them or show them to others: individuals, students, teachers, researchers, small organizations and teams.

## Planned scope

The first version aims to be small:

- Import a CSV or Parquet file
- A grid with formulas and a SQL panel on the same data
- A present mode where charts and tables are live queries

Connectors for databases and data lakes come after that. See [docs/architecture.md](docs/architecture.md) for the current thinking.

## Repository layout

| Path | Contents |
|---|---|
| `packages/core` | Workbook model, query engine integration, file format |
| `packages/connectors` | Data source connectors |
| `packages/app` | User interface |
| `docs` | Architecture notes and design decisions |
| `examples` | Sample workbooks and datasets |

## Contributing

Contributions are welcome. Please read the [contributing guide](https://github.com/spreadshow/.github/blob/main/CONTRIBUTING.md) and the [code of conduct](https://github.com/spreadshow/.github/blob/main/CODE_OF_CONDUCT.md). Good places to start are the open issues and the design questions listed in the architecture notes.

## License

Apache License 2.0. See [LICENSE](LICENSE).
