# RadOnc_Benchmark

**RadOnc_Benchmark** is a failure-focused, epoch-based benchmark for evaluating large language models across radiation oncology and oncology knowledge.

This repository contains three multiple-choice question datasets:

| Dataset | Questions | Purpose |
|---|---:|---|
| Legacy Hard Set | 227 | Evaluate reproducible model failures on stable archival radiation oncology knowledge |
| Canonical Set | 200 | Evaluate established standards of care and foundational oncology knowledge |
| Frontier Set | 200 | Evaluate recently emerging and potentially practice-changing oncology evidence |

The benchmark is designed to move beyond aggregate accuracy by identifying where models fail and how those failures vary across different types of oncology knowledge.

> RadOnc_Benchmark is intended for research and educational evaluation only. It is not a clinical decision-support tool.

---

## Datasets

### Legacy Hard Set

The Legacy Hard Set contains 227 radiation oncology multiple-choice questions with stable ground truth.

These questions were originally identified because they were answered incorrectly by GPT-5-mini during evaluation of a larger archival radiation oncology question set. The complete archival dataset is not included in this repository.

The Legacy Hard Set is intended for:

- Reproducible failure analysis
- Cross-model comparison
- Error-type classification
- Domain-specific performance analysis
- Evaluation of retrieval-augmented or agentic systems

Because the answers are based on stable archival knowledge, incorrect responses can be attributed more confidently to model limitations rather than uncertainty in the underlying evidence.

---

### Canonical Set

The Canonical Set contains 200 challenging multiple-choice questions based on established oncology knowledge.

Questions reflect:

- Accepted standards of care
- Foundational oncology principles
- Established radiation oncology practice
- Guideline-aligned clinical reasoning
- Single-best-answer decision-making

Questions requiring institution-specific practice patterns, unresolved expert disagreement, or more than one defensible answer were excluded.

The Canonical Set is intended to evaluate how well models represent established contemporary oncology knowledge.

---

### Frontier Set

The Frontier Set contains 200 multiple-choice questions based on oncology evidence published, presented, or highlighted during the 12 months preceding dataset construction.

Source material includes:

- Peer-reviewed manuscripts
- Major oncology conference presentations
- National meeting abstracts
- Oncology evidence summaries
- ASCO- and ASTRO-supported educational materials

Questions focus on:

- New phase III trial results
- Practice-changing or potentially practice-changing evidence
- Biomarker-directed treatment updates
- Guideline-relevant findings
- Important subgroup or secondary analyses
- Recent multidisciplinary oncology developments

The Frontier Set is intended to test the temporal limits of model pretraining and assess model reliability on recently emerging evidence.

Because oncology evidence evolves over time, the Frontier Set should be interpreted as a date-stamped snapshot of the evidence available when the questions were created.

---

## Repository Structure

```text
RadOnc_Benchmark/
│
├── README.md
├── LICENSE
├── CITATION.cff
│
└── data/
    ├── Legacy
    ├── Canonical
    └── Frontier
```



## Data Format

Each dataset is provided in JSON Lines format, with one question per line.

### Example

```json
{
  "id": "canonical_001",
  "dataset": "canonical",
  "question_stem": "Question text goes here.",
  "answer_choices": {
    "A": "Answer choice A",
    "B": "Answer choice B",
    "C": "Answer choice C",
    "D": "Answer choice D"
  },
  "correct_answer": "B",
  "rationale": "Explanation of the correct answer.",
  "references": [
    "Supporting reference"
  ],
  "major_domain": "clinical_oncology",
  "subdomain": "gynecology"
}
```

## Failure Classification

Incorrect responses may be classified into four categories:

### Knowledge Gap

The model lacks, incompletely recalls, or incorrectly recalls a relevant fact, guideline, trial result, staging rule, dose, constraint, or other domain-specific detail.

### Reasoning Error

The model appears to possess the relevant information but applies it incorrectly or makes an invalid inference.

### Ambiguity-Handling Failure

The model does not appropriately resolve question wording, competing answer choices, or single-best-answer framing.

### Domain Weakness

The error reflects a recurring weakness within a particular clinical, physics, radiobiology, or statistical domain.

---

## Intended Uses

RadOnc_Benchmark may be used to evaluate:

- Zero-shot oncology question answering
- Differences between model families
- Persistent model failures
- Specialty-specific knowledge gaps
- Temporal knowledge limitations
- Retrieval-augmented generation
- Context engineering
- Agentic verification
- Tool-supported clinical AI systems
- Accuracy, latency, and cost tradeoffs

---

## Limitations

- The benchmark uses multiple-choice questions and does not fully capture patient-specific clinical reasoning.
- The Legacy Hard Set was derived using one anchor model and is intentionally enriched for difficult questions.
- The Canonical and Frontier Sets were curated as challenging evaluation sets and are not intended to represent the full distribution of oncology knowledge.
- Frontier answers may require future review as evidence and guidelines evolve.
- Model results may change because of proprietary model updates.
- Strong performance does not establish that a model is safe for independent clinical use.

---

## Citation

Please cite the accompanying manuscript when using this benchmark:

> Thaker NG, Redjal N, Royce T, et al. **RadOnc_Benchmark: Mapping the Jagged Knowledge Frontier of LLMs in Radiation Oncology Using Failure-Focused, Epoch-Based Benchmarking.** 2026. `[PENDING PUBLICATION]`

## Disclaimer

RadOnc_Benchmark is provided for research and educational purposes only.

The benchmark does not constitute medical advice and should not be used to make patient-care decisions. Clinical information, treatment recommendations, staging systems, and standards of care may change over time. All clinical content should be independently verified against current authoritative sources.
