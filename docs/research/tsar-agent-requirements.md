# TSAR agent requirements interview

Status: requirements discovery in progress; not an implementation specification.
Started: 2026-10-06. Interviewee: Michael.
Local branch: `research/tsar-agent-requirements`, from `main` at `3b8abbe`.

## Evidence and decision status

The starting brief below is user-provided direction. Method names and validation
status have not been independently verified in this interview. Repository
vocabulary comes from [GLOSSARY.md](../../GLOSSARY.md); workflow policy comes from
[workflow-experiment.md](../agents/workflow-experiment.md). Recommendations and
unanswered questions are not decisions. No external source audit has been run.

## Starting brief and constraints

Investigate an agent or agentic workflow in the existing SURF Research Cloud
workspace that receives a TSAR method lead, inventories inspected source
artefacts, determines intended endpoints from authoritative evidence, identifies
and retrieves an applicable OECD Harmonised Template (OHT), and populates it only
with source-supported information. Ambiguous template applicability must be
surfaced. Neither raw-data availability nor an endpoint definition is assumed.

The user identifies these as the initial three validated-method leads:

| TSAR ID | User-provided method name | Source lead |
| --- | --- | --- |
| tm2010-07 | Transactivation assay for detection of androgenic activity of chemicals | https://tsar.jrc.ec.europa.eu/test-method/tm2010-07 |
| tm2008-05 | Human Cell Line Activation Test (h-CLAT) | https://tsar.jrc.ec.europa.eu/test-method/tm2008-05 |
| tm2009-06 | Direct Peptide Reactivity Assay (DPRA) | https://tsar.jrc.ec.europa.eu/test-method/tm2009-06 |

The other user-provided leads, `tm2019-06`, `tm2019-09`, and `tm2019-10`, remain
conceptually relevant but outside the initial focus unless Michael changes scope.

Preserved boundaries:

- No invented scientific data or unsupported scientific claims.
- No autonomous scientific adequacy conclusion; human scientific authorization
  remains separate from source support and source-fidelity review.
- No silent source substitution or resolution of conflicting evidence.
- An LLM interpretation or other transformation product is not an independent
  scientific source.
- No production writes to unrelated systems, eLabNext dependency, or assumption
  that the OMBION Dashboard is this workflow's frontend.
- Design for the existing SURF workspace; no infrastructure redesign or
  reprovisioning. Model and architecture selection remain open.
- No source content may be sent to an external service or model by default.
  External processing requires the explicit boundaries defined in Q22 below.
- During this session: no implementation, formal spec, issues, labels, commits,
  pushes, or mass source downloading/extraction. Do not invoke subsequent
  workflow stages. Michael explicitly determines when the grill is sufficient.

## Existing domain decisions to preserve

The glossary distinguishes source artefacts, source excerpts, assertion
summaries, interpretations, source provenance, and record-creation provenance.
An evidence record attributes one assertion to one inspected source artefact;
assertions from different artefacts remain separate records. Source-expressed
uncertainty and extraction/transformation uncertainty are separate concepts.
Non-reporting in inspected material does not establish absence elsewhere.
Source-fidelity review requires inspection of original supporting content and
applies to the reviewed record state; relevant changes require fresh review.
Scientific adequacy remains a separate unresolved review dimension.

## Interview decisions

### Round 1: reviewer, staging, and endpoint distinctions

Decided by Michael:

- Michael is the primary scientific reviewer for first MVP runs. Outputs should
  support inspection of available source material, review of a source-traceable
  draft, identification of missing or inaccessible information, and decisions
  about further investigation or input from Ingrid. Scientific adequacy and
  final scientific authorization remain separate from this workflow.
- First inventory all three initial leads. Then select one for deeper processing
  based on source availability, source quality, and demonstrable OHT
  applicability. No method is selected in advance.
- Keep assay readout, biological endpoint, regulatory endpoint, and OECD
  reporting endpoint conceptually separate. Preserve terminology actually used
  by authoritative sources. Establish relationships only when supported by
  those sources; do not require all four categories for every method. Unresolved
  relationships remain explicitly unresolved.

Open at the end of round 1 (some resolved in round 2):

- Definitions of the individual endpoint concepts and the reporting unit of a
  populated OHT.
- Meaning of source quality for selection, its assessment, and the authority to
  select a method after inventory.
- Source discovery boundaries and criteria for authoritative sources.
- Mandatory outputs, success criteria, and the remaining branches below.

