# TSAR agent/workflow MVP v0

Status: formal specification draft for human review; not approved for tickets,
implementation, or publication. Prepared: 2026-10-06. Primary reviewer: Michael.

Primary requirements: [TSAR agent requirements interview](../research/tsar-agent-requirements.md)
at checkpoint `250578f5d80c35d4b2aabe1675cefb6fbbea9d01`. Domain vocabulary:
[GLOSSARY.md](../../GLOSSARY.md). The current specification request authorizes
this local synthesis and supersedes the interview's historical prohibition on
writing a formal spec; the reviewed interview and glossary remain unchanged.

This draft follows the project-local `to-spec` template. That skill specifies
issue-tracker publication but provides no local specification path convention.
This document is a local review artefact, not a substitute issue tracker. The
publication step is stopped under the user's explicit no-GitHub-write boundary.
The testing seam below is proposed for Michael's review, not already approved.

## Problem Statement

Michael needs to turn TSAR method leads into inspectable, source-traceable
evidence and an applicable OECD Harmonised Template (OHT) draft without assuming
which method, endpoint, study, chemical, template, or data source is suitable.
Sources may be incomplete, inaccessible, difficult to extract, or conflicting.
Method/protocol information cannot automatically substitute for observed study
or chemical results. A plausible-looking populated template is insufficient if
its assertions, omissions, transformations, or reporting case cannot be checked.

The first substantive F-AI-R MVP must support informed human selection and
complete source-fidelity review while keeping scientific adequacy and final
scientific authorization separate. Neither actual source availability nor
authoritative validation status or OHT applicability has been independently
established by this specification.

## Solution

A manually invoked, staged, resumable workflow in the existing SURF Research
Cloud workspace inventories all three initial leads, compares their inspected
sources and preliminary OHT applicability, then waits for Michael to approve
one method. For that method it establishes the reporting unit and source case,
obtains a second approval, and produces a reviewable draft keyed to verified
OHT fields. Michael reviews the complete first case against original supporting
content. Unsupported and disputed values remain unpopulated with explicit
accounting; sparse drafts and documented blocks remain useful, distinct results.

### Starting scope and actors

The initial leads supplied by Ingrid are:

| TSAR ID | User-provided method name | Seed URL |
| --- | --- | --- |
| tm2010-07 | Transactivation assay for detection of androgenic activity of chemicals | https://tsar.jrc.ec.europa.eu/test-method/tm2010-07 |
| tm2008-05 | Human Cell Line Activation Test (h-CLAT) | https://tsar.jrc.ec.europa.eu/test-method/tm2008-05 |
| tm2009-06 | Direct Peptide Reactivity Assay (DPRA) | https://tsar.jrc.ec.europa.eu/test-method/tm2009-06 |

Their validated status and names are supplied context pending authoritative
verification. No one of the three is preselected. Michael is the primary reviewer
and approval authority. Ingrid may supply leads or inform later investigation;
the workflow does not assume that a supplied lead is authoritative evidence.

### Workflow and required packages

The phases below define observable behavior, not a single-agent or multi-agent
architecture. Discovery and preliminary screening may be interleaved within
the approved scope; all three candidates must be accounted for before comparison
and method selection. Detailed field mapping waits until method approval;
population additionally waits until the pre-population gate.

| Phase or gate | Required behavior | Reviewable result / next condition |
| --- | --- | --- |
| A — Bounded discovery / inventory | Execute and log the declared discovery plan for all three TSAR leads. | Plan, execution log, per-method artefact inventories, access failures, gaps, conflicts, uncertainty, and remaining leads. |
| B — Preliminary endpoint / OHT applicability | Inspect authoritative scope evidence; retain source endpoint terminology and unresolved relationships. No detailed field mapping or population. | Per-candidate endpoint findings, candidate OHT identity/version where identifiable, authoritative source, supporting passages, and applicability questions. |
| C — Method comparison | Compare availability, traceability, extractability, and reporting coverage separately. | Comparison, recommendation with evidence/limitations, or supported no-eligible-candidate outcome. |
| Human gate 1 — Method selection | Michael reviews all three inventories and the comparison and explicitly approves the selected method. | Recorded approval bound to reviewed versions; no automatic continuation. |
| D — Detailed reporting case / OHT determination | Establish detailed endpoints, exact OHT identity/version and structure, applicability, reporting unit, and identifiable candidate source cases. | Rationale and evidence for each foundation, proposed cases and limitations, material ambiguity/conflicts, authoritative OHT access/retention findings. |
| Human gate 2 — Pre-population approval | Michael independently reviews and approves together the foundations and selected source case. | Version-bound approval; materially unresolved foundations prohibit population. |
| E — OHT mapping / population | Use the retrieved, sufficiently verified authoritative OHT and approved case. Populate only supported values; account for all relevant fields. | Field-keyed draft, evidence ledger, gap/conflict report, run manifest, retained OHT where permitted, and review package. |
| F — Source-fidelity review | Michael inspects originals and reviews every populated assertion/value and every relevant unpopulated-field disposition for the first case. | Findings, any corrected/reference version, and acceptance of the exact reviewed output version or an explicit incomplete/rejected review. |

Inventory outputs also include preliminary applicability findings and the four
comparison dimensions. The deeper-processing package includes the retrieved
authoritative OHT/template representation where permitted, endpoint/applicability
rationale, approved reporting unit/source case, field-keyed draft, assertion/value
evidence ledger, gap/conflict report, run manifest, and human-review summary.
Related outputs may share files when relationships and provenance remain explicit.
Native-format OHT export is not required. Blocked attempts retain the obtainable
findings, logs, manifests, and reasons; they do not fabricate a populated draft
to imitate a successful package.

