# OpenTopography Global DEM Downloader (Interactive API Client)

A lightweight, interactive Python notebook for downloading global elevation (DEM) data from the [OpenTopography Global DEM API](https://portal.opentopography.org/apidocs/#/Public/getGlobalDem) — no manual portal navigation, no GIS software, just bounding-box coordinates and an API key.

## Overview

This notebook is a simple, guided 4-step interactive workflow:

1. **Enter bounds and API key** — North/South/West/East bounds in decimal degrees, plus a personal OpenTopography API key
2. **Select a DEM product** — choose from 13 supported global elevation/bathymetry datasets via a numbered menu
3. **Send the download request** — builds and sends the API request, with human-readable interpretation of HTTP response codes
4. **Download the file** — writes the returned raster to disk as a GeoTIFF

## Supported DEM Products

| # | Product | Resolution | Notes |
|---|---|---|---|
| 1 | SRTMGL3 | 90 m | SRTM Global |
| 2 | SRTMGL1 | 30 m | SRTM Global |
| 3 | SRTMGL1_E | 30 m | SRTM Global, Ellipsoidal heights |
| 4 | AW3D30 | 30 m | ALOS World 3D |
| 5 | AW3D30_E | 30 m | ALOS World 3D, Ellipsoidal heights |
| 6 | SRTM15Plus | 500 m | Global bathymetry |
| 7 | NASADEM | — | NASA reprocessed DEM |
| 8 | COP30 | 30 m | Copernicus Global DSM |
| 9 | COP90 | 90 m | Copernicus Global DSM |
| 10 | EU_DTM | 30 m | Digital Terrain Model |
| 11 | GEDI_L3 | 1000 m | Digital Terrain Model |
| 12 | GEBCOIceTopo | 500 m | Global bathymetry |
| 13 | GEBCOSubIceTopo | 500 m | Global bathymetry |

Output format defaults to **GeoTIFF**, with Arc ASCII Grid (`AAIGrid`) and Erdas Imagine (`HFA`) also supported by the underlying API.

## Method Notes

- **Human-readable HTTP status handling**: the notebook maps raw response codes (`200`, `204`, `400`, `401`, `500`) to plain-language messages, so a failed request tells you *why* (e.g. "No Data Available" vs. "Unauthorized") rather than just a numeric code.
- **API key required**: OpenTopography requires a free personal API key (register at [portal.opentopography.org](https://portal.opentopography.org)) — the notebook prompts for it interactively rather than hardcoding it, keeping credentials out of the notebook file itself.
- **Fully interactive by design**: bounds, product choice, and output filename are all entered via `input()` prompts, making this a reusable one-off download tool rather than a scripted batch pipeline — well suited for quickly pulling a DEM tile for a new study area without editing code.

## Tech Stack

- `pandas`
- `requests` — OpenTopography REST API access

## Repository Structure

```
.
├── Open_Topography_Data_Download_API.ipynb   # Main interactive downloader
└── README.md
```

## Getting Started

```bash
pip install pandas requests
```

1. Register for a free API key at [portal.opentopography.org](https://portal.opentopography.org)
2. Open the notebook and run each cell in order, entering bounds/key/product/filename when prompted


