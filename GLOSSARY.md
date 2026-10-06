# F-AI-R

F-AI-R is a framework research project within OMBION. These terms describe the
minimal manually reviewable evidence-record concept being explored for its first
TSAR-based MVP.

## Language

**Endpoint terminology**:
The terminology used by a source for assay readouts, biological endpoints,
regulatory endpoints, or OECD reporting endpoints. These concepts are distinct;
their relationships may remain unresolved, and not every source or method
describes all four.
_Avoid_: Interchangeable endpoint labels

**Reporting unit**:
The entity or level of information described by an OHT report, established from
the authoritative template documentation. Method/protocol information,
individual-study information, and chemical-specific observed results remain
distinct rather than interchangeable.
_Avoid_: Test method as an assumed universal reporting unit

**Field-population status**:
The state of population of an OHT field: unpopulated, partially populated, or
populated, with present and missing components identified for partial population.
It is distinct from source/access status and uncertainty/conflict status, whose
conditions may coexist for one field.
_Avoid_: Combined availability and population status

**Field disposition**:
An explicit account of how a relevant OHT field is treated in a draft, including
the reason it remains unpopulated and any supporting evidence. It does not
collapse field-population status, source access, and uncertainty into one state.
_Avoid_: Blank field as an explanation

**Documented blocked attempt**:
A deeper-processing attempt whose inability to proceed is recorded with its
reasons and supporting findings. It is distinct from a successful populated or
partial populated draft.
_Avoid_: Successful population run

**Not applicable**:
A finding supported by OHT semantics or authoritative method documentation that
the field does not apply to the reporting case. Missing evidence alone does not
establish non-applicability.
_Avoid_: Missing information

**Inventory completion**:
Completion of the agreed, bounded source-discovery scope with its inspections
logged. It does not imply exhaustive source coverage, availability of all
referenced material, or an eligible candidate for deeper processing.
_Avoid_: Exhaustive source coverage

**Source-supported assertion**:
A narrowly scoped assertion attributed to identifiable source material. The term
does not imply that scientific adequacy or validity has been established.
_Avoid_: Scientific evidence claim (at this stage)

**Evidence record**:
A record representing one source-supported assertion attributed to one inspected
source artefact, with source content, its location, our interpretation, and
scientific adequacy kept conceptually separate. Multiple individually traceable
passages from that artefact may support the assertion; assertions from different
artefacts remain separate records.
_Avoid_: Source document, aggregate evidence package

**Source artefact**:
An identifiable source document or other source entity referenced by an evidence
record. One source artefact can support multiple evidence records.
_Avoid_: Evidence record

**Source excerpt**:
The exact relevant text from the source artefact as inspected, retaining its
qualifications, conditions, and uncertainty. An assertion summary does not replace
the excerpt for source-fidelity review.
_Avoid_: Assertion summary, interpretation

**Assertion summary**:
A concise representation of what the supporting source content states, separate
from that content and from our interpretation.
_Avoid_: Source excerpt, interpretation

**Interpretation**:
Our optional reading of the source statement, explicitly separate from source
content and the assertion summary.
_Avoid_: Source excerpt, assertion summary

**Source provenance**:
What is known about the origin and identity of the inspected source artefact.
Unknown source lineage remains explicit.
_Avoid_: Record-creation provenance

**Record-creation provenance**:
The account of how source content became an evidence record, including the actors
and transformations involved and any human correction or verification.
_Avoid_: Source provenance

**Transformation product**:
Content produced by extraction or transformation of source material, such as OCR
text, parser output, or an LLM-generated summary. It is not an independent
scientific source.
_Avoid_: Independent scientific source

**Source-expressed uncertainty**:
A limitation, qualification, or condition expressed by the source itself about
the assertion.
_Avoid_: Extraction/transformation uncertainty, scientific adequacy rating

**Extraction/transformation uncertainty**:
Uncertainty about errors introduced while source content becomes record content,
including through OCR, parsing, transcription, or LLM-assisted transformation.
_Avoid_: Source-expressed uncertainty, scientific adequacy rating

**Missing or unknown information**:
Information currently unavailable to the record, distinguished as not reported in
the inspected material, not yet checked, or inaccessible where applicable.
Non-reporting in inspected material does not establish absence elsewhere, and
failed inspection establishes neither non-reporting, non-applicability, nor absence.
_Avoid_: Evidence of absence

**Source-fidelity review**:
A human review of source identifiability, passage locatability, faithful
representation, separation of interpretation from source content, and visibility
of uncertainty or missing information. This review can pass while scientific
adequacy remains unresolved.
Successful review requires the reviewer to inspect the identified original
supporting content; a summary alone cannot substitute for inaccessible content.
Review applies to the reviewed state of the record; a change affecting reviewed
content or traceability requires fresh review.
_Avoid_: Scientific validation

**Scientific adequacy**:
Whether a source-supported assertion is scientifically adequate or justified.
This is a separate, later review dimension whose requirements remain unresolved
pending the TSAR source audit and definition of validation requirements.
_Avoid_: Source fidelity, source traceability
