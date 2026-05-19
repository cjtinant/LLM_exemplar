# Black Hills Hydrology Plan — Change Log

## 2026-05-15T01:30:00Z — Add USGS TopoMine Symbols Dataset

**Prompt**: "could we add other mine locations?" → User selected "Add USGS TopoMine Symbols (usmin-SD) — best for comprehensive historical mining coverage (gold, silver, copper, uranium, prospects)"

**Model**: nrp/qwen3-small (Code mode)

### Changes to `plans/black_hills_hydrology_plan.md`

| Section | Change |
|---------|--------|
| **Dataset #7** (new) | Added USGS TopoMine Symbols — National Shapefiles (ver. 10.0) with URL `https://www.sciencebase.gov/catalog/file/get/5a1492c3e4b09fc93dcfd574?name=USGS_TopoMineSymbols_ver10_Shapefiles.zip` |
| **Dataset #7 Notes** | Documented filtering strategy: use `Ftr_Type` attribute to include metallic mining features (Adit, Mine Shaft, Prospect Pit, Open Pit Mine, Tailings, Uranium Mine) while excluding generic "Gravel Pit" and "Borrow Pit" |
| **Vector Outputs (Mining)** | Added `harmonized_usmin_mines.geojson` — USGS TopoMine symbols (all mine types) |
| **Vector Outputs (Mining)** | Updated buffer zone descriptions to reference "all mines" (merged layer) |
| **Step 1: Validate URLs** | Added TopoMine national shapefile URL to `check_urls.py` command |
| **Mining Impact Assessment** | Updated to map all mine locations (EPA uranium + USGS TopoMine), distinguish mine types, analyze historical mining legacy from 1886–2006 timeline |
| **Visualization Examples** | Updated multi-panel map, interactive map, and mining impact map descriptions to include all mine types with color-coding by commodity |
| **Phase 5: Mining Data** | Added steps for TopoMine filtering, merging with EPA uranium, then buffer zone creation |
| **Summary of Confirmed Specifications** | Updated Key Additions to include "comprehensive historical mining features (USGS TopoMine)" |

### Changes to `data_catalog.yml`

| Entry | Details |
|-------|---------|
| **USGS TopoMine Symbols — National Shapefiles (ver. 10.0)** | New catalog entry at line 142: type=vector, source=USGS Mineral Resources Program, topics=[hazards, mining, historical], notes include filtering guidance and documentation link |

### URL Validation

| URL | Status |
|-----|--------|
| `https://mrdata.usgs.gov/usmin/download/usmin-SD.zip` (per-state) | ❌ 404 — Per-state download links no longer work |
| `https://www.sciencebase.gov/catalog/file/get/5a1492c3e4b09fc93dcfd574?name=USGS_TopoMineSymbols_ver10_Shapefiles.zip` (national) | ✅ 200 — 253.4 MB, contains state-specific shapefiles inside |

### Key Decisions

1. **National dataset over per-state**: Per-state URLs return 404; national archive (253 MB) is the only working direct download. Workflow will extract South Dakota shapefiles from the archive.
2. **Filtering strategy**: `Ftr_Type` attribute will be used to exclude generic features ("Gravel Pit", "Borrow Pit") and retain metallic mining features for environmental impact assessment.
3. **Merged mine layer**: EPA uranium + filtered TopoMine will be combined into a unified layer before buffer zone creation, with source attribution preserved.
