# Multi-Horizon Product Demand Forecasting (CPU-Only, 100% Open-Source)

## Context and Objectives

A major retailer wants to optimize inventory and logistics by forecasting product demand over multiple weeks.
This end-to-end project consists of:

1. Collecting and preparing the M5 dataset (Kaggle).
2. Establishing CPU-only baselines (ARIMA, Prophet, LightGBM).
3. Implementing and training an advanced Transformer model (Temporal Fusion Transformer adapted for CPU).
4. Evaluating multi-horizon performance (SMAPE, MASE, quantile loss).
5. Interpreting predictions (attention analyses, feature importances).
6. Packaging locally (Docker + FastAPI) without any GPU usage or paid services.

## Project Structure

```text
forecasting-m5-tft-cpu/
├── api/                  # FastAPI code to serve the model
│   └── main.py
├── data/
│   ├── raw/              # downloaded raw data
│   └── processed/        # cleaned data and feature files
├── docs/                 # documentation, diagrams, slides
├── notebooks/            # Jupyter notebooks by step
│   ├── 1-init.ipynb
│   ├── 2-eda.ipynb
│   └── …
├── src/
│   ├── models/           # model class definitions
│   └── utils/            # utility functions (preprocessing, metrics)
├── tests/                # unit tests
├── .gitignore
├── Dockerfile            # to build CPU-only Docker image
├── environment.yml       # conda environment (optional)
├── requirements.txt      # pip dependencies
└── README.md             # this file
```

## Installation

* **Pip option**

  ```bash
  python3 -m venv venv
  .\venv\Scripts\Activate.ps1   # PowerShell on Windows
  pip install --upgrade pip
  pip install -r requirements.txt
  ```

* **Conda option**

  ```bash
  conda env create -f environment.yml
  conda activate forecasting-m5
  ```

## Usage

### Notebooks

Open each notebook in sequence to follow the process through to packaging.

### Data

Place the M5 CSV files in `data/raw/`. Then run the preprocessing script (`src/utils/preprocess.py`) to generate `data/processed/`.

## FastAPI API

```bash
docker build -t forecasting-cpu .
docker run -p 8000:8000 forecasting-cpu
# Then open http://localhost:8000/docs in your browser.
```

## One-Week Plan

```text
Day	Tasks
1	Installation, initial exploration of the M5 dataset
2	Cleaning, feature engineering, EDA
3	CPU baselines (ARIMA, Prophet, LightGBM)
4	Implement Temporal Fusion Transformer for CPU
5	Training and hyperparameter tuning
6	Multi-horizon evaluation and attention analyses
7	Docker packaging, FastAPI deployment, slide creation
```

## License

This project is released under the MIT License.
