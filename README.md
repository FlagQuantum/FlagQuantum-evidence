# FlagQuantum Evidence Archive

This repository is the external archive for sealed FlagQuantum benchmark and
validation evidence. Large payloads are published as GitHub Release assets so
they do not inflate normal clones of the
[FlagQuantum source repository](https://github.com/flagos-ai/FlagQuantum).

## What lives here

- Release assets containing immutable evidence bundles.
- A manifest beside every bundle with its source commit, file count, byte size,
  SHA-256 digest, and reproduction metadata.
- Schemas and retention rules needed to validate those manifests.

Source code, benchmark runners, current release-gate summaries, and small test
fixtures remain in the FlagQuantum source repository. Exploratory output,
profiler traces, repeated experiment matrices, and superseded raw results belong
in release bundles here.

## Release layout

Each archive release uses a date-based tag such as `evidence-2026-10-09.1` and
contains:

```text
flagquantum-evidence-2026-10-09.1.tar.zst
flagquantum-evidence-2026-10-09.1.manifest.json
SHA256SUMS
```

The manifest must validate against
[`schema/evidence-manifest-v1.schema.json`](schema/evidence-manifest-v1.schema.json).
Publish a release only after verifying the archive digest and confirming that
every source-repository link being replaced points to the new immutable asset.

## Integrity

Consumers should verify the downloaded archive before extracting it:

```bash
shasum -a 256 -c SHA256SUMS
```

Release assets are append-only evidence snapshots. Corrections use a new release
tag and manifest; an existing archive is never silently replaced.
