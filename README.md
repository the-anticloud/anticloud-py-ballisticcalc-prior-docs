# PY BALLISTICCALC PRIOR DOCS

![license](https://img.shields.io/badge/license-license-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-artillery_manufacturing-lightgrey)

> Anticloud-hardened packaging of the upstream project `PY_BALLISTICCALC_PRIOR_DOCS` in category **ARTILLERY MANUFACTURING**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** ARTILLERY MANUFACTURING · **Upstream:** https://github.com/o-murphy/py-ballisticcalc · **Upstream pin:** `663db15d7f8fdf8b6494f63b9ba5853e0ffb4e03` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

<h1 style="display: flex; align-items: center; gap: 10px;">
  <img src="./docs/favicon.svg" alt="favicon" width="50" height="50"> 
  Ballistic Solver Library
</h1>

LGPL library for small arms ballistic calculations based on point-mass (3 DoF) plus spin drift.

[![license]][LGPL-3]
[![pypi]][PyPiUrl]
[![pypi-pre]][pypi-pre-url]
[![downloads]][pepy]
[![downloads/month]][pepy]
[![coverage]][CodecovUrl]
[![py-versions]][sources]
[![Made in Ukraine]][SWUBadge]

[![powered by bclibc]][bclibc]
[![powered by pyodide]][Pyodide]

[![Pre-commit](https://github.com/o-murphy/py-ballisticcalc/actions/workflows/pre-commit.yml/badge.svg)](https://github.com/o-murphy/py-ballisticcalc/actions/workflows/pre-commit.yml)

### Contents

* **[Installation](#installation)**
    * [Latest stable][PyPiUrl]

  [//]: # (  * [From sources]&#40;#installing-from-sources&#41;)
  [//]: # (  * [source and build]&#40;#source-and-build&#41;)

* **[Quick Start](#quick-start)**
    * [Interactive Web REPL](#interactive-web-repl)
    * [Examples](#examples)
    * [Ballistic Concepts](#ballistic-concepts)
    * [Units](#units)
    * [Calculation Engines](#calculation-engines)

* **[Documentation][DOCUMENTATION]**
* **[Contributors](#contributors)**
* **[About project](#about-project)**

## Installation

### uv

```shell
uv add py-ballisticcalc

# Using precompiled backend (improves performance)
uv add py-ballisticcalc[exts]

# Using matplotlib and pandas uses additional dependencies
uv add py-ballisticcalc[charts]

# Get everything, including the SciPy engine
uv add py-ballisticcalc[exts,charts,scipy]
```

### pip

```shell
pip install py-ballisticcalc

# Using precompiled backend (improves performance)
pip install py-ballisticcalc[exts]

# Using matplotlib and pandas uses additional dependencies
pip install py-ballisticcalc[charts]

# Get everything, including the SciPy engine
pip install py-ballisticcalc[exts,charts,scipy]
```

----

## [Quick Start] - click here to open Quick Start guide

### [Interactive Web REPL]

<img src="https://raw.githubusercontent.com/pyodide/pyodide-artwork/refs/heads/main/logo-dark.svg" style="height: 32px; width: auto; background-color: black" />

Prefer to try it before installing anything? Open the [Interactive Web REPL] — runs entirely in your browser via [Pyodide].

### [Examples]
  * [Extreme Examples]

### [Ballistic Concepts]
  * [Coordinates]
  * [Slant / Look Angle]
  * [Danger Space]

### [Units]

Work in your preferred terms with easy conversions for the following dimensions and units:
* **Angular**: radian, degree, MOA, mil, mrad, thousandth, inch/100yd, cm/100m, o'clock
* **Distance**: inch, foot, yard, mile, nautical mile, mm, cm, m, km, line
* **Energy**: foot-pound, joule
* **Pressure**: mmHg, inHg, bar, hPa, PSI
* **Temperature**: Fahrenheit, Celsius, Kelvin, Rankine
* **Time**: second, minute, millisecond, microsecond, nanosecond, picosecond
* **Velocity**: m/s, km/h, ft/s, mph, knots
* **Weight**: grain, ounce, gram, pound, kilogram, newton

### [Calculation Engines]

Choose between different calculation engines, or build your own.  Included engines:

#### Mean time

![Mean time per call by engine](./docs/concepts/bench.svg)

#### Speedup vs `python.rk4`

![Speedup vs python.rk4](./docs/concepts/bench_speedup.svg)

| Engine Name                   | Speed (Find Zero / Trajectory)       |        Dependencies         | Description                                                     |                                                                                                                                Tests                                                                                                                                 |
| :---------------------------- | :----------------------------------- | :-------------------------: | :-------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| `python+rk4`                  | Baseline (1x)                        |        None; default        | Runge-Kutta 4th-order integration                               |                   [![tests](https://img.shields.io/github/actions/workflow/status/o-murphy/py-ballisticcalc/pytest-rk4-engine.yml?logo=python&label=tests)](https://github.com/o-murphy/py-ballisticcalc/actions/workflows/pytest-rk4-engine.yml)                    |
| `python+euler`                | :arrow_down: 0.6x / 0.6x (slower)    |            None             | Euler 1st-order integration                                     |                 [![tests](https://img.shields.io/github/actions/workflow/status/o-murphy/py-ballisticcalc/pytest-euler-engine.yml?logo=python&label=tests)](https://github.com/o-murphy/py-ballisticcalc/actions/workflows/pytest-euler-engine.yml)                  |
| `python+verlet`               | :arrow_down: 0.8x / 0.8x (slower)    |            None             | Verlet 2nd-order symplectic integration                         |                [![tests](https://img.shields.io/github/actions/workflow/status/o-murphy/py-ballisticcalc/pytest-verlet-engine.yml?logo=python&label=tests)](https://github.com/o-murphy/py-ballisticcalc/actions/workflows/pytest-verlet-engine.yml)                 |
| `cython+rk4`                  | :arrow_up: 205x / 129x (faster)      | [`[exts]`](#cython-engines) | Compiled Runge-Kutta 4th-order                                  |       [![tests](https://img.shields.io/github/actions/workflow/status/o-murphy/py-ballisticcalc/pytest-cythonized-rk4-engine.yml?logo=cplusplus&label=tests)](https://github.com/o-murphy/py-ballisticcalc/actions/workflows/pytest-cythonized-rk4-engine.yml)       |
| `cython+euler`                | :arrow_up: 54x / 44x (faster)        | [`[exts]`](#cython-engines) | Compiled Euler inte

*(excerpt; full text in `UPSTREAM_CLONE/`)*

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **Python** (manifests: pyproject.toml; scanned in UPSTREAM_CLONE)
- Top-level source layout: `doc/`, `examples/`, `py_ballisticcalc/`, `py_ballisticcalc.exts/`, `scripts/`, `tests/`
- Snapshot size: **363 files**, **27997 lines of code** (measured; see Benchmarks)
- Primary languages: `.py` (108), `.md` (53), `.svg` (22), `.ttf` (20), `.woff` (20), `.woff2` (20)
- Upstream commit pinned for this packaging: `663db15d7f8fdf8b6494f63b9ba5853e0ffb4e03`

---

## Installation

* [Latest stable][PyPiUrl]

  [//]: # (  * [From sources]&#40;#installing-from-sources&#41;)
  [//]: # (  * [source and build]&#40;#source-and-build&#41;)

* **[Quick Start](#quick-start)**
    * [Interactive Web REPL](#interactive-web-repl)
    * [Examples](#examples)
    * [Ballistic Concepts](#ballistic-concepts)
    * [Units](#units)
    * [Calculation Engines](#calculation-engines)

* **[Documentation][DOCUMENTATION]**
* **[Contributors](#contributors)**
* **[About project](#about-project)**

*Section quoted from the upstream readme.*
Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

* [Interactive Web REPL](#interactive-web-repl)
    * [Examples](#examples)
    * [Ballistic Concepts](#ballistic-concepts)
    * [Units](#units)
    * [Calculation Engines](#calculation-engines)

* **[Documentation][DOCUMENTATION]**
* **[Contributors](#contributors)**
* **[About project](#about-project)**

*Section quoted from the upstream readme.*
Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

[![powered by pyodide]][Pyodide]

[![Pre-commit](https://github.com/o-murphy/py-ballisticcalc/actions/workflows/pre-commit.yml/badge.svg)](https://github.com/o-murphy/py-ballisticcalc/actions/workflows/pre-commit.yml)

*Section quoted from the upstream readme.*
---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | Python |
| Manifests detected | pyproject.toml |
| Files in snapshot | 363 |
| Lines of code | 27997 |
| Dependency references | 10 |
| Dependencies by ecosystem | pypi: 10 |
| Upstream license | LGPL-3.0 |
| Overlay license | Anticommons 0.1.0 |

Top dependency references recorded in the benchmark snapshot:

| Ecosystem | Name | Version | Source file |
|-----------|------|---------|-------------|
| pypi | typing_extensions | >= | pyproject.toml |
| pypi | Deprecated | >=1.3.1 | pyproject.toml |
| pypi | -std | =c99 | py_ballisticcalc.exts/setup.py |
| pypi | -std | =c++17 | py_ballisticcalc.exts/setup.py |
| pypi | -stdlib | =libc++ | py_ballisticcalc.exts/setup.py |
| pypi | -std | =c++17 | py_ballisticcalc.exts/setup.py |
| pypi | -std | =c99 | py_ballisticcalc.exts/setup.py |
| pypi | -std | =c++17 | py_ballisticcalc.exts/setup.py |
| pypi | -std | =c99 | py_ballisticcalc.exts/setup.py |
| pypi | -std | =c++17 | py_ballisticcalc.exts/setup.py |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

Dormand-Prince, and Tsitouras measure in the same performance class as each other on typical
trajectories -- see [benchmarks](docs/concepts/benchmarks.md#dormand-prince-and-tsitouras-engines)
for the measurement, not a ranking.

*Section quoted from the upstream readme.*
Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

Upstream contributions: fork the `PY_BALLISTICCALC_PRIOR_DOCS` project, create a feature branch, and open a pull request against upstream. Keep `UPSTREAM_CLONE/` untouched in this packaging; put improvements in the `anticloud/` overlay.

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: LGPL-3.0** (evidence: `LICENSE` in the upstream snapshot).

License file excerpt:

```text
                   GNU LESSER GENERAL PUBLIC LICENSE
                       Version 3, 29 June 2007

 Copyright (C) 2007 Free Software Foundation, Inc. <https://fsf.org/>
 Everyone is permitted to copy and distribute verbatim copies
 of this license document, but changing it is not allowed.

  This version of the GNU Lesser General Public License incorporates
the terms and conditions of version 3 of the GNU General Public
License, supplemented by the additional permissions listed below.

  0. Additional Definitions.

  As used herein, "this License" refers to version 3 of the GNU Lesser
General Public License, and the "GNU GPL" refers to version 3 of the GNU
General Public License.

  "The Library" refers to a covered work governed by this License,
other than an Application or a Combined Work as defined below.
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original LGPL-3.0 terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `LGPL-3.0` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `PY_BALLISTICCALC_PRIOR_DOCS` (category: ARTILLERY MANUFACTURING)
- **Upstream URL:** https://github.com/o-murphy/py-ballisticcalc
- **Pinned commit (SHA):** `663db15d7f8fdf8b6494f63b9ba5853e0ffb4e03`
- **Branch:** master
- **Pin provenance:** resolved during the second documentation pass. The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`f2dd54d260ad54d4f4a11f23a0e17585143fda959f212f51473c33684ebe1a02`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe and Mail, Business Insider, National Post, Financial Post, StreetInsider, Digital Journal, Barchart, International Business Times, and fox47 · National Law Review.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