Assumptions explicitly rejected:

- Preselecting a method before the three-method inventory.
- Treating source support or source-fidelity review as scientific adequacy or
  final scientific authorization.
- Collapsing the four endpoint concepts, inferring unsupported relationships,
  or forcing every method into all four categories.

### Round 2: reporting unit, sources, comparison, and selection authority

Decided by Michael:

- Determine the reporting unit from authoritative OHT documentation before
  population. Keep method/protocol information, individual-study information,
  and chemical-specific observed results explicitly separated. A partial draft
  is useful when the template requires study-specific information but only
  general protocol material is available: unsupported fields stay explicitly
  unpopulated and the limitation is reported. Map protocol information into
  study-result fields only if the source and template semantics support it.
- Allowed discovery includes TSAR and directly linked material; targeted
  searches of authoritative bodies including OECD, JRC/EURL ECVAM, and relevant
  regulatory or validation organizations; and relevant identifiable original
  publications or original method-owner documentation.
- Secondary summaries may serve as discovery leads. They should not normally
  populate fields when an authoritative or original source is available. Every
  populated value retains claim-specific provenance to its supporting source.
  Exception rules and behavior when originals are unavailable remain open.
- Compare source availability, traceability, extractability, and reporting
  coverage separately. Do not combine them into an opaque quality score.
  Scientific quality or adequacy is a separate human judgment, outside automated
  method selection. Accessible but incomplete material remains distinguishable
  from richer material that is difficult to access or extract.
- After the three-method inventory, present a comparison, evidence for each
  candidate, and a recommendation. Michael must approve the selected method
  before deeper endpoint/OHT/population work continues.
- If no candidate has demonstrable OHT applicability, stop and report the
  evidence, gaps, and unresolved questions; do not automatically select a method.

Open at the end of round 2 (some resolved in round 3):

- Depth of preliminary endpoint/OHT checking permitted during inventory to
  demonstrate applicability before the selection approval gate.
- Required inventory outputs and criteria for a successful inventory, including
  the outcome when no candidate is eligible for selection.
- Discovery stopping conditions and secondary-source exception policy.
- Operational definitions of comparison dimensions and remaining branches below.

Assumptions explicitly rejected:

- Copying protocol information into study-result fields without semantic support.
- Requiring a fully populated template for a draft to be useful.
- An opaque overall source-quality score or automated scientific adequacy rating.
- Automatically selecting a method or bypassing Michael's selection approval.
- Selecting a method when none has demonstrable OHT applicability.

### Round 3: applicability screening, inventory success, and discovery bounds

Decided by Michael:

- Before selection, permit preliminary source-supported endpoint investigation
  and inspection of authoritative OHT scope documentation. For each candidate,
  record source-supported endpoint terminology; candidate OHT identity and
  version if identifiable; authoritative OHT source; supporting passages or
  precise applicability evidence; and ambiguities, conflicts, or unresolved
  applicability questions. This establishes suitability for comparison only.
  Detailed field mapping and population wait for Michael's method approval.
  Name similarity alone never establishes applicability.
- A successful inventory covers all three initial leads with source/artefact
  inventories; separate availability, traceability, extractability, and reporting
  coverage findings; preliminary endpoint/OHT applicability findings; visible
  gaps, access failures, conflicts, and uncertainty; and a comparison with a
  recommendation or a documented conclusion that no candidate currently
  qualifies. A well-supported no-eligible-candidate outcome is successful; it
  must not be manufactured into an eligible candidate to continue.
- Execute and log a bounded, reproducible first-pass discovery plan for each
  lead: inspect the TSAR record; all directly accessible, relevant TSAR-linked
  artefacts concerning methods, validation, studies, endpoints, or reporting;
  targeted authoritative searches needed for endpoint/OHT applicability,
  primarily OECD and JRC/EURL ECVAM or another clearly relevant official body;
  and identifiable original publications or method-owner documents referenced
  by authoritative material or needed to resolve a specific inventory question.
- Stop once that predefined scope has been executed and logged. Explicitly
  report uninspected references, inaccessible artefacts, unresolved leads, and
  additional searches needed. Label results partial where appropriate.
  Inventory completion means completion of the agreed discovery plan, not
  exhaustive internet coverage. No unrestricted general web search is allowed
  in the first inventory.