## User Stories

1. As Michael, I want all three initial leads inventoried before selection, so
   that an early preference does not hide a more suitable reporting case.
2. As Michael, I want a bounded discovery plan recorded before searches, so that
   I can understand the scope and reproduce the procedure.
3. As Michael, I want actual queries, followed links, inspected results, failures,
   and skipped leads logged with reasons, so that omissions remain visible.
4. As Michael, I want document and data artefact types distinguished, so that
   protocol descriptions are not mistaken for observed or raw data.
5. As Michael, I want validation status supported by authoritative evidence or
   explicitly unverified, so that supplied context does not become an invented fact.
6. As Michael, I want source access, version, reuse, and retention restrictions
   recorded per artefact, so that processing respects each source's conditions.
7. As Michael, I want source endpoint terminology and supported relationships
   preserved, so that distinct endpoint concepts are not conflated.
8. As Michael, I want preliminary OHT applicability linked to authoritative
   passages, so that name similarity cannot decide reporting suitability.
9. As Michael, I want four separate comparison dimensions, so that access and
   extraction feasibility are not presented as scientific quality.
10. As Michael, I want recommendations with evidence and gaps, so that I can
    approve a method or accept that none currently qualifies.
11. As Michael, I want method-selection approval required before deeper work,
    so that the workflow cannot choose and proceed autonomously.
12. As Michael, I want the reporting unit established from authoritative OHT
    documentation, so that the draft describes the correct entity and level.
13. As Michael, I want candidate source cases proposed after reporting-unit
    determination, so that I need not supply a study or chemical prematurely.
14. As Michael, I want studies, chemicals, experiments, and reporting cases kept
    distinct, so that their observations are not silently combined.
15. As Michael, I want one approval covering the detailed reporting foundations,
    so that population cannot proceed through material ambiguity.
16. As Michael, I want a draft keyed to the actual verified OHT structure, so
    that I can review real fields without requiring native export yet.
17. As Michael, I want every populated assertion/value tied to inspected evidence,
    so that a populated field cannot hide unsupported units or qualifiers.
18. As Michael, I want all relevant fields and missing components accounted for,
    so that a sparse draft can be informative without a coverage threshold.
19. As Michael, I want population, access, and uncertainty tracked separately,
    so that failure to retrieve a source cannot become non-applicability.
20. As Michael, I want conflicting assertions retained separately and disputed
    values left unpopulated, so that the workflow cannot manufacture agreement.
21. As Michael, I want local conflicts to permit unaffected work but foundational
    conflicts to reopen approval, so that progress respects the approved case.
22. As Michael, I want explicit extraction and transformation histories, so that
    OCR errors, conversions, summaries, and derived values can be checked.
23. As Michael, I want original artefacts retained separately from extractions
    where permitted, so that provenance remains independently inspectable.
24. As Michael, I want limitations recorded when originals cannot be retained
    or inspected, so that review completion is not overstated.
25. As Michael, I want no external processing transmission by default, so that
    source-specific restrictions are respected before any provider is chosen.
26. As Michael, I want resumable stages and inspectable intermediate artefacts,
    so that interruptions do not discard evidence or bypass approval.
27. As Michael, I want changed remote sources treated as distinct versions, so
    that an approved source is not silently replaced during resumption.
28. As Michael, I want original outputs, reviewer findings, and corrections
    preserved separately, so that evaluation can compare the actual agent result.
29. As Michael, I want independent confirmation before first-case population
    and complete review afterward, so that selection and population errors are visible.
30. As Michael, I want error classes reported separately, so that unsupported
    fills and missed information do not disappear into an overall quality score.
31. As Michael, I want acceptance recorded for an exact output version, so that
    later changes cannot inherit acceptance without the required re-review.
32. As Michael, I want scientific adequacy and final authorization kept separate
    from source fidelity, so that a faithfully recorded claim is not called validated.
33. As the workflow operator, I want runtime prerequisites verified in the
    existing SURF workspace, so that deployment decisions do not assume capabilities.
34. As the workflow operator, I want failures to identify blocked stages and
    independent work that can continue, so that failures remain reproducible.

## Implementation Decisions

These are behavioral and information contracts grounded in the interview and
current request. They do not select programming language, storage technology,
agent topology, provider, deployment infrastructure, or concrete export format.
Requirement identifiers support later acceptance-criteria traceability; they
are not implementation tickets.

### Functional requirements

**FR-1 — Inputs and stage control.** Initial input is the three agreed TSAR
IDs/URLs plus approved discovery/run configuration, including scope and processing/
retention boundaries. No chemical or study is required upfront. Preserve run and
stage identity, intermediate results, and approvals sufficiently to resume and
audit a run. Do not make automatic method selection or bypass human gates.

**FR-2 — Bounded discovery.** Before inventory, record seeds, scoped research
questions, allowed authoritative source classes, initial queries, inclusion/
relevance rules, exclusions where relevant, and stopping conditions. Inspect the
TSAR record for each lead and all directly accessible relevant TSAR-linked
artefacts concerning methods, validation, studies, endpoints, or reporting.
Use targeted authoritative searches needed for endpoint/OHT applicability,
primarily OECD and JRC/EURL ECVAM or another clearly relevant official body.
Inspect identifiable original publications or method-owner documents referenced
by authoritative material or needed for a specific inventory question. Document
targeted query refinements and their reasons; scope expansion requires Michael's
approval. Stop when the agreed procedure has been executed and logged; no
unrestricted search or arbitrary initial time/download cap. Record actual effort
and source volume to inform future limits.

