---
title: "flac"
weight: 80
description: "Planned, wave 2: FLAC decoding."
---

<!-- From go-scikit/roadmap, bib/systems-units-formats-visualization.md, sections 1c, 2d, 3c, 4 and 5, and PLAN.md item 9. Change it there first. -->

**Status: planned (wave 2). No code exists.** The package name is provisional.
It is the smallest item of the organisation (size S).

## What it will provide

FLAC decoding: frames, Rice coding, linear prediction, and the MD5 of the
samples. Whether to import `mewkiz/flac` (Unlicense, decoder and encoder) or to
port it is open.

## References

| Subject | Reference |
| --- | --- |
| the format | [RFC 9639, Free Lossless Audio Codec](https://www.rfc-editor.org/rfc/rfc9639) |

## How it will be validated

| Area | Criterion |
| --- | --- |
| decoding | exact equality of the decoded samples against the reference decoder, and the stream's MD5 of samples matches |
| hostile input | `go test -fuzz` for panics; a limit on the allocation a hostile header can ask for |

Corpus: the IETF working group's
[FLAC test files](https://github.com/ietf-wg-cellar/flac-test-files) (CC0-1.0).
Every item also needs unit tests at 100% coverage and a performance table
against the reference.
