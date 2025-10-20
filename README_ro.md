# Fisiere ROMGEO Grid

[🇬🇧 English](README.md) | [🇷🇴 Română](README_ro.md)

![Ultimul Grid](https://img.shields.io/badge/Ultimul_Grid-25.09-blue)

Acest repository conține gridurile de corecție ROMGEO utilizate pentru transformări geodezice precise.

---

## 📂 Structura
- `grids/YY.MM-alpha/` — Grid în stadiu alpha
- `grids/YY.MM-beta/` — Grid beta
- `grids/YY.MM/` — Grid lansate oficial
- `grids/pre-release/` — Grid ce urmeaza a fi publicat
- `grids/latest/` — Ultima versiune oficială

Fiecare versiune conține:
- `rom_grid3d_YY.MM.spg` — Fişier grid python pickle
- `rom_grid3d_YY.MM.json` — Fişier grid in format JSON
- `metadata.json` — Metadate descriptive

---

## 📄 Specificații Fisier SPG

Structura fișierului SPG este descrisă în detaliu [aici](spg_file_specs_ro.md).
