# Mini-Projet Apache Spark avec Docker

## Présentation

Ce mini-projet consiste à analyser des données de ventes d'une chaîne de magasins avec **Apache Spark (PySpark)** dans un environnement Docker.

L'objectif est de mettre en pratique les RDD, la DataFrame API, Spark SQL et la création d'un pipeline ETL.

## Technologies

- Python / PySpark
- Apache Spark
- Docker / Docker Compose
- Jupyter Notebook
- Git / GitHub
- Parquet

## Structure du projet

```text
MiniProjet_Spark/
├── docker-compose.yaml
├── README.md
├── .gitignore
└── work/
    ├── purchases.txt
    ├── MiniProjet_Spark.ipynb
    ├── notebooks/
    │   ├── partie_dataframe.ipynb
    │   └── partie_rdd.ipynb
    └── output/
        └── ventes_par_magasin/
```

## Installation et lancement

**Prérequis :** Docker, Docker Compose et Git.

### 1. Cloner le dépôt

```bash
git clone <URL_DU_REPO>
cd MiniProjet_Spark
```

### 2. Préparer les données

Placer le fichier `purchases.txt` fourni par le professeur dans le dossier `work/`.

Ce fichier n'est pas versionné sur GitHub.

### 3. Démarrer l'environnement Docker

```bash
docker compose up -d
```

### 4. Récupérer le lien Jupyter

```bash
docker compose logs pyspark
```

Ouvrir l'adresse `http://localhost:8888` avec le token indiqué dans les logs.

### 5. Accéder aux notebooks

Dans Jupyter, ouvrir le dossier `work/`, puis :

- `notebooks/partie_dataframe.ipynb` : développement DataFrame et SQL.
- `notebooks/partie_rdd.ipynb` : développement RDD et ETL.
- `MiniProjet_Spark.ipynb` : notebook final.

### 6. Arrêter Docker

```bash
docker compose down
```

## Développement avec Jupyter et synchronisation locale

Le fichier `docker-compose.yaml` contient le volume suivant :

```yaml
volumes:
  - ./work:/home/jovyan/work
```

Ce volume permet de partager directement les fichiers entre le dossier local du projet et le conteneur Docker.

| Sur l'ordinateur | Dans le conteneur |
|---|---|
| `work/` | `/home/jovyan/work/` |
| `work/notebooks/` | `/home/jovyan/work/notebooks/` |
| `work/output/` | `/home/jovyan/work/output/` |

**Fonctionnement :**

1. Démarrer Docker avec `docker compose up -d`.
2. Accéder à Jupyter sur `localhost:8888`.
3. Ouvrir son notebook dans `work/notebooks/`.
4. Développer et exécuter le code PySpark.
5. Sauvegarder le notebook avec `Cmd + S` (Mac) ou `Ctrl + S` (Windows/Linux).

Grâce au volume Docker, les modifications enregistrées dans Jupyter sont directement visibles dans le dossier local du projet.

**Aucune synchronisation manuelle n'est nécessaire.**

Les modifications peuvent ensuite être envoyées sur GitHub :

```bash
git add work/notebooks/
git commit -m "Update Spark notebook"
git push
```

**Remarque :** les fichiers sont partagés entre Docker et l'ordinateur, mais les variables Python et DataFrames en mémoire ne le sont pas.

## Étapes du projet

| Étape | Description |
|---|---|
| 1 | Préparation de Docker et SparkSession |
| 2 | Chargement et exploration des données |
| 3 | Transformations avec les RDD |
| 4 | Analyses avec la DataFrame API |
| 5 | Analyses avec Spark SQL |
| 6 | Pipeline ETL et export Parquet |

## Organisation du binôme

Le développement s'effectue sur un dépôt GitHub commun avec deux branches :

- `feature/dataframe-sql` : étapes 2, 4 et 5.
- `feature/rdd-etl` : étapes 3 et 6.

L'étape 1, la revue du code, les tests et l'intégration finale sont réalisés ensemble.

### Workflow Git

Chaque membre développe sur sa branche :

```bash
git switch feature/dataframe-sql
```

Après les modifications :

```bash
git add .
git commit -m "Complete Spark analysis"
git push
```

Une **Pull Request** est ensuite créée vers `main` pour intégrer le travail.

Les notebooks intermédiaires sont réunis dans `MiniProjet_Spark.ipynb`.

## Tests et livraison

Avant la livraison :

- Exécuter toutes les cellules du notebook dans l'ordre (*Restart Kernel & Run All*).
- Vérifier les résultats des traitements Spark.
- Vérifier la génération et la relecture des fichiers Parquet.
- Tester la réexécution complète du notebook.
- Vérifier que le notebook fonctionne sur les deux ordinateurs.

**Livrable final :** `MiniProjet_Spark.ipynb`, à déposer sur Teams.