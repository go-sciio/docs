---
title: "go-sciio documentation"
linkTitle: "Home"
type: docs
cascade:
  type: docs
description: "Scientific file formats in pure Go (CGO=0): HDF5, MAT, NetCDF, FITS, npy, Matrix Market, WAV and FLAC. Planned, wave 2 of the go-scikit roadmap: no library exists yet."
---

**go-sciio is planned.** It is the organisation the
[go-scikit parity plan](https://github.com/go-scikit/roadmap/blob/main/PLAN.md)
names for what MATLAB's file functions and Mathematica's `Import` read and
write. No library exists, no code is written and nothing is released: these
pages say what the organisation will cover, in which wave, and what each format
will be validated against.

## Scope

HDF5, MAT-files (v4, v5, v7 and v7.3), NetCDF (classic and NetCDF-4), FITS, NumPy
`.npy` and `.npz`, Matrix Market, WAV and FLAC. CSV, Parquet and Arrow already
exist in go-dataframe, and the bridge from xlsx to a dataframe belongs in
go-dataframe and go-ooxml, not here.

## Plan

| Item in the plan | What | Wave |
| --- | --- | --- |
| 9 | go-sciio: HDF5, then MAT v7.3 on it; NetCDF, FITS, npy (size XL), together with go-units | 2 |

The plan is [PLAN.md](https://github.com/go-scikit/roadmap/blob/main/PLAN.md);
where each item stands is [STATUS.md](https://github.com/go-scikit/roadmap/blob/main/STATUS.md).
The facts behind the scope, the references and the validation measures are in
the roadmap's
[bibliography](https://github.com/go-scikit/roadmap/blob/main/bib/systems-units-formats-visualization.md).
go-sparse's wave 1 already lists Matrix Market I/O, so the line between that
work and `mtx` is yet to be drawn.

## The planned packages

The names are provisional.

| Package | Status | Format |
| --- | --- | --- |
| [h5]({{< relref "h5" >}}) | planned (wave 2) | HDF5 |
| [mat]({{< relref "mat" >}}) | planned (wave 2) | MAT-files v4, v5, v7, v7.3 |
| [netcdf]({{< relref "netcdf" >}}) | planned (wave 2) | NetCDF classic and NetCDF-4 |
| [fits]({{< relref "fits" >}}) | planned (wave 2) | FITS |
| [npy]({{< relref "npy" >}}) | planned (wave 2) | NumPy `.npy` and `.npz` |
| [mtx]({{< relref "mtx" >}}) | planned (wave 2) | Matrix Market |
| [wav]({{< relref "wav" >}}) | planned (wave 2) | WAV |
| [flac]({{< relref "flac" >}}) | planned (wave 2) | FLAC |

## Status

Nothing is released, so there is nothing to install. When a package is released
its page becomes the package's own documentation, and this site's version label
follows the newest release, as in the other go-scikit organisations.
