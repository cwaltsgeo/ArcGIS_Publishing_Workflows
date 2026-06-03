# Contributing

Contributions are welcome — whether that's a bug fix to an existing notebook, a new example pipeline, or an improvement to the documentation.

## Ways to Contribute

- **New example notebooks** — real-world workflows built on the core `arcgis/` notebooks (see [`examples/README.md`](examples/README.md) for what makes a good example)
- **Fixes or improvements** to existing notebooks (clarity, correctness, updated API usage)
- **Documentation** updates to any README

## Getting Started

1. Fork the repository and create a branch from `main`:
   ```bash
   git checkout -b your-feature-name
   ```

2. Follow the setup steps in the root [README](README.md) to get your environment running.

3. Make your changes, keeping notebooks in the appropriate folder:
   - `arcgis/` — core, reusable publishing mechanics
   - `examples/` — end-to-end, domain-specific pipelines

## Guidelines

- **No credentials in notebooks.** All sensitive values (portal URL, client ID, datastore names) must be loaded from environment variables via `python-dotenv`. Use `.env.example` as the reference.
- **Clear cell structure.** Use markdown cells to introduce each step before the code cell that implements it.
- **Clean outputs.** Clear all cell outputs before committing notebooks.
- **One concern per notebook.** Keep notebooks focused; chain them by reference rather than duplicating logic.

## Submitting Changes

1. Push your branch and open a Pull Request against `main`.
2. Describe what the change does and, for new examples, what ArcGIS/dataset scenario it covers.
3. I will review and merge or provide feedback.

## Requesting Changes

Search for open issues and pull requests to see if your request has already been made.
If not, open a [GitHub Issue](https://github.com/cwaltsgeo/ArcGIS_Publishing_Workflows/issues) with a description of the change you would like to see.

## Reporting Issues

Open a [GitHub Issue](https://github.com/cwaltsgeo/ArcGIS_Publishing_Workflows/issues) with a description of the problem, the relevant notebook, and any error output.