- Do not impose an arbitrary time/download limit yet. Record actual effort and
  source volume to inform later operational limits.
- No secondary-source population exception in this MVP. If a secondary source
  points to information whose supporting original/authoritative source cannot
  be inspected, keep the OHT field unpopulated, retain the secondary as a discovery
  lead, identify the unavailable original where possible, and record access
  limitations and uncertainty. Exceptions may be evaluated in a later scope.

Open at the end of round 3 (some resolved in round 4):

- Required outputs and success criteria for deeper processing and partial drafts.
- Provenance granularity and representation, missing-information states, and
  review gates after method selection.
- Discovery-log detail, executable search-plan inputs, reporting-coverage
  assessment before detailed mapping, and treatment of inspection failures.
- Operational definitions of comparison dimensions and remaining branches below.

Assumptions explicitly rejected:

- Detailed field mapping or population before method-selection approval.
- Name similarity as sufficient OHT applicability evidence.
- Equating completed discovery scope with exhaustive source coverage or complete
  source availability.
- Requiring an eligible candidate for inventory success.
- Unrestricted first-pass searching, arbitrary initial time/download caps, and
  secondary-source exceptions for population in this MVP.

### Round 4: draft outputs, assertion-level provenance, states, and review gates

Decided by Michael:

- After method approval, deeper processing must produce the authoritative OHT
  or authoritative template representation; endpoint/applicability rationale;
  approved reporting unit and selected source case; a populated draft keyed to
  actual OHT fields; a field/assertion-level evidence and provenance ledger;
  explicit gap/conflict report; run manifest; and human-review summary. Related
  reports may be combined if reviewability improves and traceability is intact.
  Retain the retrieved authoritative template. Native-format export is not
  required for this MVP pending inspection of actual authoritative formats.
- Provenance is required at assertion/value level, including separate support
  for values, units, conditions, and qualifiers where needed. One field may
  reference multiple evidence records. Preserve the existing rule: one record
  attributes one narrowly scoped assertion to one inspected source artefact.
- Each evidence record should contain, where available: source identity/title;
  location; version/publication date; retrieval/access date; precise page,
  section, table, row/cell, or equivalent locator; exact excerpt or relevant
  table content where legally/technically retainable; source-supported assertion
  or value; separate summary/interpretation; extraction/transformation history;
  relevant tool/model/version; and human correction/verification. The manifest
  describes inspected sources, versions, retrieval dates, tools/models, and
  processing steps.
- Represent source/access status, field-population status, and uncertainty/
  conflict status as separate dimensions. Initial vocabulary includes not
  reported in inspected material, not yet checked, referenced but unavailable,
  inaccessible, ambiguous/conflicting, and not applicable. Conditions may
  coexist. Exact assignment of vocabulary to dimensions and supported/partial
  population states remains to be detailed.
- Not-applicable findings need support from OHT semantics or authoritative
  method documentation; missing evidence alone never suffices.
- After method selection, Michael must approve together the detailed endpoint
  determination, exact OHT identity/version, applicability rationale, reporting
  unit, selected study/chemical/source case, and any unresolved ambiguity that
  could affect population. Pause if applicability, reporting unit, or source-case
  selection remains materially unresolved. Population begins only after this
  gate is passed.
- After population, Michael reviews source fidelity, provenance completeness,
  gaps, conflicts, and unsupported mappings. Successful population or
  source-fidelity review does not imply scientific adequacy or final scientific
  authorization; those remain separate human decisions.

Open at the end of round 4 (some resolved in round 5):

- Deeper-run success criteria, evaluation cases/procedure, and acceptance rules.
- Source snapshots, retention/access constraints, reproducibility, and how to
  preserve reviewability when original content cannot be retained or accessed.
- Allowed transformations and local field-conflict behavior after the pre-fill
  gate; corrections and approval invalidation.
- Runtime, interaction, and other operational branches below.

Assumptions explicitly rejected:

- Whole-template or whole-field provenance as sufficient granularity.
- Mandatory native-format export before authoritative formats are inspected.
- One mutually exclusive status for every missing/disputed field.
- Not-applicable as a substitute for missing evidence.
- Population before the second approval gate or through materially unresolved
  applicability, reporting-unit, or source-case decisions.
- Source-fidelity review or successful population as scientific authorization.

### Round 5: deeper-processing success, correctness, retention, and transformations

Decided by Michael (Q16–Q19):

**Q16 — Deeper-processing success**

