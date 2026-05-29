# ArcGIS Cloud-Referenced Imagery Publishing Workflows

This repository provides minimal, practical examples for publishing Image Services **by reference** from data stored in an ArcGIS Cloud Datastore (e.g., AWS S3) using the ArcGIS API for Python. These workflows bypass the need for local `arcpy` installations or geoprocessing toolboxes, executing directly via Portal analytics and administrative endpoints.

## Repository Structure

### 1. `arcgis/publish_raster_collection.ipynb`
* **Purpose:** Demonstrates how to publish an Image Collection-based Image Service (synonymous with mosaic dataset-based image services) by reference.
* **Workflow:**
  * Connects to ArcGIS Enterprise Portal.
  * Locates a registered S3 Cloud Datastore.
  * Dynamically references a collection of target raster datasets.
  * Creates an empty `imageService` placeholder item configured with `copyData: false` and source type `esriImageServiceSourceTypeMosaicDataset`.
  * Populates the service using `create_image_collection()` with context parameters passing `{byref: True}`.

### 2. `arcgis/publish_raster_dataset.ipynb`
* **Purpose:** Demonstrates how to publish an individual, standalone raster dataset from a Cloud Datastore by reference.
* **Workflow:**
  * Connects to ArcGIS Enterprise Portal and verifies the Cloud Datastore connection.
  * Formats the target input raster path from the datastore.
  * Constructs an image service configuration using `copyData: false` and `esriImageServiceSourceTypeDataset`.
  * Deploys the service via `gis.content.create_service()`.
  * Manually starts the underlying service using the Raster Analytics server administration endpoint.

### 3. `arcgis/publish_tempo.ipynb`
* **Purpose:** A targeted, advanced pipeline demonstrating how to leverage `RasterCollection` objects along with map/reduce operations and Raster Function Templates (RFTs) to filter, mask, and append multi-dimensional satellite imagery (TEMPO dataset).
* **Workflow:**
  * Extracts filenames and formats ISO timestamps directly from the input data.
  * Builds a `RasterCollection` parameterized by a custom metadata attribute dictionary.
  * Applies a localized `.map()` function using `multidimensional_filter` and `raster_calculator` to clean data based on quality and cloud fraction flags.
  * Converts the collection to a multidimensional raster (`.to_multidimensional_raster()`) and persists it as a Cloud Raster Format (CRF).
  * Outlines ongoing, programmatic slice appending (`APPEND_SLICES`) and multidimensional transpose updates via `manage_multidimensional_raster` and `build_multidimensional_transpose`.
  