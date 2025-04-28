# Specificații Fișier SPG

[🇬🇧 English](spg_file_specs.md) | [🇷🇴 Română](spg_file_specs_ro.md)

Acest document descrie structura fișierelor `.spg` (Pachet de Grilă Spațială) utilizate în proiectul ROMGEO.

---

## Structura Principală

- **`params`** (`dict`): Parametri generali și transformări.
- **`grids`** (`dict`): Grile de deplasare geodezică și de înălțime geoidică.
- **`metadata`** (`dict`): Metadate și informații despre versiune.

---

## `params` (dicționar)

Parametri generali de procesare:

- `geodetic_shifts_file` (`str`): Calea către grila de deplasare geodezică.
- `geoid_heights_file` (`str`): Calea către grila de înălțime geoidică.
- `version` (`str`): Identificator de versiune.
- `output_file` (`str`): Calea fișierului de ieșire.
- `helmert` (`dict`): Parametrii transformării Helmert.# Specificații Fișier SPG

[🇬🇧 English](spg_file_specs.md) | [🇷🇴 Română](spg_file_specs_ro.md)

Acest document descrie structura fișierelor `.spg` (Pachet de Grilă Spațială) utilizate în proiectul ROMGEO.

---

## Structura Principală

- **`params`** (`dict`): Parametri generali și transformări.
- **`grids`** (`dict`): Grile de deplasare geodezică și de înălțime geoidică.
- **`metadata`** (`dict`): Metadate și informații despre versiune.

---

## `params` (dicționar)

Parametri generali de procesare:

- `geodetic_shifts_file` (`str`): Calea către grila de deplasare geodezică.
- `geoid_heights_file` (`str`): Calea către grila de înălțime geoidică.
- `version` (`str`): Identificator de versiune.
- `output_file` (`str`): Calea fișierului de ieșire.
- `helmert` (`dict`): Parametrii transformării Helmert.

### Structura Transformării Helmert

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

## `grids` (dicționar)

Conține două grile:

- `geodetic_shifts`
- `geoid_heights`

Fiecare grilă conține:

- `name` (`str`): Numele grilei.
- `source` (`str`): Sistemul de referință sursă.
- `target` (`str`): Sistemul de referință țintă.
- `metadata` (`dict`): Metadate ale grilei.
- `grid` (`ndarray`): Matrice NumPy care conține datele grilei.

---

### Deplasări Geodezice — Metadate

| Câmp     | Tip    | Descriere                   |
|----------|--------|------------------------------|
| `ndim`   | `int`  | Număr de dimensiuni           |
| `mine`   | `float`| Est minim                     |
| `maxe`   | `float`| Est maxim                     |
| `minn`   | `float`| Nord minim                    |
| `maxn`   | `float`| Nord maxim                    |
| `stepe`  | `float`| Pas Est                       |
| `stepn`  | `float`| Pas Nord                      |
| `crs_type` | `str` | Tip sistem de coordonate      |
| `ncols`  | `int`  | Număr de coloane              |
| `nrows`  | `int`  | Număr de rânduri              |

**Formă matrice**: `(2, 53, 72)`, `dtype=float32`

---

### Înălțimi Geoidice — Metadate

| Câmp      | Tip    | Descriere                   |
|-----------|--------|------------------------------|
| `ndim`    | `int`  | Număr de dimensiuni           |
| `minla`   | `float`| Latitudine minimă             |
| `maxla`   | `float`| Latitudine maximă             |
| `minphi`  | `float`| Longitudine minimă            |
| `maxphi`  | `float`| Longitudine maximă            |
| `stepla`  | `float`| Pas Latitudine                |
| `stepphi` | `float`| Pas Longitudine               |
| `crs_type`| `str`  | Tip sistem de coordonate      |
| `ncols`   | `int`  | Număr de coloane              |
| `nrows`   | `int`  | Număr de rânduri              |

**Formă matrice**: `(1, 160, 320)`, `dtype=float32`

---

## `metadata` (dicționar)

Metadate generale ale fișierului:

