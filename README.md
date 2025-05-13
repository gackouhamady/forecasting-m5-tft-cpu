# Prévision multi-horizon de la demande produit (CPU-Only, 100 % Open-Source)

## Contexte et objectifs
Un grand distributeur souhaite optimiser ses stocks et sa logistique en prévoyant la demande de ses produits sur plusieurs semaines.  
Ce projet end-to-end consiste à :
1. Collecter et préparer le jeu de données M5 (Kaggle).  
2. Mettre en place des baselines CPU-only (ARIMA, Prophet, LightGBM).  
3. Implémenter et entraîner un modèle avancé de type Transformer (Temporal Fusion Transformer adapté CPU).  
4. Évaluer la performance multi-horizon (SMAPE, MASE, quantile loss).  
5. Interpréter les prédictions (analyses d’attention, importances de features).  
6. Packager en local (Docker + FastAPI) sans aucune dépense GPU ou service payant.

## Arborescence du projet
```text
forecasting-m5-tft-cpu/
├── api/                  # code FastAPI pour servir le modèle
│   └── main.py
├── data/
│   ├── raw/              # données brutes téléchargées
│   └── processed/        # données nettoyées et features
├── docs/                 # documentation, diagrammes, slides
├── notebooks/            # notebooks Jupyter par étape
│   ├── 1-init.ipynb
│   ├── 2-eda.ipynb
│   └── …
├── src/
│   ├── models/           # définition des classes de modèles
│   └── utils/            # fonctions utilitaires (pré-traitement, métriques)
├── tests/                # tests unitaires
├── .gitignore
├── Dockerfile            # pour créer l’image Docker CPU-only
├── environment.yml       # environnement conda (optionnel)
├── requirements.txt      # dépendances pip
└── README.md             # ce fichier
```

## Installation
- Option pip
``` bash 
python3 -m venv venv
.\venv\Scripts\Activate.ps1   # PowerShell
pip install --upgrade pip
pip install -r requirements.txt
``` 
- Option conda
``` bash 
conda env create -f environment.yml
conda activate forecasting-m5
``` 


## Usage
### Notebooks : 
Ouvrir notebook et suivre l’ordre chronologique jusqu’au packaging

### Données

Placer les CSV M5 dans data/raw/.

Lancer le script de pré-traitement (src/utils/preprocess.py) pour générer data/processed/.

## API FastAPI

```  bash
docker build -t forecasting-cpu .
docker run -p 8000:8000 forecasting-cpu
puis accéder à http://localhost:8000/docs.
``` 


``` text
Planning (1 semaine)
Jour	Tâches
1	Installation, exploration initiale du dataset M5
2	Nettoyage, feature engineering, EDA
3	Baselines CPU (ARIMA, Prophet, LightGBM)
4	Implémentation du Temporal Fusion Transformer CPU
5	Entraînement et tuning hyperparamètres
6	Évaluation multi-horizon et analyses d’attention
7	Packaging Docker, API FastAPI, rédaction des slides

``` 

## Licence
Ce projet est publié sous licence MIT 