# ROMGEO Grid Files

[🇬🇧 English](README.md) | [🇷🇴 Română](README_ro.md)

![Latest Grid](https://img.shields.io/badge/Latest_Grid-25.04-blue)

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
