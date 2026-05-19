# Repository Summary: LLM_lesson_exemplar

## Overview

**LLM_lesson_exemplar** is a teaching and demonstration repository that shows how Large Language Models (LLMs) can harmonize geospatial datasets for environmental science research. Instead of writing custom scripts for each dataset combination, this system uses LLMs to intelligently orchestrate data harmonization workflows.

---

## Core Concept

The repository demonstrates an AI-assisted workflow where:

1. **User provides** dataset URLs and a region of interest
2. **LLM inspects** the datasets and makes harmonization decisions
3. **Python functions** perform the actual geospatial processing
4. **System generates** harmonized outputs and visualizations

This approach eliminates the need for custom scripts for each dataset combination, making geospatial analysis more accessible to scientists.

---

## Key Components

### Core Library

**[`src/geospatial_harmonizer.py`](../src/geospatial_harmonizer.py)**
- Main harmonization engine
- Handles downloading, reprojecting, clipping, and resampling
- Supports multiple data formats:
  - Rasters (GeoTIFF, NetCDF)
  - Vectors (Shapefile, GeoJSON, GeoPackage)
  - ZIP archives (automatic extraction)
  - OPeNDAP streaming (for climate data)
- Provides Python API: `DatasetSpec`, `ExampleWorkflow`, `run_harmonization_example()`

### Helper Scripts

**[`scripts/check_urls.py`](../scripts/check_urls.py)**
- Validates that dataset URLs are reachable
- Ensures URLs return actual geospatial data (not HTML portal pages)

**[`scripts/find_dataset.py`](../scripts/find_dataset.py)**
- Searches the data catalog by keyword
- Helps discover relevant datasets

**[`scripts/region_extent.py`](../scripts/region_extent.py)**
- Looks up boundaries for US states, counties, and places
- Returns bounding boxes and boundary polygons
- Supports different coordinate reference systems

### Examples

**[`examples/colorado_fire_risk/`](../examples/colorado_fire_risk/)**
- Reference implementation demonstrating the complete workflow
- Harmonizes four datasets for Colorado fire risk analysis:
  - FBFM40 Fire Behavior Fuel Models (raster)
  - MACAv2 Winter Precipitation (raster, OPeNDAP)
  - MTBS Burned Area Boundaries (vector)
  - Microsoft Building Footprints (vector, rasterized)
- All harmonized to EPSG:4326, ~270m resolution
- **Read this first** to understand the pattern

### Workflows

**[`workflows/`](../workflows/)**
- Where user analyses are created
- Each project gets its own folder (e.g., `utah_fire_risk/`)
- Structure:
  ```
  workflows/
    <project_name>/
      <script>.py
      output/
        harmonized_*.tif
        harmonized_*.geojson
        harmonized_visualization.png
        harmonized_visualization.html
  ```

---

## The Harmonization Pipeline

The system follows a 10-step process (detailed in [`TASKS.md`](../TASKS.md)):

1. **Validate Data Sources** - Check URLs are reachable and return geospatial data
2. **Download Datasets** - Fetch data, extract archives, identify geospatial files
3. **Determine Target Grid** - Resolve region to bounding box and boundary polygon
4. **Reproject to Common CRS** - Transform all datasets to the same coordinate system
5. **Clip to Region of Interest** - Crop to target area using boundary or bounding box
6. **Resample Rasters** - Align all rasters to the same pixel size
   - Nearest-neighbor for categorical data (land cover, fuel models)
   - Bilinear for continuous data (temperature, precipitation)
7. **Handle Vector Data** - Keep as vector or rasterize to match raster grid
8. **Save Harmonized Outputs** - Write GeoTIFFs and GeoJSONs
9. **Generate Visualizations** - Create static PNG and interactive HTML maps
10. **Document the Work** - Record decisions and parameters for reproducibility

---

## What the System Can Do

### Data Handling
- Download from direct URLs
- Extract and process ZIP archives
- Stream data via OPeNDAP (for large climate datasets)
- Identify geospatial files automatically

### Spatial Operations
- Reproject to any coordinate reference system
- Clip to state/county/place boundaries (US)
- Clip to custom boundaries or bounding boxes
- Resample rasters to common resolution
- Rasterize vector data
- Preserve vector geometry when needed

### Output Generation
- Harmonized rasters (GeoTIFF)
- Harmonized vectors (GeoJSON)
- Static visualization (PNG)
- Interactive map (HTML with Folium)

---

## Design Philosophy

**LLM Responsibilities:**
- Inspect and understand datasets
- Make harmonization decisions (CRS, resolution, resampling method)
- Orchestrate the workflow
- Handle edge cases and errors

**Python Responsibilities:**
- Execute geospatial operations (GDAL/OGR)
- Process raster and vector data
- Generate visualizations
- Manage file I/O

**Result:**
- Reusable system across diverse datasets
- No custom scripting required for each analysis
- Accessible to scientists without deep GIS expertise

---

## Documentation

### For Scientists

**[`README.md`](../README.md)**
- Quick start guide
- Python API examples
- Repository structure

**[`TASKS.md`](../TASKS.md)**
- Plain-English description of the harmonization pipeline
- Tool-agnostic (applies to any GIS stack)

**[`examples/colorado_fire_risk/`](../examples/colorado_fire_risk/)**
- Complete working example
- Follow this pattern for new analyses

