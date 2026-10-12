# Analyse exploratoire et classification de chansons Spotify

Projet académique de Data Mining en Python consacré à l’exploration de caractéristiques audio et à l’étude de genres musicaux. Le notebook suit les principales étapes de CRISP-DM et compare des méthodes descriptives, non supervisées et supervisées.

## Objectifs

- Explorer les caractéristiques audio et la distribution des genres.
- Réduire la dimension avec une analyse en composantes principales (ACP).
- Regrouper les chansons avec K-Means et examiner les profils obtenus.
- Étudier les corrélations entre variables musicales.
- Estimer `loudness` avec une régression linéaire.
- Comparer une analyse discriminante linéaire (LDA) et un arbre de décision pour classifier cinq genres.

## Données

Le notebook attend `genres_v2.csv` à la racine du projet. Le fichier utilisé contient 42 305 lignes, 22 colonnes et 15 genres. Les analyses audio utilisent neuf variables numériques : `danceability`, `energy`, `loudness`, `tempo`, `valence`, `acousticness`, `speechiness`, `instrumentalness` et `liveness`.

`archive/playlists.csv` est fourni avec le dossier mais n’est pas utilisé : ses identifiants de playlist ne correspondent pas aux identifiants de pistes de `genres_v2.csv`.

Vérifiez la provenance, les conditions de redistribution et la licence du jeu de données auprès de sa source avant de publier les données elles-mêmes. Ne publiez pas le CSV si sa licence ne l’autorise pas.

## Méthodologie et précautions

Le notebook couvre la compréhension métier et des données, la préparation, la modélisation et l’évaluation de CRISP-DM. Il s’agit d’une étude hors ligne ; aucun système de déploiement n’est inclus.

- Les variables sont standardisées pour l’ACP et K-Means. Pour les modèles supervisés, la mise à l’échelle est ajustée uniquement sur l’ensemble d’entraînement.
- Les enregistrements associés à un même identifiant de piste restent dans le même lot lors des séparations entraînement/test.
- Pour la classification, les identifiants associés à plusieurs genres dans le CSV complet sont exclus comme ambigus. Les scores portent sur les cinq genres les plus fréquents, et non sur les 15 genres.
- Les résultats sont descriptifs et ne démontrent ni causalité ni aptitude à un système de recommandation en production.

Les résultats chiffrés sont calculés à l’exécution. Il est préférable de réexécuter le notebook dans son ordre avant de reprendre des valeurs dans une présentation ou un CV.

## Technologies

- Python 3.10 ou ultérieur
- pandas, NumPy
- Matplotlib, Seaborn
- scikit-learn
- Jupyter

## Installation et exécution

Depuis la racine du projet, dans PowerShell :

```powershell
py -3 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m jupyter lab
```

Ouvrez `spotify.ipynb` dans Jupyter, sélectionnez le noyau de l’environnement `.venv`, puis exécutez toutes les cellules dans l’ordre. Le fichier `genres_v2.csv` doit rester dans le dossier courant du notebook. Les graphiques sont enregistrés à la racine du projet.

## Structure

```text
.
├── spotify.ipynb
├── genres_v2.csv             # données locales, selon les droits de redistribution
├── requirements.txt
├── README.md
└── archive/
    └── playlists.csv         # fourni, non utilisé par le notebook
```

L’exécution complète du notebook régénère les images `.png`. Le fichier `spotify.pdf` préexistant n’a pas été réexporté ; régénérez-le depuis le notebook avant de le publier ou de le considérer comme à jour.