**FR-3 — Inspection log and inventory.** Log actual queries, results/sources
inspected, links followed, retrieval/access timestamps, inspection outcomes,
access/download failures, relevant leads not inspected, and refinement reasons.
Make searched, inspected, skipped, and unresolved items distinguishable with
reasons. Where applicable, distinguish TSAR metadata, method descriptions,
SOPs/protocols, validation reports, study reports, appendices, tables/figures,
downloadable datasets, raw data, processed data, regulatory/validation documents,
original-source/publication references, versions/dates, access restrictions,
reuse/licensing information, and referenced-but-unavailable material. Do not
assume that raw data or any listed artefact type exists. An inaccessible artefact
may be inventoried as a reference without being represented as inspected.

**FR-4 — Preliminary applicability.** Before selection, record source-supported
endpoint terminology, candidate OHT identity/version where identifiable,
authoritative OHT source, supporting passages or precise applicability evidence,
and ambiguities, conflicts, and unresolved questions. This is comparison evidence
only; no detailed field mapping or population is allowed in phases A–C. An unknown
candidate OHT version stays unknown during screening and must be resolved before
population. Name similarity alone does not establish applicability.

**FR-5 — Comparison.** Cover all three leads using source-linked findings for
availability (actual access/inspectability and limitations), traceability (unique
source identity/version and precise locators), extractability (reliable native,
OCR, or manual extraction and limitations), and reporting coverage (supported
information categories relevant to the prospective reporting unit before detailed
mapping). Keep accessible-but-incomplete sources distinct from rich but difficult
sources. Do not create an aggregate score, population threshold, or automated
scientific-quality/adequacy judgment. Produce a comparison, evidence-supported
recommendation and gaps, or a supported conclusion that none currently qualifies.

**FR-6 — Detailed foundations and case proposal.** After gate 1, document detailed
endpoint determination, exact OHT identity/version and verified structure,
applicability rationale, authoritative reporting-unit semantics, source-supported
case candidates, and material ambiguity/conflicts. For each proposed case show
source identity, reporting-unit match rationale, available support, gaps, and case
identity/boundary ambiguities. Michael approves the selected study/chemical/source
case at gate 2. Do not silently combine distinct cases or presume supplied leads
are inspected evidence.

**FR-7 — Field-keyed population.** Retrieve the authoritative OHT/template
representation and sufficiently verify its identity/version and structure before
any population. Preserve the exact version where permitted. Map the approved
case into actual verified OHT fields and account for every relevant field, with
relevance grounded in OHT semantics and the approved reporting case. Produce
supported assertions/values or explicit dispositions, not invented replacements.
Do not invent missing scientific or metadata values. Native-format export is
not required. Record inability to retrieve/verify the authoritative OHT as a
documented blocked attempt; never populate an inferred substitute template.

### Scientific and evidence requirements

**SE-1 — Endpoint distinctions and reporting unit.** Assay readout, biological
endpoint, regulatory endpoint, and OECD reporting endpoint remain distinct where
sources require distinction. Use the source's terminology; establish relationships
only from supporting evidence and retain unresolved relationships explicitly.
Do not force all four concepts onto every method. Determine the reporting unit
from authoritative OHT documentation. Keep method/protocol, individual-study,
and chemical-specific observed information separate. Protocol information may
enter a study-result field only when both source and OHT semantics support it.

**SE-2 — Source authority.** Allowed discovery sources are TSAR, relevant linked
material, OECD, JRC/EURL ECVAM, other clearly relevant official regulatory/
validation bodies, identifiable original publications, and appropriate original
method-owner documents. Assess source support for the specific assertion, not
only a site's reputation. Secondary summaries may be discovery leads, but there
is no secondary-source population exception in MVP v0. If the supporting original/
authoritative source cannot be inspected, leave the affected value unpopulated,
identify the unavailable original where possible, and record limitations and
uncertainty. A transformation product is not an independent scientific source.

**SE-3 — Conflicts.** Preserve each conflicting assertion in its own evidence
record with provenance. Leave conflicting/disputed values unpopulated until
resolved; mark conflict/ambiguity explicitly and never synthesize a preferred
value silently. Continue unaffected fields. If a conflict undermines approved
endpoint determination, OHT identity/version, applicability, reporting unit, or
source case, pause deeper processing and return to the relevant human gate.
Any human resolution must remain explicit, evidenced, and subject to the same
population and review rules; approval cannot make unsupported content evidence.

**SE-4 — Transformations.** Allow only explicit, reproducible, traceable
transformations. Prefer native machine-readable/text extraction and deterministic
parsing/validation. Use OCR only when reliable native extraction is unavailable
or insufficient; label OCR-derived content and preserve source location and
extraction method. Faithful summaries assist mapping/review but remain separate
from source excerpts and interpretations and cannot become independent evidence.
Mechanical unit conversions retain original value/unit, target unit, rule/formula,
and result. Never infer missing scientific values. New scientific results for
population are not allowed unless Michael explicitly approves a defined
deterministic transformation needed for a specific OHT field. Record that approval
and derivation; never present a derived value as directly reported by the source.

