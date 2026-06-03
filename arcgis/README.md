# ArcGIS Cloud-Referenced Imagery Publishing Workflows

This folder contains minimal, practical notebooks for publishing Image Services **by reference** from data stored in an ArcGIS Cloud Datastore (e.g., AWS S3) using the ArcGIS API for Python. These workflows bypass the need for local `arcpy` installations or geoprocessing toolboxes, executing directly via Portal analytics and administrative endpoints.

## Notebooks

### `publish_raster_collection.ipynb`

Demonstrates how to publish an **Image Collection**-based Image Service (synonymous with mosaic dataset-based image services) by reference.

**Workflow:**
- Connects to ArcGIS Enterprise Portal.
- Locates a registered S3 Cloud Datastore.
- Dynamically references a collection of target raster datasets.
- Creates an empty `imageService` placeholder item configured with `copyData: false` and source type `esriImageServiceSourceTypeMosaicDataset`.
- Populates the service using `create_image_collection()` with context parameters passing `{byref: True}`.

---

### `publish_raster_dataset.ipynb`

Demonstrates how to publish an **individual, standalone raster dataset** from a Cloud Datastore by reference.

**Workflow:**
- Connects to ArcGIS Enterprise Portal and verifies the Cloud Datastore connection.
- Formats the target input raster path from the datastore.
- Constructs an image service configuration using `copyData: false` and `esriImageServiceSourceTypeDataset`.
- Deploys the service via `gis.content.create_service()`.
- Manually starts the underlying service using the Raster Analytics server administration endpoint.

## Prerequisites

See the root [`README.md`](../README.md) for environment setup and dependency installation.
