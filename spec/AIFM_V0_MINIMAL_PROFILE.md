# AIFM v0 Minimal Profile (SDA + Canonical Integrity)

Status: **LOCKED (v0)**
Verification tier: **SDA only**
Integrity: **sha256 + canonical_excludes_self**

This document defines the minimum required structure for an **AIFM** package to be considered valid in AIFX v0.

AIFM is a container for AI-generated music/audio, bundling:
- `manifest.json`
- one primary audio asset in `assets/`
- optional cover image asset in `assets/`
- canonical integrity hashes

---

## 1) Container structure

An **.aifm** file is a ZIP container with:

Required:
- `manifest.json`
- `assets/audio.<ext>` (single primary audio)

Optional:
- `assets/cover.<ext>` (e.g., `.png`, `.jpg`, `.jpeg`, `.webp`)

No symlinks.
No absolute paths.
No `..` traversal.

---

## 2) Manifest required fields

`manifest.json` MUST be valid JSON and MUST include:

### Identity / work
- `aifx_version` (string; current tooling uses `"0.1"`)
- `type` = `"AIFM"`
- `work.title` (string; non-empty)

### Creator (SDA)
- `creator.name` (string; non-empty)
- `creator.contact` (string; non-empty; email recommended)

### Provenance scope
- `mode` (string; example: `human-directed-ai`)
- `verification_tier` MUST be `"SDA"`
- `ai_generated` MUST be `true`
- `declaration` (string; non-empty; human-authored)

---

## 3) Assets

AIFM v0 requires exactly **one** primary audio asset.

Recommended canonical path:
- `assets/audio.<ext>`

Allowed audio extensions (tooling v0):
- `.wav`, `.mp3`, `.flac`, `.m4a`, `.ogg`

If a cover image is included, recommended:
- `assets/cover.<ext>`

---

## 4) Canonical integrity (AIFX)

AIFM MUST include the canonical `integrity` block:

```json
"integrity": {
  "algorithm": "sha256",
  "manifest_hash_mode": "canonical_excludes_self",
  "hashed_files": {
    "assets/audio.wav": {"sha256": "<sha256>"},
    "manifest.json": {"sha256": "<sha256_of_manifest_canonical_excludes_self>"}
  }
}
```
Rules
	•	integrity.algorithm MUST be "sha256".
	•	integrity.hashed_files MUST be an object with sha256 entries for all required files.
	•	Required hashed files include at minimum:
	•	the primary audio asset (e.g., assets/audio.wav)
	•	manifest.json

Canonical excludes self

The manifest.json hash MUST be computed over the manifest JSON with the manifest.json hash entry excluded.

⸻

5) Validation outcomes

A package FAILS if any required field is missing, empty, or invalid, including:
	•	missing manifest.json
	•	missing work.title
	•	missing creator.name or creator.contact
	•	verification_tier not "SDA"
	•	ai_generated not true
	•	missing/empty declaration
	•	missing integrity or integrity mismatch
	•	missing primary audio asset
	•	unsafe paths/symlinks

⸻

6) v0 scope boundary

AIFM v0 does not:
	•	prove originality
	•	verify identity
	•	enforce licensing
	•	perform moderation

It only enforces:
	•	structure
	•	SDA boundary
	•	canonical integrity

⸻

Core principle

Declare only what you can prove today.
Design for what you can verify tomorrow.
