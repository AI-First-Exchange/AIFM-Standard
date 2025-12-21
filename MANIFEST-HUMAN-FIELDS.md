OPTIONAL MANIFEST FIELDS FOR HUMAN AUTHORSHIP DOCUMENTATION

(AIFX — AI First Exchange)

The following optional fields MAY be included in manifest.json files for
AIFM, AIFV, AIFI, and AIFP formats under the AI First Exchange (AIFX).

These fields allow creators to declare and document human creative involvement
in AI-assisted workflows. They are intended to support transparency, attribution,
and contextual authorship documentation.

Inclusion of these fields does not constitute a legal determination of
copyright ownership, authorship, or eligibility. Interpretation and legal
significance are determined by downstream platforms, rights holders, and
applicable law.

Optional Fields
```json
"human_authorship_statement": "",
"human_signature": "",
"creator_email": "",
"editorial_notes": "",
"human_editing_steps": [],
"human_curated_output": true
```
Field Descriptions
human_authorship_statement

A creator-provided declaration describing meaningful human creative involvement,
such as concept development, prompt design, scripting, selection, sequencing,
editing, or curation of AI-generated material.

human_signature

An optional typed name, digital signature, or cryptographic hash associated with
the authorship statement. This field is declarative and not a legal attestation.

creator_email

Optional contact information for the declaring creator. This field may be used
for attribution, communication, or verification workflows.

editorial_notes

Free-form notes describing human creative decisions, narrative intent, stylistic
direction, or editorial judgment applied during creation or post-processing.

human_editing_steps

An optional array documenting post-generation human actions, such as edits,
cuts, refinements, sequencing changes, audio adjustments, or visual corrections.

human_curated_output

A boolean flag indicating that the final output was selected, arranged, refined,
or approved by a human rather than being an unreviewed automated result.

Notes

All fields are optional

All fields are self-declared

Fields are documentation-oriented, not forensic

AIFX does not verify or certify the accuracy of these declarations

Legal interpretation is the responsibility of downstream systems and law
