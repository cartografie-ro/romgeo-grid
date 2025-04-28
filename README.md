# ROMGEO Grid Files

![Latest Grid](https://img.shields.io/badge/Latest_Grid-25.04-blue)

![Latest Grid](https://img.shields.io/badge/Latest_Grid-$(curl -s https://raw.githubusercontent.com/YOUR_USER/YOUR_REPO/main/grids/latest/version.txt)-blue)

This repository contains the ROMGEO correction grids used for precise geodetic transformations.

---

## 📂 Structure
- `grids/YY.MM-alpha/` — Alpha stage grids
- `grids/YY.MM-beta/` — Beta stage grids (pre-release)
- `grids/YY.MM/` — Final released grids
- `grids/latest/` — Latest official released version

Each version contains:
- `grid_YY.MM.spg` — Binary grid file
- `metadata.json` — Descriptive metadata

---

## 🚀 Publishing Workflow

Publishing is manually triggered via GitHub Actions:
- `publish-alpha`: Promote an alpha version to beta.
- `publish-beta`: Promote a beta version to final release.
- `publish-latest`: Update the `latest/` pointer to the newest release.

---

## 📄 SPG File Specifications

The SPG file structure is described in detail [here](spg_file_specs.md).

### Quick Overview

#### Top-Level Structure:
- `params` (dictionary):
  - `geodetic_shifts_file` (str)
  - `geoid_heights_file` (str)
  - `version` (str)
  - `output_file` (str)
  - `helmert` (dictionary) — Helmert transformation parameters

- `grids` (dictionary):
  - `geodetic_shifts` (dictionary)
  - `geoid_heights` (dictionary)

- `metadata` (dictionary):
  - License, author, versioning, validity periods, etc.

Each grid contains:
- **Name**, **source**, **target**
- **Metadata** (dimensions, extents, resolution)
- **Grid Data** (NumPy array, float32 precision)

### Helmert Transform Example:
```text
helmert:
  os_st70:
    tE: (float)
    tN: (float)
    dm: (float)
    Rz: (float)
  st70_os:
    tE: (float)
    tN: (float)
    dm: (float)
    Rz: (float)