**SE-5 — Scientific boundaries.** No invented data, unsupported scientific claim,
automatic scientific-adequacy conclusion, or automatic regulatory conclusion.
Source fidelity, source support, and population success do not confer scientific
adequacy or final scientific authorization. Source-expressed uncertainty and
extraction/transformation uncertainty remain separately visible.

### Data and provenance requirements

**DP-1 — Artefact/version record.** For retained artefacts record at least identity/
title, original URL/location or identifier, version/date where available,
retrieval date, local filename or artefact identifier, content hash, and applicable
retention/access/licensing restriction. Preserve exact inspected artefacts and
the exact authoritative OHT version where legally and technically permitted.
Unknown metadata is explicit, not guessed. If retention is prohibited or technically
impossible, record the limitation and enough identity, locator, retrieval, and
provenance metadata for independent retrieval where possible. Do not claim a
retained hash or snapshot exists when it could not be obtained.

**DP-2 — Evidence record.** One record attributes one narrowly scoped assertion
to one inspected source artefact; multiple individually traceable passages from
that artefact may support it. Assertions from different artefacts remain separate
records. A field may reference multiple records. Require assertion/value-level
support, with separate support for units, conditions, and qualifiers where needed.
Whole-field or whole-template provenance is insufficient.

For each record capture where available: artefact identity/title, location,
version/publication date, retrieval/access date, precise page/section/table/row/
cell or equivalent locator, exact excerpt or relevant table/source content where
retainable, source-supported assertion/value, separate assertion summary and
interpretation, extraction/transformation history, relevant tool/model/version,
and human correction/verification. Keep source provenance separate from
record-creation provenance. Unknown source lineage, missing metadata, source
qualifications, extraction uncertainty, and access limitations remain explicit.
Unavailable provenance needed to inspect an assertion prevents review acceptance
for that assertion; an optional unavailable metadata item is recorded as such.

**DP-3 — Field accounting.** For each relevant field maintain separate dimensions:

| Dimension | Minimum vocabulary / accounting |
| --- | --- |
| Field-population status | Unpopulated, partially populated, populated. For partial fields identify supported present components and each missing component, with reasons where known. |
| Source/access status | Inspected/accessible, referenced but unavailable, inaccessible, not yet checked, or another explicitly documented source-supported condition. |
| Uncertainty/conflict status | Ambiguous/conflicting, source-expressed qualification/uncertainty, extraction/transformation uncertainty, or another documented condition. |
| Field disposition | Reasons and supporting findings for unpopulated fields/components, including not reported in inspected material and authoritative not applicable findings. |

Multiple conditions may coexist; do not force a field into one combined status.
Not applicable requires OHT semantics or authoritative method documentation and
never means merely missing. Not reported is limited to inspected material, not
the internet or other uninspected sources. Link missing/disputed components to
source locators, gap evidence, or inspection results where available. Retain
the reason when a component is not yet checked. A failed inspection establishes
neither non-reporting, non-applicability, nor absence of content.

**DP-4 — Run manifest and packages.** Identify inspected sources and versions,
retrieval dates, processing steps, relevant tools/models/versions, actors, and
relationships between inventories, decisions, evidence records, OHT fields,
transformations, gaps/conflicts, approvals, and output versions. Original sources,
extracted representations, and transformation metadata remain distinct and linked.
Related reports may share a representation, but original provenance may not be
replaced by an extraction or summary. The package must support passage location
and inspection of original supporting content, not just reading a summary.

**DP-5 — History, correction, and resumption.** Preserve original agent output,
reviewer findings, and any corrected/reference result as distinct versions.
Preserve original inspection records. Resume using preserved source/OHT versions
where available; changed/replaced remote content is a distinct source version,
not a silent update. Reassess affected assertions/values, field dispositions,
provenance records, transformations, dependent mappings, and gap/conflict
conclusions. Reopen gate 2 if correction changes its foundations; return to gate 1
if the approved method-selection basis is undermined. Exact output acceptance
does not carry silently to changed content or traceability.

### Human-review and evaluation requirements

**HR-1 — Method gate.** Gate 1 records Michael's decision after review of all
three inventories/comparison. A recommendation is not approval. Without approval,
only allowed inventory work may proceed; no deeper endpoint/OHT/case work or
detailed mapping/population follows automatically. A no-eligible-candidate outcome
stops selection and reports the evidence, limitations, and questions.

**HR-2 — Pre-population gate.** Michael independently reviews and approves together
the detailed endpoint determination, exact OHT identity/version, applicability
rationale, reporting unit, selected study/chemical/source case, and any ambiguity
affecting population. Materially unresolved foundations prohibit population.
The approval record identifies what was reviewed, source/OHT versions, decision,
reviewer, time, and approved output/basis version. An approval cannot bypass the
authoritative-template retrieval/verification requirement.

**HR-3 — Complete review and acceptance.** For the first selected case Michael
reviews every populated assertion/value and every relevant unpopulated-field
disposition, including mappings, provenance, transformations, gaps, and conflicts.
He must inspect original supporting content for claims depending on it. If the
original is no longer inspectable, summaries, extractions, or later replacements
do not make review complete. A retained exact inspected original is usable;
an extracted representation is not that original. Record findings and acceptance
or rejection/incompleteness for the exact output version. After correction the
complete first-case review requirement remains; acceptance must cover the complete
current version rather than only a sample of changed fields. Scientific adequacy
and final authorization remain separate decisions, with criteria unresolved.

