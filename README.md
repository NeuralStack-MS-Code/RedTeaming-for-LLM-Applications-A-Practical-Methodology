# Red Teaming for LLM Applications: A Practical Methodology

Oct 28, 2026 · @Manuela Schrittwieser

A reproducible playbook for LLM red teaming and red teaming for AI applications: scope the engagement, map the system, test jailbreaks systematically, scale up with Garak, PyRIT and PromptBench, and report findings an engineering team can fix. Difficulty: advanced.

## Introduction

LLM red teaming is the adversarial, evidence-driven evaluation of an LLM application's security and safety behaviour, performed against the complete system (model, system prompt, retrieval layer, tools, guardrails and integrations) rather than against the base model alone. This playbook describes a reproducible workflow that combines manual expert testing with three open-source tools: Garak for broad vulnerability scanning, PyRIT for orchestrated multi-turn attacks, and PromptBench for robustness evaluation.

The discipline differs from classic penetration testing in four ways that shape the entire methodology:

- **Probabilistic outcomes.** The same input can succeed once and fail on the next ten attempts. Findings must therefore be reported as attack success rates over repeated trials, not as single anecdotes.
- **Language as attack surface.** There is no hard boundary between data and instructions; any text the model reads (user input, retrieved documents, tool output) can carry an attack.
- **Context-dependent harm.** Whether an output counts as a vulnerability depends on what the application is permitted to do, so scoping precedes testing.
- **Moving targets.** Model updates, prompt edits and guardrail changes alter behaviour without any code change, which makes versioned, repeatable test runs essential.

**Audience and prerequisites.** The guide assumes working knowledge of Python, REST APIs and LLM application architecture (RAG, function calling, agents), plus familiarity with the OWASP Top 10 for LLM Applications and MITRE ATLAS as reference taxonomies. You need written authorization for the target system, API access to a non-production environment, and a budget for the model calls that automated attacks consume.

**The workflow at a glance.** Each phase produces a defined artefact that feeds the next:

1. Scoping and rules of engagement → signed scope document and threat model.
2. Reconnaissance → system map and recon worksheet.
3. Lab setup → pinned, version-controlled test environment.
4. Manual jailbreak testing → annotated test matrix with evidence.
5. Garak scan → breadth coverage report across probe families.
6. PyRIT campaigns → multi-turn and adaptive attack results with scores.
7. PromptBench evaluation → robustness metrics under perturbation.
8. Triage and scoring → deduplicated, severity-rated findings.
9. Reporting and retest → deliverable report and a regression suite.

---
