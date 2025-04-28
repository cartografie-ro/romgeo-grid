# SPG File Specifications

This document describes the structure of `.spg` (Spatial Grid Package) files used in the ROMGEO project.

---

## Top-Level Structure

- **`params`** (`dict`): General parameters and transformations.
- **`grids`** (`dict`): Geodetic shifts and geoid heights grids.
- **`metadata`** (`dict`): Metadata and versioning information.

---

## `params` (dictionary)

General processing parameters:

- `geodetic_shifts_file` (`str`): Path to geodetic shifts grid.
- `geoid_heights_file` (`str`): Path to geoid heights grid.
- `version` (`str`): Version identifier.
- `output_file` (`str`): Output file path.
- `helmert` (`dict`): Helmert transformation parameters.

### Helmert Transformation Structure

```yaml
helmert:
  os_st70:
    tE: float
    tN: float
    dm: float
    Rz: float
  st70_os:
    tE: float
    tN: float
    dm: float
    Rz: float
```

---

## `grids` (dictionary)

Contains two grids:

- `geodetic_shifts`
- `geoid_heights`

Each grid contains:

- `name` (`str`): Grid name.
- `source` (`str`): Source reference frame.
- `target` (`str`): Target reference frame.
- `metadata` (`dict`): Grid metadata.
- `grid` (`ndarray`): NumPy array containing the grid data.

---

### Geodetic Shifts — Metadata

| Field   | Type   | Description           |
|---------|--------|-----------------------|
| `ndim`  | `int`  | Number of dimensions   |
| `mine`  | `float`| Minimum Easting        |
| `maxe`  | `float`| Maximum Easting        |
| `minn`  | `float`| Minimum Northing       |
| `maxn`  | `float`| Maximum Northing       |
| `stepe` | `float`| Step size Easting      |
| `stepn` | `float`| Step size Northing     |
| `crs_type` | `str` | Coordinate Reference System type |
| `ncols` | `int`  | Number of columns      |
| `nrows` | `int`  | Number of rows         |

**Array shape**: `(2, 53, 72)`, `dtype=float32`

---

### Geoid Heights — Metadata

| Field    | Type   | Description            |
|----------|--------|------------------------|
| `ndim`   | `int`  | Number of dimensions    |
| `minla`  | `float`| Minimum Latitude        |
| `maxla`  | `float`| Maximum Latitude        |
| `minphi` | `float`| Minimum Longitude       |
| `maxphi` | `float`| Maximum Longitude       |
| `stepla` | `float`| Step size Latitude      |
| `stepphi`| `float`| Step size Longitude     |
| `crs_type` | `str` | Coordinate Reference System type |
| `ncols`  | `int`  | Number of columns       |
| `nrows`  | `int`  | Number of rows          |

**Array shape**: `(1, 160, 320)`, `dtype=float32`

---

## `metadata` (dictionary)

General file metadata:

- `file` (`str`): Filename.
- `license` (`str`): Licensing information.
- `created_by` (`str`): Author or organization.
- `attribution` (`str`): Attribution text.
- `abstract` (`str`): Abstract or description.
- `release` (`dict`): Release version info.
- `release_date` (`str`): Official release date.
- `valid_from` (`str`): Grid validity start date.
- `valid_to` (`str`): Grid validity end date.

### Release Structure

```yaml
release:
  major: int
  minor: int
  revision: int
  legacy: str
```

---

## Summary

Each `.spg` file contains:

- Helmert transformation details
- Two spatial grids (`geodetic_shifts` and `geoid_heights`)
- Complete metadata including license, attribution, and versioning
- Data stored as efficient NumPy arrays

---

## Example Grid Metadata Snippet

```json
{
  "name": "Geodetic Shifts",
  "source": "ETRS89",
  "target": "Black Sea 1975",
  "metadata": {
    "ndim": 2,
    "mine": 200000.0,
    "maxe": 800000.0,
    "minn": 400000.0,
    "maxn": 900000.0,
    "stepe": 1000.0,
    "stepn": 1000.0,
    "crs_type": "projected",
    "ncols": 600,
    "nrows": 500
  }
}
```
