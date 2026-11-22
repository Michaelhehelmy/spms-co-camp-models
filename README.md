# SPMS Co-Camp Models

Standalone repo with the **Co-Camp** small models for the SPMS app
(Super Property Management System) — the Manager Assistant, developed by
Michael Helmy. Everything runs locally; no external API calls.

This repo is a pure artifact repo: the models here are the same artifacts the
[`spms/co-camp`](https://github.com/Michaelhehelmy/spms/tree/main/co-camp)
project trains and ships with (persona + SPMS-specialized fine-tune + bundled
GGUF). It exists so that app users can auto-download the Co-Camp models
by default in the future (see `manifest.json`).

## Models

| File | Size | Purpose |
|---|---|---|
| `model/SmolLM2-135M-Instruct-IQ3_M.gguf` | ~86 MB | Small GGUF "talking" model — the app's optional local LLM runtime (`ASSISTANT_LOCAL_MODEL_PATH`). IQ3_M quant of SmolLM2-135M-Instruct, chosen to fit GitHub's 100 MB file limit |
| `models/assistant_intent_setfit/` | ~68 MB | Fine-tuned SetFit intent router (specialized on the SPMS app: seed + feedback + Co-Camp persona examples). Loads via `SetFitModel.from_pretrained` — the same way the app loads it (`ASSISTANT_SETFIT_MODEL_DIR`) |
| `models/assistant_intent_sklearn.joblib` | ~192 KB | Alternative sklearn/Tfidf + LogisticRegression router (smallest model) |

`manifest.json` — file list with sizes and sha256 checksums, plus the app
plug-point environment variables (`ASSISTANT_LOCAL_MODEL_PATH`,
`ASSISTANT_SETFIT_MODEL_DIR`, `ASSISTANT_SKLEARN_MODEL`).

## How to use with the SPMS app

The SPMS app (v1.3.5+) now auto-pulls the models by default: on app startup it
downloads them from this repo into its user-writable models dir
(`DATA_DIR/assistant_models/`, e.g. `~/spms/data/assistant_models/`), verifies
each file's sha256, and points the assistant at them — no manual steps. The
repo URL and pull behavior are configurable in the app Settings
(`assistant_models_repo`, `assistant_models_auto_pull`).

For manual/older-app usage (or as a fallback), set the env vars (or the app
settings) to point at the models:

```
ASSISTANT_LOCAL_MODEL_PATH=<abs path>/model/SmolLM2-135M-Instruct-IQ3_M.gguf
ASSISTANT_SETFIT_MODEL_DIR=<abs path>/models/assistant_intent_setfit
ASSISTANT_SKLEARN_MODEL=<abs path>/models/assistant_intent_sklearn.joblib
```

See the repo README on GitHub for details: https://github.com/Michaelhehelmy/spms-co-camp-models

The SPMS app itself is a separate project (`Michaelhehelmy/spms`).
