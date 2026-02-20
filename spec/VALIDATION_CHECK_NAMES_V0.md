# AIFX v0 Validation Check Names (Canonical)

Status: **LOCKED (v0)**

This document defines the canonical `checks` map keys emitted by AIFX v0 validators.
Tooling and specs MUST keep these names stable in v0.

---

## Security / path safety
- `security.safe_paths` (no absolute paths, no traversal)
- `security.no_symlinks` (no symlinks)

---

## Files (format-specific)
AIFM:
- `files.primary_audio_single`

AIFV:
- `files.primary_video_single`
- `files.thumbnail_present`

AIFI:
- `files.primary_image_single`

---

## Manifest presence
- `manifest` (string: `"ok"` / `"fail"`)

---

## Provenance / identity
- `aifx_version` (string)
- `work.title` (bool)
- `author` (bool) *(legacy compatibility; true if creator.name present)*
- `contact` (bool) *(legacy compatibility; true if creator.contact present)*
- `ai_declared` (bool)

Manifest-field checks (bool):
- `manifest.work.title`
- `manifest.creator.name`
- `manifest.creator.contact`
- `manifest.mode`
- `manifest.verification_tier`
- `manifest.ai_generated`
- `manifest.declaration`

---

## Integrity (canonical AIFX)
- `integrity` (string: `"ok"` / `"fail"`)
Optional detailed keys may include:
- `integrity.algorithm`
- `integrity.hashed_files_present`
- `integrity.hashes_match`

v0 tooling may emit either the single `integrity` string or the detailed sub-keys (or both).
Specs should treat `integrity="ok"` as PASS for canonical integrity.

---

## Informational (warnings only in v0)
- `info.video_facts_present` (AIFV only; warning if false)

---

## Notes
- Exit codes are defined by the CLI/tooling layer, not the validator.
- Validators must never imply identity verification beyond SDA.