**EV-1 — First-case correctness evaluation.** Combine independent confirmation
at gate 2 with complete review at phase F. Record at least these error classes
separately: unsupported fills; incorrect source-to-field mappings; missed available
information; missed gaps; incorrect field dispositions; provenance/locator failures;
transformation errors. Keep findings traceable to output versions and affected
fields/evidence. Preserve the original result, findings, and corrected/reference
result where produced for reproducible comparison. Do not invent numerical
performance or population-coverage thresholds.

### Runtime, security, and non-functional requirements

**RS-1 — Existing SURF target.** The eventual workflow runs within the existing
SURF Research Cloud development workspace. Verify actual network/browser/download,
storage/retention, local parsing/OCR/tooling, and processing capabilities before
depending on them. The repository's hello-world deployment and engineering skills
do not establish a scientific workflow architecture or its runtime capabilities.
No reprovisioning, infrastructure redesign, or GPU/VM sizing is prescribed.

**RS-2 — External processing boundary.** No source content may leave SURF for an
external service/model by default. Original publication retrieval from an allowed
source is distinct from sending retrieved content to a processing provider;
do not transmit source content through discovery, telemetry, logging, or another
channel as an unnoticed processing exception. Before any such transmission,
separately define permitted destination/provider, content classes, artefacts that
may/may not leave SURF, contractual/licensing/privacy restrictions, whether excerpts,
documents, metadata, or derived text may be sent, provider retention/logging, and
required service/model/version provenance. Respect each artefact individually.
Prefer local processing where practical; provider/model selection remains open.
Unavailable external approval must not silently be replaced by provider defaults.

**NF-1 — Inspectability and reproducibility.** Intermediate review artefacts must
remain inspectable and the stages resumable. Preserve exact versions and the
basis of each approval; later stages cannot silently invalidate or bypass earlier
approval. Retention limitations and failed inspections remain visible. Reproducible
discovery means an accountable procedure, not guaranteed identical future search
results. Reproducible transformations retain their inputs, locations, methods,
rules, versions, and products as available. No quantitative runtime, volume, or
performance target is invented; record actual effort and source volume.

### Outcome and failure contracts

| Situation | Required outcome / continuation rule |
| --- | --- |
| Agreed inventory procedure executed and logged for all three leads | Inventory completion, with source coverage/access limitations and partial findings explicit. It is not exhaustive internet coverage. |
| Inventory supports a candidate | Successful inventory with evidence-supported recommendation; wait at gate 1. |
| Inventory supports no eligible candidate | Successful inventory with documented no-eligible-candidate outcome; stop deeper processing. |
| Discovery procedure interrupted or incomplete | Incomplete inventory with unfinished scope visible; resumable, not declared complete. |
| Inspection/download/extraction failure | Log failure and affected evidence limitations; continue independent work only where the approved stage is not blocked. Never convert failure to absence or non-applicability. |
| Pending or materially unresolved foundational approval | Pause at the relevant human gate; no population through unresolved foundations. |
| Authoritative OHT cannot be retrieved or identity/version/structure is insufficiently verified | Documented blocked attempt; no population or inferred replacement structure. |
| Verified OHT and approved reporting case have no source-supported applicable OHT field components that can be populated | Documented blocked attempt, never a successful partial populated draft. Require complete relevant-field/component accounting, provenance, inspection logs, gaps/conflicts, and approval/review records. |
| Local field conflict without undermining approved foundations | Preserve conflict assertions, leave disputed values unpopulated, continue unaffected fields. |
| Conflict/change undermines an approved foundation | Pause deeper processing and return to the relevant human gate. |
| Original supporting content cannot be inspected for review | Affected source-fidelity review remains incomplete; no success declaration relying on that incomplete review. |
| Review identifies errors or correction is pending | Preserve result/findings, produce separate correction where appropriate, perform required re-review; do not declare acceptance prematurely. |
| External processing attempted without defined permission or contrary to an artefact restriction | No transmission; record the unmet boundary and continue permitted local/independent work only. |
| Michael accepts the exact output with the deeper-success conditions met | Record successful populated draft or successful partial populated draft distinctly. Neither is scientific authorization. |

Deeper-success conditions are verified authoritative OHT identity/version and
structure; approved reporting unit/source case and passed pre-population gate;
nonzero source-supported population of applicable OHT field components; inspected
evidence for every populated assertion; accounting for every relevant field and
component by population or explicit disposition; complete provenance and gap/conflict
reporting; and Michael's accepted source-fidelity review.

A partially populated field containing at least one supported applicable component
counts as population even if no field is fully populated. Gap explanations,
workflow metadata, provenance metadata, and disposition-only records do not
themselves count as populated OHT content. Nonzero supported population remains
eligible for successful partial-draft acceptance when the other success conditions
are met; no additional count or percentage threshold is introduced. Apply the
populated-versus-partial label distinction consistently with the verified OHT's
applicable field/component accounting.

For a verified OHT and approved reporting case, zero source-supported populated
OHT field components means a documented blocked attempt, not a successful partial
populated draft. Complete relevant-field/component accounting, provenance,
inspection logs, gaps/conflicts, and approval/review records remain required.
Documented blocked attempts are distinct from successful population runs.

## Testing Decisions

### Proposed test seam and prior art

Propose one public workflow boundary: approved run inputs and staged invocation/
resumption with explicit human decisions in; reviewable packages, stage/outcome
transitions, and observable retrieval/transmission effects out.

