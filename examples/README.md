# Examples

This folder contains end-to-end, real-world publishing pipelines built on top of the core workflows in [`arcgis/`](../arcgis/). Where the core notebooks illustrate the fundamental mechanics of publishing by reference, the examples here demonstrate how those primitives compose into complete, domain-specific solutions.

Each example is self-contained and includes its own step-by-step commentary. All examples share the same environment setup described in the root [`README.md`](../README.md).

## When to Use These Examples

The core `arcgis/` notebooks answer: *"How do I publish a raster or image collection by reference?"*

The examples here answer: *"How do I apply that to [a specific dataset / workflow / operational pattern]?"* They typically involve:

- Pre-processing or transforming source data before publishing (e.g., quality masking, band math, metadata extraction)
- Working with multidimensional or time-series datasets
- Combining multiple core operations into a repeatable operational pipeline
- Handling ongoing data ingestion (e.g., appending new time slices to an existing service)

## Notebooks

### [`publish_tempo.ipynb`](publish_tempo.ipynb)

An advanced pipeline for processing and publishing **NASA TEMPO** tropospheric NO₂ satellite data as a multidimensional Image Service by reference.

**Highlights:**
- Builds a `RasterCollection` from TEMPO granules stored in S3, with filenames and ISO timestamps extracted from the granule naming convention
- Applies per-granule quality masking using `multidimensional_filter` and `raster_calculator` (`SetNull` on QA flag and cloud fraction)
- Reduces the collection to a multidimensional CRF via `.to_multidimensional_raster()` and persists it to the Cloud Datastore
- Publishes the initial service using `publish_raster_dataset.ipynb` as a dependency
- Demonstrates an ongoing append pattern using `manage_multidimensional_raster` (`APPEND_SLICES`) and `build_multidimensional_transpose`

## Contributing an Example

A good example notebook should:

1. State its goal clearly in the opening markdown cell
2. Load credentials from environment variables (via `python-dotenv`) — never hardcode them
3. Follow the same step-by-step cell structure as the existing notebooks
4. Reference the relevant core notebook(s) from `arcgis/` where applicable
