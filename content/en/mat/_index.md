---
title: "mat"
weight: 20
description: "Planned, wave 2: MAT-files v4, v5, v7 and v7.3."
---

<!-- From go-scikit/roadmap, bib/systems-units-formats-visualization.md, sections 1c, 2d, 3c, 4 and 5, and PLAN.md item 9. Change it there first. -->

**Status: planned (wave 2). No code exists.** The package name is provisional.

## What it will provide

- MAT v4: a 20-byte header per matrix.
- MAT v5 and v7: a 128-byte header and tagged data elements, with zlib
  compression (`miCOMPRESSED`) in v7.
- MAT v7.3: an HDF5 file with a 512-byte user block, the `MATLAB_class`
  attribute, complex numbers as compound types and sparse matrices as groups,
  written and read on top of `h5`.

## References

| Subject | Reference |
| --- | --- |
| v4, v5, v7, v7.3 | MathWorks, [MAT-File Format](https://www.mathworks.com/help/pdf_doc/matlab/matfile_format.pdf) |

## How it will be validated

| Area | Criterion |
| --- | --- |
| reading | exact equality of the values read against the oracle |
| round trip | Go writes and SciPy (v4 to v7) or h5py (v7.3) reads, with identical arrays; Go reads their files |
| hostile input | `go test -fuzz` for panics; a limit on the allocation a hostile header can ask for |

`scipy.io` (`loadmat`, `savemat`) is the oracle for v4, v5 and v7, and does not
support v7.3. Corpus: SciPy's `scipy/io/matlab/tests/data` (BSD-3-Clause). Every
item also needs unit tests at 100% coverage and a performance table against the
reference.
