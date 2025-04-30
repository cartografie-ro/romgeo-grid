# ROMGEO Grid Files

[🇬🇧 English](README.md) | [🇷🇴 Română](README_ro.md)

![Latest Grid](https://img.shields.io/badge/Latest_Grid-25.04-blue)

This repository contains the ROMGEO correction grids used for precise geodetic transformations.

---

## 📂 Structure
- `grids/YY.MM-alpha/` — Alpha stage grids
- `grids/YY.MM-beta/` — Beta stage grids
- `grids/YY.MM/` — Final released grids
- `grids/pre-release/` — Next in line grid to be released
- `grids/latest/` — Latest official released version

Each version contains:
- `rom_grid3d_YY.MM.spg` — Binary grid file
- `metadata.json` — Descriptive metadata

---

## 📄 SPG File Specifications

The SPG file structure is described in detail [here](spg_file_specs.md).
