# ArcGIS Cloud-Referenced Imagery Publishing Workflows

A collection of minimal, practical Jupyter notebooks for publishing Image Services **by reference** from cloud-hosted raster data using the **ArcGIS API for Python**. These workflows target ArcGIS Enterprise with a registered Cloud Datastore (e.g., AWS S3) and require no local `arcpy` installation or geoprocessing toolboxes.

## Repository Structure

```
.
├── arcgis/                                 # Core, reusable publishing workflows
│   ├── publish_raster_collection.ipynb     # Publish an image collection (mosaic dataset) by reference
│   └── publish_raster_dataset.ipynb        # Publish a standalone raster dataset by reference
│
├── examples/                               # Advanced, real-world publishing pipelines
│   └── publish_tempo.ipynb                 # End-to-end TEMPO NO₂ multidimensional image service
│
├── .env.example                            # Environment variable template
├── pyproject.toml                          # Python project / dependency definition
└── CONTRIBUTING.md                         # Guidelines for contributing
```

## Workflows

| Notebook | Folder | Description |
|----------|--------|-------------|
| [`publish_raster_collection.ipynb`](arcgis/publish_raster_collection.ipynb) | `arcgis/` | Publish a mosaic/image collection Image Service by reference from S3 |
| [`publish_raster_dataset.ipynb`](arcgis/publish_raster_dataset.ipynb) | `arcgis/` | Publish a single raster dataset Image Service by reference from S3 |
| [`publish_tempo.ipynb`](examples/publish_tempo.ipynb) | `examples/` | Advanced TEMPO NO₂ pipeline with RasterCollection map/filter, quality masking, and ongoing slice appending |

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/cwaltsgeo/ArcGIS_Publishing_Workflows.git
cd ArcGIS_Publishing_Workflows
```

### 2. Install dependencies

This project uses [uv](https://github.com/astral-sh/uv) for dependency management.

```bash
uv sync
```

Or with `pip`:

```bash
pip install arcgis python-dotenv ipykernel
```

### 3. Configure environment variables

Copy `.env.example` to `.env` and fill in your values:

```bash
cp .env.example .env
```

| Variable | Description |
|----------|-------------|
| `PORTAL_URL` | Base URL of your ArcGIS Enterprise Portal (e.g., `https://arcgisenterprise.com/portal`) |
| `CLIENT_ID` | OAuth2 Client ID registered in your Portal |
| `CLOUDSTORE_NAME` | Datapath of the registered Cloud Datastore (e.g., `/cloudStores/my-s3-store`) |

### 4. Launch Jupyter and run a notebook

Open any notebook from the `arcgis/` or `examples/` directories and run cells sequentially.

## Prerequisites

- ArcGIS Enterprise (with Raster Analytics server)
- A registered **Cloud Datastore** (AWS S3 or compatible)
- Python
- ArcGIS API for Python

## Further Reading

- [ArcGIS API for Python – Raster Analytics](https://developers.arcgis.com/python/latest/api-reference/arcgis.raster.analytics.html)
- [`arcgis/` folder README](arcgis/README.md)
- [`examples/` folder README](examples/README.md)
- [Contributing guide](CONTRIBUTING.md)