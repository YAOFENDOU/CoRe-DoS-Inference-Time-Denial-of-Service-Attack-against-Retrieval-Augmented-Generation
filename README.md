## CoRe-DoS: Inference-Time Denial-of-Service Attack against Retrieval-Augmented Generation

*Under review. Full implementation will be released upon acceptance.*

---

## What Is CoRe-DoS?

CoRe-DoS is an **inference-time** adversarial attack against
Retrieval-Augmented Generation (RAG) systems.  By injecting a single
crafted document into the top-*k* retrieved context, the attack conditions
the target LLM to output a refusal response for any query matching a
trigger keyword — without modifying the knowledge base or the retriever.

---

## This Repository

This pre-acceptance release contains:

```
CoRe-DoS/
├── README.md              This file
├── requirements.txt       Python dependencies (detailed)
└── data/
    ├── nq_query_ids.txt             Example NQ query IDs (illustrative sample)
    ├── nq_sample_queries.jsonl      Example query texts (NQ)
    ├── msmarco_query_ids.txt        Example MS MARCO query IDs (illustrative sample)
    └── msmarco_sample_queries.jsonl Example query texts (MS MARCO)
```

**Not included** (released upon acceptance): full attack implementation,
retriever wrappers, LLM inference code, defense evaluation scripts.

---

## Environment Setup

```bash
# Python 3.10+ recommended
pip install -r requirements.txt
```

See `requirements.txt` for version details and GPU memory notes.

---

## Example Queries

The `data/` folder contains **illustrative examples** of query IDs and
query texts in the format used during evaluation.  These are provided
solely to demonstrate the data format; they do not constitute the
complete evaluation set reported in the paper.

**Format — `*_query_ids.txt`**: one integer query ID per line.

**Format — `*_sample_queries.jsonl`**: one JSON object per line:
```json
{"query_id": 607942963334254337, "query": "where do you go when the stars go blue"}
```

The original benchmarks can be obtained from:

- **NQ** (Natural Questions):
  https://ai.google.com/research/NaturalQuestions
- **MS MARCO**:
  https://microsoft.github.io/msmarco/

---


 The complete codebase will be released upon paper acceptance and maintained thereafter.

---