The public acceptance boundary comprises defined run inputs and human decisions;
observable stage outputs and outcome transitions; provenance and discovery-log
artefacts; approval state and version bindings; and field/component dispositions.
Required retrieval and transmission behavior is also observable. Internal
single-agent, multi-agent, or hybrid architecture is outside this acceptance
boundary. Required actor/tool/model provenance remains part of the observable
artefacts.

Tests exercise external behavior at this highest practical seam. Source retrieval,
extraction, review decisions, and runtime/provider availability can be controlled
fixtures behind that boundary without prescribing production modules or agent
topology.

The repository currently contains documentation, workflow skills, and a SURF
hello-world playbook; no substantive scientific workflow implementation or
application test suite was found. There is no established application seam or
scientific test prior art to reuse. Michael must accept the proposed boundary
before implementation tickets are generated. A test framework, language, and
concrete calling convention remain to be selected later.

Good tests prove observable package contents, provenance links, stage ordering,
gate enforcement, conflict/failure semantics, version history, and forbidden
transmission behavior. They do not assert prompts, internal agent counts, parser
implementation details, or hidden execution order beyond required gates. Use
clearly marked artificial fixtures to exercise supported values, unsupported
components, conflicting passages, restricted retention, and changed versions;
they are not scientific evidence about the three real leads or the actual OHT.
Live source audit and Michael's review separately establish real-case support.

### Acceptance criteria

These criteria define implementable observable obligations and later human
acceptance evidence. They are not results of tests run during specification.
For each fixture scenario, inspect the resulting package and recorded decisions/
effects; compare to the fixture's declared evidence and expected dispositions.

| ID | Scenario and required observable result | Requirements |
| --- | --- | --- |
| AC-01 | Start with the approved three seeds/configuration and no study/chemical. All three have inventories and preliminary findings before recommendation; no method/case is silently preselected. | FR-1–6, HR-1 |
| AC-02 | Run a bounded plan. The package preserves all declared plan items, actual searches, inspected/skipped results, links, timestamps, failures, and refinements/reasons. Completion occurs only after scope execution; interruption remains incomplete. | FR-2–3, NF-1 |
| AC-03 | Refine a query within scope and request an out-of-scope search. The former is logged; the latter does not execute without recorded Michael approval. Actual effort and source volume are recorded without an invented cap. | FR-2–3 |
| AC-04 | Supply heterogeneous artefacts, raw data absent, and an inaccessible reference. Types and access/version/reuse restrictions remain distinguishable; no raw data is invented and the reference is not called inspected. | FR-3, DP-1, SE-5 |
| AC-05 | Provide distinct endpoint terms, incomplete relationships, and similar OHT names without authoritative scope support. Preserve terms/unknowns; do not infer relationships, applicability, detailed mapping, or population before selection. | FR-4, SE-1 |
| AC-06 | Compare incomplete-accessible and richer-inaccessible cases. Report the four source-linked dimensions separately without an aggregate score or scientific-quality judgment. Coverage describes categories, not preselection field mapping. | FR-5 |
| AC-07 | No candidate has demonstrable applicability after completed bounded inventory. Produce a supported successful no-eligible-candidate inventory and stop; do not force a selection. | FR-5, HR-1 |
| AC-08 | A recommendation exists but gate 1 is absent or rejected. No deeper processing occurs. Recorded Michael approval of reviewed versions permits only the next allowed stage. | FR-1, HR-1 |
| AC-09 | Candidate cases include general protocol material, separate studies, or chemicals. Show identity, reporting-unit fit, support, limitations, and boundaries; no silent cross-case merge or unsupported protocol-to-study-result fill occurs. | FR-6, SE-1 |
| AC-10 | Gate 2 is missing or a foundation is materially unresolved. No population occurs. First-case independent confirmation records all five foundations and their evidence/versions. | HR-2, FR-6–7 |
| AC-11 | Authoritative OHT retrieval fails or identity/version/structure verification is insufficient, even with other evidence or a prior approval. Produce a documented blocked attempt; no template population or successful-population label. | FR-7, HR-2 |
| AC-12 | A sparse case has nonzero source-supported population of applicable OHT field components and verified OHT/case approvals. Every relevant field/component is keyed to actual structure and populated or explicitly accounted for. Successful partial-draft acceptance remains possible when the other success conditions are met, without an additional count or percentage threshold or native export. | FR-7, DP-3, HR-3 |
| AC-13 | A field has a supported applicable value component but missing unit/condition/qualifier. Evidence supports each populated component; population is partial and missing components/reasons are explicit. This field counts as population even if no field is fully populated. Gap explanations, workflow metadata, provenance metadata, and disposition-only records do not themselves count as populated OHT content. Missing scientific/metadata values are not fabricated. | DP-2–3, FR-7 |
| AC-14 | Multiple sources/passages support one field. Preserve one assertion per inspected artefact per record, separate different artefacts, link multiple records where needed, and retain locators, summaries, interpretations, and uncertainties distinctly. | DP-2, SE-5 |
| AC-15 | Missing, not-checked, inaccessible, qualified, and non-applicable components coexist. Keep status dimensions separate and locators/findings linked where available; non-applicability requires authoritative support. | DP-3 |
| AC-16 | Two inspected sources conflict locally. Preserve both assertions and provenance, mark ambiguity, leave disputed values unpopulated, and continue unaffected fields. A foundation conflict pauses and reopens the relevant gate. | SE-3, HR-1–2 |
| AC-17 | Native extraction is adequate, another artefact needs OCR, and a value needs a unit conversion. Use native extraction preferentially; label OCR with location/method; retain conversion originals, target units, rule, and result. Parsing/validation is reproducible and traceable. | SE-4, DP-4 |
| AC-18 | Summary-only support, inferred values, silent derivations, and an unapproved scientific calculation are proposed. They cannot populate fields. An explicitly Michael-approved defined deterministic field-specific scientific transformation remains separately labelled and traceable. | SE-2, SE-4 |
| AC-19 | Retention is permitted for one artefact and prohibited/impossible for another. Retain exact allowed originals/OHT with identity, version/date, retrieval metadata, artefact ID, hash, and restrictions; record limitations/available retrieval metadata for the other. Extractions never replace originals. | DP-1, DP-4 |
| AC-20 | Attempt processing transmission of documents, excerpts, metadata, or derived text without defined permission, or with permission for a different artefact. No such transmission occurs. Any separately permitted destination/content respects per-artefact restrictions and records service/model/version provenance. | RS-2 |
| AC-21 | Interrupt and resume around gates, and observe changed remote content. Preserve inspection records, intermediate artefacts, source/OHT versions, and approval basis. Replacement becomes a distinct version and cannot silently inherit approvals. | DP-5, NF-1 |
| AC-22 | Supporting original becomes inaccessible for Michael, leaving an extraction or later replacement. Affected source-fidelity review is incomplete; no accepted-success claim is made solely from those substitutes. | HR-3, DP-1, DP-5 |
| AC-23 | Perform first-case evaluation, then correct a result. Preserve original output, findings by every required error class, and corrected/reference result separately. Review all affected content and complete the first-case review of all current assertions/dispositions; foundational changes reopen approval and acceptance names the exact version. | HR-2–3, EV-1, DP-5 |
| AC-24 | A runtime prerequisite is unavailable/unverified. Report the affected stage/requirement and independent permissible work; do not assume network/browser/tool capability, select a provider, or reprovision infrastructure to hide the block. | RS-1–2 |
| AC-25 | Present completed packages and outcomes. Distinguish successful populated draft, successful partial populated draft, and documented blocked attempt using verified applicable OHT field/component accounting. For a verified OHT and approved reporting case with zero source-supported populated OHT field components, require a documented blocked attempt, never successful partial population, with complete relevant-field/component accounting, provenance, inspection logs, gaps/conflicts, and approval/review records. Include rationale, ledger, manifest, gaps/conflicts, approval/review summary, and retained authoritative OHT where permitted. Never label these scientific adequacy or regulatory authorization. | FR-7, DP-3–4, HR-3, SE-5 |

