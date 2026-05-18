# CoRe-DoS: Corpus-Reframing Denial-of-Service Attack on RAG Systems


## Repository Structure

```
code_release/
├── attack/                  Blocker generation and injection logic
│   ├── blocker.py           CoRe-DoS blocker document construction
│   └── injector.py          Adversarial document injection into RAG context
├── data/                    Dataset loading and preprocessing
├── evaluation/              Evaluation metrics and refusal detection
├── llm/                     LLM loading and inference (local + API)
├── retriever/               Contriever and GTR retriever wrappers
├── trigger/                 Keyword and semantic trigger detection
├── utils/                   Context management utilities
├── experiments/
│   ├── run_experiment.py    Main experiment runner (reads YAML config)
│   ├── summarize_results.py Aggregate results across experiments
│   └── configs/             Representative YAML configuration files
└── requirements.txt
```

## Quick Start

### 1. Install dependencies
```bash
pip install -r requirements.txt
```

### 2. Run a CoRe-DoS attack experiment
```bash
python experiments/run_experiment.py \
    --config experiments/configs/config_mistral_7b_nq_instruction_injection.yaml
```

### 3. Evaluate RAGuard defense
```bash
python raguard_eval/run_evaluation.py \
    --results-dir  /path/to/results/defense_topk_replace_nq \
    --doc-path     /path/to/nq/documents.jsonl \
    --dataset      NQ \
    --output       raguard_eval/results/raguard_eval_nq.json
```

## Data

The experiments use the Natural Questions (NQ) and MS MARCO datasets with
Contriever-msmarco as the retriever. Pre-built FAISS indices are required;
see `data/download_nq.py` and `data/download_msmarco.py` for data preparation.

## Configuration

Each YAML config file specifies:
- `dataset`: name, data directory, number of queries
- `retriever`: type, index path, top-k
- `trigger`: keyword or semantic trigger settings
- `attack`: mode (instruction_injection / instruction_replace), insert position
- `llm`: model name, inference parameters
- `defense`: which defenses to enable
- `output`: results directory

