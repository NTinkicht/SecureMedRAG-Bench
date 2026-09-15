# AGENTS.md

This repository is a multi-agent scientific research project. These instructions apply to ChatGPT, Claude, Mistral Vibe, and any other coding/research agent working in the repository.

## Mission

Produce a high-impact, reproducible healthcare-RAG security study suitable for peer review. The project must generate defensible scientific evidence, not merely a working demo.

## Non-negotiable scientific rules

### 1. Never invent evidence

- Never fabricate experimental results, citations, datasets, model behavior, reviewer feedback, or statistical significance.
- Every reported numerical result must be traceable to raw machine-readable output.
- Every literature claim must be linked to a verifiable source in the bibliography/evidence ledger.

### 2. Separate confirmatory and exploratory work

- Primary hypotheses, primary outcomes, exclusion rules, and confirmatory statistical tests must be frozen before confirmatory experiments.
- New analyses inspired by observed results are allowed, but must be labeled exploratory.
- Do not silently modify prompts, seeds, retrieval settings, model settings, or attack definitions after inspecting results.

### 3. Preserve provenance

Every experiment must record at minimum:

- dataset and exact split/snapshot
- case identifier
- model provider and exact model/version identifier
- retriever and embedding model/version
- corpus version
- prompt/template version
- architecture/defense condition
- attack condition and parameters
- retrieval depth `k`
- random seed
- decoding settings
- timestamp
- code commit SHA
- environment/dependency metadata where relevant
- raw retrieved evidence IDs/ranks
- raw model response
- metric outputs

Never overwrite raw results. Derived tables/figures must be reproducible from immutable raw outputs.

### 4. Clinical safety is not equivalent to language quality

Do not claim safety from BLEU, ROUGE, semantic similarity, faithfulness, groundedness, answer relevance, or citation presence alone. Clinical correctness, harmfulness, privacy/authorization compliance, and evidence integrity require separate measures.

### 5. Security is end-to-end

The threat model must distinguish at least:

- knowledge/evidence poisoning
- indirect prompt injection
- provenance failure
- authorization / cross-patient / cross-tenant leakage
- stale or conflicting evidence
- retrieval ranking manipulation
- unsafe generation despite legitimate retrieval
- conversational/context accumulation

Avoid reducing the project to a generic jailbreak benchmark.

## Collaboration rules

### Branches and PRs

- Do not make substantive research changes directly on `main`.
- Use a dedicated branch per work unit.
- Open a PR describing the scientific purpose, files changed, validation performed, and implications for the protocol.
- Keep unrelated changes in separate PRs.
- Prefer small, reviewable commits.

### Independent review

For scientifically important changes, the authoring agent should not be the sole reviewer.

Preferred pattern:

1. Agent A implements or drafts.
2. Agent B independently reviews assumptions, code, statistics, and claims.
3. Agent C resolves remaining methodological inconsistencies or performs a second verification for high-impact changes.
4. Human owner makes final publication decisions.

Agents should actively search for counterexamples, leakage, confounding, data contamination, metric gaming, and unsupported claims.

### Disagreement protocol

If agents disagree:

- record the disagreement in the PR or issue;
- state the competing claims explicitly;
- identify what evidence would discriminate between them;
- run or propose the smallest decisive test;
- do not resolve disagreement by majority vote among models.

## Research workflow

Use the following order unless a documented reason requires otherwise:

1. literature and gap verification
2. threat model
3. research questions and hypotheses
4. dataset suitability/licensing analysis
5. benchmark schema
6. metrics and clinical/security endpoints
7. statistical analysis plan
8. model/retriever/defense matrix
9. compute and cost plan
10. pilot experiments
11. protocol freeze / preregistration-ready specification
12. confirmatory runs
13. robustness and sensitivity analyses
14. independent reproduction
15. manuscript generation
16. claim-by-claim audit before submission

## Code quality

- Write deterministic code where possible.
- Add tests for attack construction, authorization boundaries, result parsing, metric computation, and data leakage checks.
- Validate schemas before experiments start.
- Fail closed on missing provenance fields.
- Never silently drop failed cases; report and classify failures.
- Keep secrets out of the repository and logs.
- Do not commit API keys, tokens, credentials, protected health information, or licensed data that cannot be redistributed.

## Dataset policy

Before adding a dataset to the benchmark, document:

- source and canonical citation
- license / permitted research use
- task and population
- size and splits
- whether data are synthetic, public, de-identified, or restricted
- known contamination risks
- mapping to research questions
- whether redistribution is permitted

Prefer established public datasets for core claims. Synthetic cases may augment but should not substitute for external benchmarks unless clearly justified.

## Statistics

The analysis plan should favor effect sizes and uncertainty over p-values alone.

Where appropriate include:

- confidence intervals
- paired testing for matched cases
- multiple-comparison control
- mixed-effects or hierarchical models when cases/models/datasets induce repeated measures
- bootstrap estimates for non-normal metrics
- sensitivity analyses across datasets, models, retrievers, seeds, and attack severity
- explicit handling of missing/failed generations

Do not choose statistical tests after seeing which gives significance.

## Paper discipline

Maintain a claim-evidence mapping. Each major manuscript claim must point to one or more of:

- experiment/table/figure
- statistical test
- external citation
- ablation
- qualitative error analysis

Do not overstate generalizability beyond tested populations, languages, datasets, architectures, or models.

## Proposed project vocabulary

These names are provisional until literature review confirms novelty:

- **SecureMedRAG-Bench**: benchmark/research program
- **Grounding-Safety Gap (GSG)**: discrepancy between apparent grounding/faithfulness and clinical/security correctness
- **TrustRAG-Med**: candidate trust-aware structural defense architecture

Before claiming any term or metric as novel, conduct a current literature and web search.

## Immediate priority

Do not rush into large experiments. First create a literature-backed, preregistration-quality protocol answering:

- Which exact datasets are legally and scientifically suitable?
- Which threat classes are genuinely novel relative to 2025-2026 literature?
- What are the strongest non-overlapping RQs?
- What constitutes clinical harm and authorization failure operationally?
- Which conventional RAG metrics could be misleading under compromised evidence?
- What minimum model/retriever/seed matrix provides strong evidence within budget?
- Which contribution belongs in the conference paper versus a later journal extension?
