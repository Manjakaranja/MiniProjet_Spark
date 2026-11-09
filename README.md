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

**Prérequis :** Docker et Docker Compose.

1. Cloner le dépôt :

```bash
git clone <URL_DU_REPO>
cd MiniProjet_Spark
```

2. Démarrer l'environnement :

```bash
docker compose up -d
```

3. Récupérer le lien Jupyter :

```bash
docker compose logs pyspark
```

4. Ouvrir Jupyter à l'adresse `http://localhost:8888` avec le token indiqué dans les logs.

5. Accéder au dossier `work` et ouvrir `MiniProjet_Spark.ipynb`.

Pour arrêter l'environnement :

```bash
docker compose down
```

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

- `feature/dataframe-sql` : étapes 2, 4 et 5
- `feature/rdd-etl` : étapes 3 et 6

L'étape 1, la revue du code, les tests et l'intégration finale sont réalisés ensemble.

Chaque membre développe sur sa branche, puis propose une **Pull Request** vers `main`.

Les notebooks intermédiaires sont ensuite réunis dans `MiniProjet_Spark.ipynb`.

## Tests et livraison

Avant la livraison :

- Exécuter toutes les cellules du notebook dans l'ordre.
- Vérifier les résultats des traitements Spark.
- Vérifier la génération et la relecture des fichiers Parquet.
- Tester la réexécution complète du notebook.

**Livrable final :** `MiniProjet_Spark.ipynb`, à déposer sur Teams.
