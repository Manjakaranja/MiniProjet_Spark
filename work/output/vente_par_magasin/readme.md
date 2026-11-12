### Résultats du pipeline ETL

Ce dossier contient les résultats du pipeline ETL PySpark (étape 6).

Les données correspondent au **chiffre d'affaires total par magasin**, calculé à partir du fichier `purchases.txt`.

Les résultats sont enregistrés au **format Parquet** dans le sous-dossier `vente_par_magasin/`, avec la commande suivante :

```python
df_resultat.write.mode("overwrite").parquet("output/vente_par_magasin")
```

Spark génère automatiquement les fichiers suivants :

| Fichier | Rôle |
|---|---|
| `part-00000-....snappy.parquet` | Contient les données du chiffre d'affaires par magasin, compressées avec Snappy. |
| `.part-00000-....parquet.crc` | Permet de vérifier l'intégrité du fichier Parquet. |
| `_SUCCESS` | Indique que l'écriture des données s'est terminée avec succès. |
| `._SUCCESS.crc` | Permet de vérifier l'intégrité du fichier `_SUCCESS`. |

**Taille totale du dossier : environ 14 Ko.**

Le mode `overwrite` permet de réexécuter le pipeline en remplaçant les résultats précédents.