### For LLM Agents

**[`AGENTS.md`](../AGENTS.md)**
- Workflow rules and requirements
- Script structure and conventions
- Error handling guidelines
- Output requirements

### Website

**[`docs/`](../docs/)**
- MkDocs-based documentation site
- Tutorials, examples, and guides
- Run locally with `mkdocs serve`

---

## Example Use Case: Colorado Fire Risk

The reference example harmonizes four datasets to analyze fire risk patterns:

**Datasets:**
- Fire fuel models (categorical raster)
- Projected winter precipitation (continuous raster, climate model)
- Historical burned areas (vector polygons)
- Building footprints (vector polygons, rasterized)

**Target:**
- Region: Colorado
- CRS: EPSG:4326 (geographic)
- Resolution: ~270 m (0.00243°)
- Extent: `-109.05, 36.99, -102.04, 41.01`

**Output:**
- All datasets aligned to the same grid
- Visualization showing spatial patterns
- Ready for integrated analysis

**Goal:**
> Visualize fire behavior fuel models, projected winter precipitation, past burned areas, and human infrastructure together to understand fire risk patterns across Colorado.

---

## Repository Structure

```
LLM_lesson_exemplar/
├── src/                              # Core harmonization library (read-only)
│   ├── geospatial_harmonizer.py      # Main API
│   └── _gdal_utils.py                # GDAL helper functions
│
├── scripts/                          # Helper utilities
│   ├── check_urls.py                 # URL validation
│   ├── find_dataset.py               # Catalog search
│   └── region_extent.py              # Boundary lookup
│
├── examples/                         # Reference implementations (read-only)
│   └── colorado_fire_risk/           # Colorado fire risk example
│       ├── colorado_harmonization.py
│       └── output/
│
├── workflows/                        # User analyses (create new projects here)
│   ├── utah_fire_risk/               # Example user workflow
│   └── <your_project>/               # Your analysis goes here
│
├── docs/                             # MkDocs website source
│   ├── index.md
│   ├── start-here.md
│   ├── examples.md
│   └── workflows/
│
├── tests/                            # Test suite
│
├── AGENTS.md                         # LLM behavior rules
├── TASKS.md                          # Harmonization pipeline description
├── README.md                         # Main documentation
├── data_catalog.yml                  # Curated dataset catalog
└── requirements.txt                  # Python dependencies
```

---

## Getting Started

### Installation

```bash
pip install -r requirements.txt
```

### Run the Example

```bash
python examples/colorado_fire_risk/colorado_harmonization.py
```

### Create Your Own Workflow

1. Read the Colorado example to understand the pattern
2. Create a new folder in `workflows/<your_project>/`
3. Write a script following the template in [`AGENTS.md`](../AGENTS.md)
4. Set `output_dir=Path(__file__).parent / "output"`
5. Run with `nohup` for long-running processes

---

## Python API Example

```python
from pathlib import Path
from src.geospatial_harmonizer import (
    DatasetSpec,
    ExampleWorkflow,
    run_harmonization_example
)

workflow = ExampleWorkflow(
    name="my_analysis",
    datasets=[
        DatasetSpec(
            name="my_raster",
            url="https://example.com/data.tif",
            data_type="raster",
            resampling_method="bilinear",
        ),
        DatasetSpec(
            name="my_vector",
            url="https://example.com/data.zip",
            data_type="vector",
            rasterize=True,
        ),
    ],
    target_crs="EPSG:4326",
    target_extent=(-109.05, 36.99, -102.04, 41.01),
    target_resolution=0.00243,
    clip_boundary="state:Colorado",
    output_dir=Path("./output"),
    create_visualization=True,
    verbose=True,
)

output_files, interactive_map = run_harmonization_example(workflow)
```

---

## Key Features

### Intelligent Decision-Making
- LLM determines appropriate CRS for the region
- Selects resampling method based on data type
- Handles format variations automatically

### Robust Error Handling
- Validates URLs before processing
- Detects HTML portal pages vs. actual data
- Reports specific failures with actionable messages

### Reproducible Workflows
- All parameters documented
- Outputs include metadata
- Scripts can be re-run with same results

### Flexible Output
- Keep vectors as vectors or rasterize them
- Generate both static and interactive visualizations
- All outputs share common spatial reference

---

## Use Cases

This repository is designed for:

- **Scientists** learning AI-assisted geospatial workflows
- **Educators** teaching data harmonization concepts
- **Researchers** needing to combine diverse environmental datasets
- **Developers** building LLM-powered geospatial tools

---

## Technical Stack

- **Python 3.x**
- **GDAL/OGR** - Geospatial data processing
- **Rasterio** - Raster I/O and operations
- **GeoPandas** - Vector data handling
- **Matplotlib** - Static visualizations
- **Folium** - Interactive web maps
- **MkDocs** - Documentation site

---

## Summary

**LLM_lesson_exemplar** demonstrates a paradigm shift in geospatial analysis: instead of writing custom scripts for each dataset combination, we use LLMs to orchestrate reusable processing functions. This makes complex geospatial workflows more accessible to scientists while maintaining reproducibility and rigor.

The repository serves as both a teaching tool and a functional system for harmonizing environmental datasets, showing how AI can augment scientific workflows without replacing human expertise and judgment.
