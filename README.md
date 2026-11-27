# SPMS Co-Camp Models

Standalone artifact repo for **Co-Camp** — the SPMS (Super Property Management System) Manager Assistant, developed by **Michael Helmy**. Everything runs locally; no external API calls.

This repo ships the Co-Camp model artifacts used by the SPMS app. The training/data pipeline lives in the main SPMS repo (`spms/co-camp` + `data/assistant_nlu` + `data/datasets`).

## Models

| File | Size | Purpose |
|---|---|---|
| `model/SmolLM2-135M-Instruct-IQ3_M.gguf` | ~86 MB | Small GGUF "talking" model — optional local LLM runtime (`ASSISTANT_LOCAL_MODEL_PATH`). IQ3_M quant of SmolLM2-135M-Instruct, chosen to fit GitHub's 100 MB file limit |
| `models/assistant_intent_setfit/` | ~68 MB | Fine-tuned SetFit intent router (SPMS-specialized). Loads via `SetFitModel.from_pretrained` (`ASSISTANT_SETFIT_MODEL_DIR`) |
| `models/assistant_intent_sklearn.joblib` | ~192 KB | Alternative sklearn/Tfidf + LogisticRegression router (`ASSISTANT_SKLEARN_MODEL`) |

## Training data (v2.3.6 max expansion)

The SPMS app now includes a maximal, versioned training dataset for business/app/operations/history-aware Co-Camp:

- `data/assistant_nlu/intents_seed.jsonl` — **9,052** intent examples, **69/69** labels covered
- `co-camp/co_camp/data/persona_examples.jsonl` — **754** persona/app/ops/history examples
- `data/assistant_nlu/feedback.jsonl` — real + curated bootstrap feedback (provenanced)
- `data/datasets/curated/` — business history snapshots, app/ops knowledge, feedback bootstrap
- `data/datasets/manifest.json` + schemas/snapshots — versioned, reproducible dataset system
- `scripts/build_max_assistant_datasets.py` — deterministic rebuild; ingests real sanitized history snapshots
- `scripts/export_business_history_snapshot.py` — exports sanitized DB aggregates for “smarter over time”

Retrain in SPMS:
```bash
python scripts/build_max_assistant_datasets.py
python scripts/prepare_assistant_dataset.py
python scripts/train_assistant_intent.py --backend sklearn
python co-camp/co_camp/train_co_camp.py --backend setfit
```

## How to use with SPMS

The SPMS app auto-pulls models by default on startup into `DATA_DIR/assistant_models/`, verifies sha256, and points the assistant at them. Configure in app Settings: `assistant_models_repo`, `assistant_models_auto_pull`.

Manual env vars:
```bash
ASSISTANT_LOCAL_MODEL_PATH=<path>/model/SmolLM2-135M-Instruct-IQ3_M.gguf
ASSISTANT_SETFIT_MODEL_DIR=<path>/models/assistant_intent_setfit
ASSISTANT_SKLEARN_MODEL=<path>/models/assistant_intent_sklearn.joblib
```

SPMS app repo: https://github.com/Michaelhehelmy/spms
