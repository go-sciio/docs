---
title: "fits"
weight: 40
description: "Planned, wave 2: FITS images, binary tables and compressed images."
---

<!-- From go-scikit/roadmap, bib/systems-units-formats-visualization.md, sections 1c, 2d, 3c, 4, 5 and 6, and PLAN.md item 9. Change it there first. -->

**Status: planned (wave 2). No code exists.** The package name is provisional.

## What it will provide

FITS 4.0: 2880-byte blocks of 80-character cards, big-endian data, images, binary
tables, and compressed images (Rice, GZIP and HCOMPRESS).

Whether to fork or to audit an existing package is open. `astrogo/fitsio`
(BSD-3-Clause) is archived on GitHub, and a fork would keep its notice.

## References

| Subject | Reference |
| --- | --- |
| the format | IAU FITS Working Group, [FITS Standard 4.0](https://fits.gsfc.nasa.gov/fits_standard.html), 2018 |

## How it will be validated

| Area | Criterion |
| --- | --- |
| reading | exact equality of the values read against the oracle |
| round trip | Go writes and astropy reads, and the other way round, with identical arrays |
| hostile input | `go test -fuzz` for panics; a limit on the allocation a hostile header can ask for |

Oracles: `astropy.io.fits` (BSD-3-Clause) and `fitsverify`. Corpus: NASA's
[FITS sample files](https://fits.gsfc.nasa.gov/fits_samples.html) and astropy's
test data. Every item also needs unit tests at 100% coverage and a performance
table against the reference.
