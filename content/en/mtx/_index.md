---
title: "mtx"
weight: 60
description: "Planned, wave 2: Matrix Market files."
---

<!-- From go-scikit/roadmap, bib/systems-units-formats-visualization.md, sections 1c, 2d, 4 and 5, PLAN.md items 2 and 9. Change it there first. -->

**Status: planned (wave 2). No code exists.** The package name is provisional.
go-sparse's wave 1 (item 2 of the plan) also lists Matrix Market I/O, so the
division between that work and this package is yet to be drawn.

## What it will provide

Matrix Market files in coordinate and array form, with real, complex, integer
and pattern fields and general, symmetric, skew-symmetric and Hermitian
symmetry.

## References

| Subject | Reference |
| --- | --- |
| the format | NIST, [The Matrix Market formats](https://math.nist.gov/MatrixMarket/formats.html) |

## How it will be validated

| Area | Criterion |
| --- | --- |
| round trip | Go writes and `scipy.io.mmread` reads, and the other way round, with identical matrices |
| hostile input | `go test -fuzz` for panics; a limit on the allocation a hostile header can ask for |

`scipy.io` (`mmread`, `mmwrite`) is the oracle. Corpus: the Matrix Market and
[SuiteSparse](https://sparse.tamu.edu/) collections. Every item also needs unit
tests at 100% coverage and a performance table against the reference.