### Real first-case acceptance evidence

After an authorized source audit and implementation, Michael must independently
confirm the real foundations before population and review the entire real first
case afterward. The evidence for acceptance includes all three inventories,
logged bounded discovery, comparison and gate decisions, exact verified template,
approved reporting case, draft and field accounting, inspectable original support,
provenance/transformations, error findings, correction history where produced,
and accepted output version. Passing fixture tests does not verify real TSAR
validation status, establish actual OHT applicability, or substitute for that
human review. Source audit may legitimately establish no eligible candidate or
a documented block; those results must be assessed by the defined outcome rules.

## Out of Scope

- Automatic scientific-adequacy or regulatory conclusions and final scientific
  authorization; those remain separate human scientific decisions.
- Inventing missing scientific/metadata values, unsupported claims, or inferring
  missing scientific values to complete a field.
- Exhaustive internet discovery, unrestricted searching, arbitrary initial
  search/download caps, and secondary-source exceptions for population.
- Silent conflict resolution, synthesized disputed values, silent source/case
  substitution or case aggregation, or uncontrolled external processing.
- eLabNext dependency, OMBION Dashboard integration, production deployment, SURF
  reprovisioning/infrastructure redesign, and GPU/VM sizing selection.
- No production writes to unrelated systems. The MVP may not write to unrelated
  production services or systems unless separately and explicitly authorized in
  a later scope decision.
- Mandatory native-format OHT export, a dedicated UI without demonstrated need,
  and premature LLM/provider or single-agent/multi-agent architecture selection.
- Processing the additional thyroid-method leads tm2019-06, tm2019-09, and
  tm2019-10 in MVP v0; their supplied partial-validation context is not independently
  verified here.
- Autonomous `implement-spec` execution; repository single-ticket, review, and
  acceptance policy remains in force for later authorized implementation.
- Implementation, prototypes, ticket generation, code review, retrospectives,
  commits, pushes, merging, PR creation, GitHub issues/labels, and external source
  auditing during this specification-only invocation.

## Further Notes

### Open verification tasks and effect on readiness

These are unverified facts or deferred decisions, not assumed successful outcomes.
An authorized audit records inspected evidence, limitations, and possible blocked
results. Do not fabricate scientific acceptance facts to make a task appear ready.

