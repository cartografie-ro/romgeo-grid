# Fisiere ROMGEO Grid

[🇬🇧 English](README.md) | [🇷🇴 Română](README_ro.md)

![Ultimul Grid](https://img.shields.io/badge/Ultimul_Grid-25.04-blue)

Acest repository conține grilele de corecție ROMGEO utilizate pentru transformări geodezice precise.

---

## 📂 Structura
- `grids/YY.MM-alpha/` — Grile în stadiu alpha
- `grids/YY.MM-beta/` — Grile pre-lansare (beta)
- `grids/YY.MM/` — Grile lansate oficial
- `grids/latest/` — Ultima versiune oficială

Fiecare versiune conține:
- `grid_YY.MM.spg` — Fişier grid binar
- `metadata.json` — Metadate descriptive

---

## 🚀 Flux de Publicare

Publicarea se declanșează manual prin GitHub Actions:
- `publish-alpha`: Promovează o versiune alpha la beta.
- `publish-beta`: Promovează o versiune beta la lansare oficială.
- `publish-latest`: Actualizează linkul `latest/` către ultima versiune.

---

## 📄 Specificații Fisier SPG

Structura fișierului SPG este descrisă în detaliu [aici](spg_file_specs_ro.md).