- A sparse partial draft can be a successful deeper-processing run. Do not
  introduce a numerical population-coverage threshold for the first MVP.
- Success requires verified authoritative OHT identity/version and structure;
  Michael's approval of the reporting unit and source case; inspected evidence
  supporting every populated assertion; every relevant OHT field accounted for
  by population or an explicit field disposition; complete provenance and
  gap/conflict reporting according to the agreed MVP requirements; and Michael's
  acceptance of the post-population source-fidelity review. The existing
  pre-population approval gate remains required.
- Keep three outcomes distinct: successful populated draft, successful partial
  populated draft, and documented blocked attempt. If the authoritative OHT
  cannot be retrieved or its structure cannot be sufficiently verified, do not
  populate it. Record a documented blocked outcome; this is not a successful
  population run.

**Q17 — Correctness evaluation**

- For the first selected case, combine independent pre-population confirmation
  with complete post-population review. Before population, Michael independently
  reviews endpoint determination, OHT identity/version, applicability rationale,
  reporting unit, and the selected study/chemical/source case.
- After population, review every populated assertion/value and every relevant
  unpopulated-field disposition for that first case.
- Record error classes separately, including unsupported fills, incorrect
  source-to-field mappings, missed available information, missed gaps, incorrect
  field dispositions, provenance/locator failures, and transformation errors.
- Do not overwrite the original agent result during evaluation. Preserve the
  original agent output, reviewer findings, and any corrected/reference result
  separately, enabling reproducible comparison with human-reviewed material.

**Q18 — Source retention and reproducibility**

- Retain the exact inspected source artefacts and exact authoritative OHT version
  used for mapping and review where legally and technically permitted.
- For each retained artefact, record at least source identity/title, original
  location/URL or identifier, version/date where available, retrieval date,
  locally retained filename or artefact identifier, content hash, and applicable
  retention/access/licensing restriction.
- Keep extracted representations and transformation metadata separate from the
  original. Extracted or transformed representations never replace original
  sources as provenance.
- If an artefact cannot legally or technically be retained, explicitly record
  that limitation and retain sufficient identity, locator, retrieval, and
  provenance metadata for independent retrieval where possible.
- If Michael can no longer inspect the supporting original, source-fidelity
  review of claims depending on that artefact cannot be considered complete
  merely because extracted or summarized content remains available.

**Q19 — Permitted transformations**

- Allow only explicit, reproducible, traceable transformations. Prefer native
  machine-readable/text extraction where available. Use OCR only when reliable
  native extraction is unavailable or insufficient; explicitly label OCR-derived
  content and retain the source location and extraction method.
- Faithful summaries may assist review and mapping, but stay separate from source
  excerpts and never become independent evidence.
- Mechanical unit conversions are permitted when needed. Retain the original
  value/unit, target unit, conversion rule/formula, and result. Deterministic
  parsing and validation are permitted and preferred where applicable.
- Do not infer missing scientific values. Do not calculate new scientific results
  for population in the first MVP unless Michael explicitly approves a defined
  deterministic transformation required for a specific OHT field. Never present
  a derived value as though it were directly reported by the source.

Open at the end of round 5 (some resolved in round 6):

- Field-level conflicts and ambiguity discovered after pre-population approval;
  correction behavior, approval invalidation, and review of changed outputs.
- SURF runtime capabilities and external-service constraints; invocation inputs,
  resumability, and interaction points.
- Remaining operational detail for discovery plans, comparison dimensions,
  field dispositions/status vocabulary, and source-case selection.

Assumptions explicitly rejected:

- A minimum percentage of populated OHT fields as an MVP success requirement.
- Treating an unavailable or insufficiently verified authoritative OHT as a
  successful population run, or proceeding with population despite that block.
- Sampling the first case's populated assertions or relevant field dispositions
  instead of reviewing all of them.
- Overwriting original agent output with evaluation corrections.
- Substituting extracted/summarized content for original-source provenance or
  treating it as sufficient for source-fidelity review of an unavailable original.
- Unlabelled OCR, untraceable transformations, inferred missing scientific values,
  unapproved new scientific calculations, or derived values represented as reported.

### Round 6: conflicts, corrections, external boundaries, and staged interaction

Decided by Michael (Q20–Q23):

**Q20 — Conflicts after approval**