| Open item | Evidence or decision required later | Consequence if unresolved |
| --- | --- | --- |
| Actual sources/data for each lead | Bounded inventory of accessible and referenced artefacts, inspection/access results, source volume and effort. | Comparison reports unknowns/limitations; failures cannot imply absence. |
| Authoritative validation status | Original/authoritative validation documentation and precise support. | Supplied validated status remains labelled context; no invented verification. |
| Endpoint evidence and relationships | Source terminology and passages supporting each determination/relationship. | Unknown relationships remain unknown; material foundational uncertainty blocks population. |
| Exact OHT applicability, identity/version/status, structure | Authoritative scope/template documentation and retrieved sufficiently verified representation. | Preliminary candidate uncertainty remains explicit; unresolved detailed foundations or unavailable/unverified template block population. |
| OHT/source access, licensing, reuse, retention | Per-artefact terms/conditions and technical retention feasibility. | Respect restrictions, retain permissible metadata, and identify review limitations. |
| Reporting unit and concrete source case | Verified OHT semantics, identifiable source case evidence, and Michael's approval. | No assumption that method protocol equals study/chemical results; no population without approval. |
| Actual SURF network/browser/download capability | Verification within the existing authorized workspace. | No reliance on unavailable capability; document stage impact. |
| Local parsing/OCR/tooling, storage and processing capability | Capability inspection and extraction feasibility with relevant versions. | Choose tooling only after verification; record inaccessible/unextractable evidence. |
| External processing policy and model/provider | Separate destination/content/per-artefact/contract/privacy/licensing/retention/provenance decisions. | No external source transmission by default; do not fix a provider in this spec. |
| Scientific adequacy criteria | Later human scientific requirements and authorization. | Source-fidelity acceptance remains scientifically bounded. |

### Human review before to-tickets

The required behavior is specified without selecting an agent architecture or
scientific case. Michael must review the proposed public testing seam and confirm
that the acceptance scenarios match the intended workflow. This is the skill's
test-seam expectation check, presented with the concrete draft for human review.
No implementation tickets may be generated before specification review.

Concrete serialization, invocation/approval recording convention, storage layout,
source/OHT adapters, and test framework are deferred technical choices. The
field/disposition vocabulary is a required minimum; actual field/component and
relevance rules must follow the audited OHT, not invented generic fields.
The human-approved classification convention is based on source-supported
applicable OHT field components: a supported component in a partially populated
field counts as population; gap explanations, workflow metadata, provenance
metadata, and disposition-only records do not themselves count as populated OHT
content. Nonzero supported population is eligible for successful partial-draft
acceptance when the other success conditions are met, with no additional count
or percentage threshold. For a verified OHT and approved reporting case, zero
supported fills is a documented blocked attempt requiring complete relevant-field/
component accounting, provenance, inspection logs, gaps/conflicts, and approval/
review records. Apply populated-versus-partial labels consistently with verified
applicable OHT field/component accounting. Success requirements, human review
gates, and blocked-template behavior remain binding.

No agreed requirement requires an architecture choice or a fabricated scientific
fact to translate into this contract. Exact scientific fields, actual source
permissions, concrete cases, and runtime capabilities cannot be fixed cleanly
without the stated audit; their verification dependencies remain explicit.
Any later ticket must identify its applicable acceptance criteria, parent spec,
and unresolved blockers. This document does not generate that breakdown.

### Requirements traceability

| Requirements interview decision group | Specification coverage |
| --- | --- |
| Round 1: reviewer, all-three inventory, endpoint distinctions | FR-1, FR-3–5, SE-1, HR-1, HR-3, AC-01/05/08 |
| Round 2: reporting unit, discovery sources, separate dimensions, selection authority | FR-2, FR-5–6, SE-1–2, HR-1, AC-06–09 |
| Round 3: preliminary applicability, inventory success, discovery bounds, no secondary exception | FR-2–5, SE-2, outcome contracts, AC-02–07/18 |
| Round 4: outputs, assertion provenance, states, approval gates | FR-7, DP-1–4, HR-1–3, AC-10–15/25 |
| Q16: sparse success and documented OHT block | FR-7, deeper-success/outcome contracts, AC-11–12/25 |
| Q17: independent confirmation, complete evaluation, error classes, history | HR-2–3, EV-1, DP-5, AC-10/23 |
| Q18: exact-source/OHT retention and original inspectability | DP-1, DP-4–5, HR-3, AC-19/22 |
| Q19: traceable permitted transformations | SE-4, AC-17–18 |
| Q20: conflicts and foundational approval return | SE-3, HR-1–2, AC-16 |
| Q21: correction versions, all affected review, exact acceptance | DP-5, HR-2–3, EV-1, AC-23 |
| Q22: default external prohibition and separately defined boundaries | RS-2, AC-20 |
| Q23: staged resumable workflow, version-bound approvals, inspectability | FR-1, NF-1, HR-1–3, AC-08/10/21 |
| Q24: separate statuses and component accounting | DP-3, AC-13/15 |
| Q25: declared plan, execution log, refinements/scope approval | FR-2–3, AC-02–03 |
| Q26: four comparison dimensions with no score/adequacy judgment | FR-5, AC-06 |
| Q27: initial inputs and identifiable case proposals | FR-1, FR-6, SE-1, AC-01/09 |
| Q28: failure semantics, preserved versions, changed-source review | DP-3, DP-5, HR-3, outcome contracts, AC-15/21–22 |
| Existing domain boundaries and deferred verification | SE-1–5, DP-1–5, RS-1–2, Out of Scope, open verification tasks |

### Publication boundary

The installed `to-spec` process says: "Write the spec using the template below,
then publish it to the project issue tracker." Its normal publication also
applies `ready-for-agent`. This invocation explicitly prohibits GitHub issues,
remote writes, commits, and pushes, so it stops before that step. No issue or
label has been created or changed, and this local draft does not claim human
acceptance or implementation readiness.