- `file` (`str`): Numele fișierului.
- `license` (`str`): Informații despre licență.
- `created_by` (`str`): Autor sau organizație.
- `attribution` (`str`): Text de atribuire.
- `abstract` (`str`): Rezumat sau descriere.
- `release` (`dict`): Informații despre versiune.
- `release_date` (`str`): Data lansării oficiale.
- `valid_from` (`str`): Data de început a valabilității.
- `valid_to` (`str`): Data de sfârșit a valabilității.

### Structura Versiunii

```yaml
release:
  major: int
  minor: int
  revision: int
  legacy: str
```

---

## Sumar

Fiecare fișier `.spg` conține:

- Detalii despre transformarea Helmert
- Două grile spațiale (`geodetic_shifts` și `geoid_heights`)
- Metadate complete, inclusiv licență, atribuire și versiune
- Date stocate sub formă de matrice NumPy eficiente

---

## Exemplu Metadate Grilă

```json
{
  "name": "Geodetic Shifts",
  "source": "ETRS89",
  "target": "Marea Neagră 1975",
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



### Structura Transformării Helmert

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

## `grids` (dicționar)

Conține două grile:

- `geodetic_shifts`
- `geoid_heights`

Fiecare grilă conține:

- `name` (`str`): Numele grilei.
- `source` (`str`): Sistemul de referință sursă.
- `target` (`str`): Sistemul de referință țintă.
- `metadata` (`dict`): Metadate ale grilei.
- `grid` (`ndarray`): Matrice NumPy care conține datele grilei.

---

### Deplasări Geodezice — Metadate

| Câmp     | Tip    | Descriere                   |
|----------|--------|------------------------------|
| `ndim`   | `int`  | Număr de dimensiuni           |
| `mine`   | `float`| Est minim                     |
| `maxe`   | `float`| Est maxim                     |
| `minn`   | `float`| Nord minim                    |
| `maxn`   | `float`| Nord maxim                    |
| `stepe`  | `float`| Pas Est                       |
| `stepn`  | `float`| Pas Nord                      |
| `crs_type` | `str` | Tip sistem de coordonate      |
| `ncols`  | `int`  | Număr de coloane              |
| `nrows`  | `int`  | Număr de rânduri              |

**Formă matrice**: `(2, 53, 72)`, `dtype=float32`

---

### Înălțimi Geoidice — Metadate

| Câmp      | Tip    | Descriere                   |
|-----------|--------|------------------------------|
| `ndim`    | `int`  | Număr de dimensiuni           |
| `minla`   | `float`| Latitudine minimă             |
| `maxla`   | `float`| Latitudine maximă             |
| `minphi`  | `float`| Longitudine minimă            |
| `maxphi`  | `float`| Longitudine maximă            |
| `stepla`  | `float`| Pas Latitudine                |
| `stepphi` | `float`| Pas Longitudine               |
| `crs_type`| `str`  | Tip sistem de coordonate      |
| `ncols`   | `int`  | Număr de coloane              |
| `nrows`   | `int`  | Număr de rânduri              |

**Formă matrice**: `(1, 160, 320)`, `dtype=float32`

---

## `metadata` (dicționar)

Metadate generale ale fișierului:

- `file` (`str`): Numele fișierului.
- `license` (`str`): Informații despre licență.
- `created_by` (`str`): Autor sau organizație.
- `attribution` (`str`): Text de atribuire.
- `abstract` (`str`): Rezumat sau descriere.
- `release` (`dict`): Informații despre versiune.
- `release_date` (`str`): Data lansării oficiale.
- `valid_from` (`str`): Data de început a valabilității.
- `valid_to` (`str`): Data de sfârșit a valabilității.

### Structura Versiunii

```yaml
release:
  major: int
  minor: int
  revision: int
  legacy: str
```

---

## Sumar

Fiecare fișier `.spg` conține:

- Detalii despre transformarea Helmert
- Două grile spațiale (`geodetic_shifts` și `geoid_heights`)
- Metadate complete, inclusiv licență, atribuire și versiune
- Date stocate sub formă de matrice NumPy eficiente

---

## Exemplu Metadate Grilă

```json
{
  "name": "Geodetic Shifts",
  "source": "ETRS89",
  "target": "Marea Neagră 1975",
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