- Preserve conflicting assertions separately, each with its own provenance. Do
  not silently resolve conflicts or populate a disputed field with a synthesized
  value. Explicitly mark the field as conflicting/ambiguous and continue
  population of unaffected fields.
- Pause deeper processing because of a conflict only when it undermines a
  previously approved basis, such as endpoint determination, OHT identity/version,
  applicability rationale, reporting unit, or selected study/chemical/source
  case. Return to the relevant human approval gate before continuing.

**Q21 — Corrections and renewed review**

- Preserve original agent output and subsequent corrections as distinct versions.
  Preserve reviewer findings as already required by Q17.
- When output changes, review all affected assertions/values, field dispositions,
  provenance records, transformations, dependent mappings, and gap/conflict
  conclusions.
- If a correction changes the basis of endpoint determination, OHT selection,
  applicability, reporting unit, or source-case selection, reopen the
  pre-population approval gate. Record the exact output version Michael accepts.
- For the first selected case, complete review of all populated assertions and
  relevant field dispositions remains required after correction.

**Q22 — External processing and data boundaries**

- No source content may be sent to an external service or model by default.
  Before using external processing, explicitly define the permitted destination/
  provider; permitted content classes; source artefacts that may or may not leave
  SURF; contractual/licensing/privacy restrictions; whether excerpts, full
  documents, metadata, or derived text may be transmitted; external-service
  retention/logging behavior; and required service/model/version provenance.
- Respect each artefact's restrictions individually. Prefer local processing on
  SURF where practical until these boundaries are defined.
- Provider/model selection remains open and must not be fixed in this requirements
  phase unless separately approved.

**Q23 — Invocation and interaction model**

- A manually invoked staged workflow is sufficient for the first MVP. Stages
  must be resumable, and approval checkpoints explicit and recorded.
- Preserve the exact source/OHT versions and the basis of each approval. A later
  stage must not silently invalidate or bypass an earlier approval. Intermediate
  review artefacts must remain inspectable.
- No dedicated UI is required for the MVP. Add an interface only if the review
  workflow later demonstrates a concrete need.

Open at the end of round 6 (resolved in round 7 except later verification work):

- Operational definitions of comparison dimensions and the field-status/disposition
  vocabulary; reproducible discovery-plan inputs and inspection logs.
- Invocation inputs and the policy for proposing a study/chemical/source case.
- Failure handling and resumption when sources, extracted content, or approval
  bases change. Actual SURF capability verification and architecture/provider
  choice remain later work, not facts established by this interview.

Assumptions explicitly rejected:

- Silent conflict resolution, synthesized disputed values, or pausing unaffected
  fields solely because an unrelated field conflicts.
- Overwriting original results with corrections, omitting affected transformations
  or gap/conflict conclusions from review, or retaining an approval after its
  basis changes without renewed approval.
- Sampling the first case's review after correction or accepting an unspecified
  output version.
- Sending source content externally by default, treating permission for one
  artefact as permission for all, or fixing a provider/model without separate
  approval during requirements discovery.
- Bypassing prior approvals on resume, losing intermediate review artefacts, or
  requiring a dedicated UI without a demonstrated review need.

### Round 7: field accounting, discovery, comparison, inputs, and resumption

Decided by Michael (Q24–Q28): all five recommendations accepted, with the
following explicit requirements.

**Q24 — Field accounting**

- Population status stays separate from source/access status and uncertainty/
  conflict status. Distinguish at least unpopulated, partially populated, and
  populated for each relevant OHT field.
- For partial population, identify which components are present and which are
  missing, with a reason for each missing component where known. Keep conflicting/
  disputed values unpopulated until resolved.
- Not applicable is a separate disposition requiring authoritative support; it
  is never a synonym for missing information. Where available, link each missing
  or disputed component to the relevant source locator, gap evidence, or inspection
  result. The Q16 requirement to account for every relevant field remains intact.

**Q25 — Reproducible discovery plan and log**

- Before inventory, record a bounded discovery plan containing at least TSAR seed
  URLs/IDs, scoped research questions, allowed authoritative source classes,
  initial search queries, relevance/inclusion rules, exclusion rules where
  relevant, and stopping conditions.
- During execution, log actual queries, results/sources inspected, links followed,
  retrieval/access timestamps, inspection outcomes, access/download failures,
  relevant leads not inspected, and the reason for any query refinement.
- Documented targeted query refinement within scope is allowed. Expansion beyond
  the agreed discovery scope requires Michael's approval. The log must allow a
  reviewer to understand what was searched, inspected, or skipped, and why.
