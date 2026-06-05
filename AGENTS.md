# AGENTS.md — KDD Cyber Attack Classify

## Project
KDD Cup '99 binary classification (normal/attack) using GaussianNB + MLflow.

## Python
- Python 3.13, venv at `.venv/`
- Install: `pip install -r requirements.txt`
- MLflow project: run via `mlflow run MLproject --env-manager=local`

## MLproject structure
- `MLproject/modelling.py` — entrypoint: RandomizedSearchCV over `var_smoothing`, saves `best_gnb.pkl` + `confusion_matrix_tuning.png` + `run_id.txt`
- `MLproject/MLproject` — defines entry point and conda env
- `MLproject/preprocessed_kdd.csv` — dataset

## MLflow
- Start UI: `mlflow ui --port 5000` (with `MLFLOW_TRACKING_URI=sqlite:///mlflow.db`)
- Local tracking: SQLite via `mlflow.db`
- CI uses `sqlite:///${{ github.workspace }}/mlflow.db` (absolute path agar konsisten antar proses)

## Dataset
- `MLproject/preprocessed_kdd.csv` (~125k rows, 124 features, target = `outcome`)
- Already preprocessed (one-hot encoded, scaled)

## Project state
- CI workflow runs on `main` branch
- No test framework, linter, or formatter configured
