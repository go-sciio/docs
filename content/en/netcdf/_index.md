---
title: "netcdf"
weight: 30
description: "Planned, wave 2: NetCDF classic and NetCDF-4."
---

<!-- From go-scikit/roadmap, bib/systems-units-formats-visualization.md, sections 1c, 2d, 3c, 4 and 5, and PLAN.md item 9. Change it there first. -->

**Status: planned (wave 2). No code exists.** The package name is provisional.

## What it will provide

- NetCDF classic in its three variants (CDF-1, CDF-2 with 64-bit offsets and
  CDF-5): big-endian, with a record dimension.
- NetCDF-4: HDF5 with dimension scales, the "classic model" subset, on top of
  `h5`.
- The CF conventions' `units` attribute, which is in the UDUNITS syntax; the
  planned `units` package of go-units parses it.

## References

| Subject | Reference |
| --- | --- |
| the formats | Unidata, [NetCDF File Format Specification](https://docs.unidata.ucar.edu/netcdf-c/current/file_format_specifications.html) |
| conventions | the [CF conventions](https://cfconventions.org/) |

## How it will be validated

| Area | Criterion |
| --- | --- |
| reading | exact equality of the values read against the oracle |
| round trip | Go writes and netcdf-c reads, and the other way round, with identical arrays |
| hostile input | `go test -fuzz` for panics; a limit on the allocation a hostile header can ask for |

Oracle: Unidata's [netcdf-c](https://github.com/Unidata/netcdf-c) and its
`ncdump`. Its test files are the corpus. Every item also needs unit tests at
100% coverage and a performance table against the reference.