- Preserve the earlier prohibition on unrestricted first-pass searching and the
  decision not to impose arbitrary initial time/download caps.

**Q26 — Comparison dimensions**

- Availability: whether a relevant source artefact can actually be accessed and
  inspected, including access limitations.
- Traceability: whether the source can be uniquely identified/versioned and its
  supporting content precisely located.
- Extractability: whether relevant content can be reliably extracted using native
  text/data access, OCR, or manual extraction, including limitations. Q19's
  extraction preference and OCR restrictions still apply.
- Reporting coverage: which source-supported information categories relevant to
  the prospective reporting unit are available before detailed OHT field mapping.
- Keep findings source-linked and separate. Do not calculate an aggregate score,
  introduce a population threshold, or use these dimensions as an automated
  scientific-quality or scientific-adequacy judgment.

**Q27 — Inputs and source-case proposals**

- Initial input consists of the three agreed validated TSAR leads and the approved
  discovery/run configuration. Their validated status remains user-provided
  direction pending the source audit. Michael need not supply a study or chemical
  case upfront.
- After inventory, method selection, and reporting-unit determination, the
  workflow may propose identifiable candidate source cases. For each case,
  present source identity, why it appears to match the reporting unit, available
  supporting material, limitations/gaps, and any ambiguity about case identity
  or boundaries.
- Michael approves the source case before detailed population, through the
  existing pre-population gate. Additional user-supplied sources remain leads
  until inspected. Never silently combine distinct studies, chemicals,
  experiments, or reporting cases.

**Q28 — Failures and resumption**

- Log failed inspections explicitly and continue independent work where failure
  does not block the approved stage. Failed inspection never means not reported,
  not applicable, or evidence that the content does not exist.
- Preserve the blocking rule when authoritative OHT identity/structure or another
  approved foundation cannot be verified. Do not bypass the applicable approval
  gate or classify a blocked attempt as a successful population run.
- On resumption, use preserved source/OHT versions where available and preserve
  the original inspection record. Treat changed/replaced remote content as a
  distinct source version. Reassess affected assertions, mappings, field
  dispositions, and approvals under Q21's correction/review rules, including
  affected provenance, transformations, and gap/conflict conclusions.
- If original supporting content can no longer be inspected, affected
  source-fidelity review is not complete merely because a later replacement or
  extracted copy exists. A retained exact original remains distinct from an
  extracted representation or a later replacement.

Assumptions explicitly rejected:

- Combining population, access, and uncertainty into a single status; hiding
  missing components of partial fields; or treating not applicable as missing.
- Undocumented query refinements or unapproved discovery-scope expansion.
- Aggregate comparison scores, population thresholds, or automated scientific
  quality/adequacy judgments from inventory comparison dimensions.
- Requiring Michael to supply a case upfront, assuming supplied leads are already
  authoritative, or silently combining distinct reporting cases.
- Interpreting failed inspection as non-reporting, non-applicability, or absence;
  replacing source versions or inspection records silently; or completing review
  of unavailable originals using only replacements or extracted content.

## Open decision tree

Current policy frontier: no unanswered questions from Q1–Q28. Michael has
accepted Q24–Q28; no additional requirements round is being introduced merely
to repeat settled decisions. The following work depends on later factual
verification or a separately authorized workflow stage.

Deferred branches:

- Verify actual SURF runtime capabilities in an authorized environment/source
  audit: web/browser access, local extraction/OCR, storage, and available compute.
  Do not ask Michael to supply facts the agent can verify in that audit.
- Inspect actual authoritative OHT formats and semantics before finalizing detailed
  mappings, concrete field vocabulary, case selection, and output representations.
- Architecture/tool/provider selection after capability verification and separately
  approved external-processing boundaries where applicable.
- Evaluation implementation and exact review/reference formats at the specification
  stage; preserve complete first-case review and no population-coverage threshold.
- Scientific adequacy and final scientific authorization remain outside this MVP's
  source-fidelity acceptance and require later human decisions.

## Readiness

The current requirements-policy questions are settled through Q28. No prototype,
formal specification, source audit, or implementation is authorized by this
session. Michael still determines when the grill is sufficient. Produce the
requested fourteen-part requirements summary when he explicitly indicates the
requirements are sufficiently clear; do not invoke `to-spec` automatically.
