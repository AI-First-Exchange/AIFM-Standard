AIFM — AI First Music Format (.aifm)

Part of the AI First Exchange (AIFX)

AIFM (AI First Music Format) is an open, ZIP-based standard for AI-generated music. It packages audio assets, prompts, generation parameters, stems, artwork, licensing information, and declared provenance into a single .aifm file.

AIFM is designed for transparent, inspectable, and interoperable AI-native music workflows across platforms and tools.

🎧 Overview

An .aifm file represents a single AI-generated music track with structured
context describing:

how the music was generated

with what tools or models

under what parameters

and how humans may have curated or edited the result

AIFM documents declared metadata and workflow context.
It does not guarantee reproducibility, legal authorship, or ownership.

📦 AIFM Container Structure

An .aifm file is a ZIP container with the following standardized layout:

/
  manifest.json                     # REQUIRED: primary music manifest
  audio/
    main.mp3                        # REQUIRED: main track (or wav / flac)
    stems/                          # OPTIONAL: separated instrument stems
  artwork/
    cover.jpg                       # OPTIONAL: cover art
  prompts/
    generation.txt                  # OPTIONAL: main prompt
    negative.txt                    # OPTIONAL: negative prompt
    settings.json                   # OPTIONAL: generation parameters
  legal/
    license.txt                     # OPTIONAL: licensing terms
    terms.txt                       # OPTIONAL
  extra/
    notes.md                        # OPTIONAL: creator notes


The manifest.json anchors the container by defining metadata, declared AI
sources, provenance, and file references.

🧠 Key Capabilities
✔ AI-Native Music Metadata

AIFM may record declared information such as:

AI tool or platform identifier (e.g., Suno)

Model or version name

Prompt and negative prompt sources

Generation parameters (tempo, style, structure, etc.)

Creation timestamp

Declared creator identity

Toolchain history

✔ Unified Music Container

A single .aifm file may include:

Final audio track

Stems (optional)

Prompts and settings

Artwork

Licensing information

Declared provenance

This supports exchange, archiving, review, and platform ingestion
without relying on external sidecar files.

✔ Declared Provenance & Transparency

AIFM enables documentation of:

who declared authorship

which tools were used

what inputs shaped the output

when the track was generated

AIFM records declared provenance, not absolute proof of origin.

✔ Open & Extensible Design

AIFM is:

ZIP-based

JSON-driven

language-agnostic

forward-compatible

Developers may extend AIFM for:

multi-track or album workflows

remix or derivative tracking

DAW integration

AI music publishing platforms

📑 manifest.json (Simplified Example)
{
  "aifm_version": "1.0.0",
  "id": "aifm-2025-000001",
  "title": "Track Title",
  "creator": "Artist Name",
  "duration_seconds": 180.0,
  "genres": ["lofi"],
  "ai_generated": true,

  "ai_source": {
    "tool_name": "Suno",
    "model_name": "Suno-v4",
    "prompt_source": "prompts/generation.txt",
    "settings_source": "prompts/settings.json"
  },

  "provenance": {
    "creator_handle": "YourName",
    "creation_utc": "2025-11-25T20:31:00Z",
    "tool_chain": ["Suno", "AIFX Converter v1.0"]
  },

  "files": {
    "main_audio": "audio/main.mp3",
    "stems": [],
    "cover_art": "artwork/cover.jpg",
    "license_file": "legal/license.txt"
  }
}

🌐 MIME Type

Proposed MIME type:

audio/aifm

🧰 Tooling (Planned)

Reference implementations may include:

aifmwrap — package audio assets into .aifm

aifm-validate — validate AIFM containers

aifm-core — libraries for reading/writing AIFM files

🛠 Use Cases

AI music publishing platforms

Transparent AI music labeling

Creator attribution and curation

Remix and derivative tracking

Archival of AI-native music works

🔄 Versioning

AIFM follows semantic versioning:

1.x.x — backward-compatible enhancements

2.x.x — backward-incompatible schema changes

Unknown fields should be ignored for forward compatibility.

📬 Contributing

AIFM is an open specification under the AI First Exchange (AIFX).
Feedback, proposals, and pull requests are welcome.

📝 License

Released under the MIT License.
