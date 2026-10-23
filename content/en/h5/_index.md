---
title: "h5"
weight: 10
description: "Planned, wave 2: an HDF5 reader and writer."
---

<!-- From go-scikit/roadmap, bib/systems-units-formats-visualization.md, sections 1c, 2d, 3c, 4, 5 and 6, and PLAN.md item 9. Change it there first. -->

**Status: planned (wave 2, the first item of go-sciio). No code exists.** The
package name is provisional (`go-hdf5` belongs to a third party and is not
available).

## What it will provide

An HDF5 reader and writer: superblock versions 0 to 3, object headers v1 and v2,
B-trees v1 and v2, the fractal heap, the local heap, chunked layout, the deflate,
shuffle and fletcher32 filters, and the global heap for variable-length data.
`mat` (v7.3) and `netcdf` (NetCDF-4) are built on it and inherit its bugs.

Whether to audit and wrap an existing pure-Go package (`scigolib/hdf5`, MIT,
young, partial write support) or to write the package here is **undecided**; it
couples the whole organisation to one choice. Any audit includes hostile-input
limits: allocation caps and recursion depth.

## References

| Subject | Reference |
| --- | --- |
| the format | HDF Group, [HDF5 File Format Specification, version 3.0](https://support.hdfgroup.org/documentation/hdf5/latest/_f_m_t3.html) |

## How it will be validated

| Area | Criterion |
| --- | --- |
| reading | exact equality of integers, strings and raw floats against the reference reader |
| round trip | Go writes and h5py reads, and the arrays are identical; Go reads files that h5py wrote |
| hostile input | `go test -fuzz` for panics; a limit on the allocation a hostile header can ask for |

Oracles: h5py, `h5dump` and `h5ls` from the HDF Group, whose C library is the
reference reader. Corpus: the HDF Group's
[example files](https://support.hdfgroup.org/documentation/hdf5/latest/_examples.html)
and h5py's test files. Every item also needs unit tests at 100% coverage and a
performance table against the reference.
