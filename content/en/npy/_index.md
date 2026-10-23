---
title: "npy"
weight: 50
description: "Planned, wave 2: NumPy .npy and .npz files."
---

<!-- From go-scikit/roadmap, bib/systems-units-formats-visualization.md, sections 1c, 2d, 3c, 4 and 5, and PLAN.md item 9. Change it there first. -->

**Status: planned (wave 2). No code exists.** The package name is provisional.

## What it will provide

NumPy's `.npy` format (a header dictionary, little- or big-endian data, Fortran
order) and `.npz` archives of several arrays. A small format, in the roadmap's
words.

## References

| Subject | Reference |
| --- | --- |
| the format | NumPy, [NEP 1, the `.npy` format](https://numpy.org/neps/nep-0001-npy-format.html) |

## How it will be validated

| Area | Criterion |
| --- | --- |
| round trip | Go writes and NumPy reads, and the other way round, with identical arrays |
| hostile input | `go test -fuzz` for panics; a limit on the allocation a hostile header can ask for |

NumPy is the oracle. Every item also needs unit tests at 100% coverage and a
performance table against the reference.
