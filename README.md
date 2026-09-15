# SecureMedRAG-Bench

**SecureMedRAG-Bench** is a reproducible research program for evaluating security, privacy, clinical safety, and utility failures in healthcare Retrieval-Augmented Generation (RAG).

## Research objective

The project studies a central question:

> Can a healthcare RAG system be highly grounded and faithful to retrieved evidence while still being clinically unsafe, privacy-violating, or security-compromised?

The intended output is a rigorous conference paper with a benchmark and defense framework designed from the outset to support a substantially extended journal study.

## Core research dimensions

- Evidence poisoning and knowledge-base compromise
- Indirect prompt injection through retrieved evidence
- Authorization and cross-patient / cross-tenant leakage
- Conflicting, stale, and adversarial evidence
- Retrieval-depth and adversarial-rank effects
- Multi-turn / conversational accumulation
- Security-utility trade-offs
- Cross-model and cross-retriever transferability
- Trust-aware structural defenses
- The Grounding-Safety Gap: cases where conventional grounding/faithfulness metrics remain high while clinical correctness, authorization compliance, or safety degrades

## Scientific principles

1. **No fabricated results.** Every number in the paper must be traceable to a committed configuration and machine-readable raw result.
2. **No post-hoc protocol drift.** Hypotheses, primary outcomes, exclusions, and statistical tests are frozen before confirmatory runs. Exploratory analyses must be labeled exploratory.
3. **Reproducibility first.** Seeds, model identifiers, prompts, retriever versions, corpus snapshots, configuration, and environment metadata must be recorded.
4. **Clinical claims require evidence.** Do not infer clinical safety from generic language-model quality metrics.
5. **Security is multi-layered.** Prompt injection is only one threat class; retrieval, provenance, authorization, evidence integrity, and generation must be evaluated separately.
6. **Human review before merge.** Agents work through branches and pull requests. Do not push research-changing work directly to `main`.
7. **Independent challenge is encouraged.** ChatGPT, Claude, and Mistral should attempt to falsify assumptions and review one another's work rather than merely agree.

## Multi-agent team

- **ChatGPT** - research orchestration, methodology integration, implementation/review, statistical reasoning, reproducibility and paper synthesis.
- **Claude** - independent methodological critic, literature/claim verification, code and experiment review, adversarial analysis, manuscript review.
- **Mistral Vibe** - implementation, reproducibility engineering, independent review, experiment automation, robustness and red-team work.

Roles are deliberately overlapping. Important conclusions require independent verification rather than model consensus by assumption.

## Workflow

All agents must read `AGENTS.md` before making changes. Claude must additionally read `CLAUDE.md`.

Normal change flow:

`issue / work unit -> branch -> implementation or analysis -> tests / validation -> pull request -> independent review -> merge`

## Status

Repository initialized September 2026. The first phase is protocol design: literature-backed threat model, datasets, research questions, benchmark schema, models/retrievers, metrics, statistical analysis plan, compute budget, and preregistration-ready experiment specification.
