---
title: "wav"
weight: 70
description: "Planned, wave 2: WAV audio files."
---

<!-- From go-scikit/roadmap, bib/systems-units-formats-visualization.md, sections 1c, 2d, 3c, 4 and 5, and PLAN.md item 9. Change it there first. -->

**Status: planned (wave 2). No code exists.** The package name is provisional.

## What it will provide

Microsoft RIFF WAVE files: PCM at 8, 16, 24 and 32 bits, floating point, and the
extensible header. WAV is simple enough that the roadmap suggests writing it
afresh; `go-audio/wav` (Apache-2.0) is archived and the `go-audio` name belongs
to a third party.

## References

| Subject | Reference |
| --- | --- |
| the format | Microsoft's RIFF WAVE specification, as cited in the roadmap's bibliography |

## How it will be validated

| Area | Criterion |
| --- | --- |
| round trip | Go writes and `scipy.io.wavfile` reads, and the other way round, with identical samples |
| hostile input | `go test -fuzz` for panics; a limit on the allocation a hostile header can ask for |

`scipy.io.wavfile` is the oracle. Every item also needs unit tests at 100%
coverage and a performance table against the reference.
