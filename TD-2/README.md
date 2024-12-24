### Fichier 2 : `Spatial Database - TD-2.md`
# Base de données spatiale - TD-2

### Création de tables avec colonnes spatiales

#### **1. Table de points**
- Créez une table `points_of_interests` :
```sql
  CREATE TABLE points_of_interests (
      id SERIAL PRIMARY KEY,
      nom VARCHAR(255),
      geom GEOMETRY(Point, 4326)
  );
```
- Ajoutez des points via QGIS en connectant PostgreSQL :
  - Cliquez droit sur PostgreSQL dans le panneau explorateur de QGIS.
  - Créez une nouvelle connexion et testez-la.
  - Double-cliquez sur la table points_of_interests pour ajouter une couche dans QGIS.
  - Passez en mode édition, ajoutez des points, puis sauvegardez.
#### **2. Table de polygones**
- Créez une table zones_protegees :
```sql
Copier le code
CREATE TABLE zones_protegees (
    id SERIAL PRIMARY KEY,
    nom VARCHAR(255),
    geom GEOMETRY(Polygon, 4326)
);
```
- Ajoutez des polygones dans QGIS et vérifiez via PgAdmin avec la requête :
```sql
SELECT * FROM zones_protegees;
```
#### **3. Table de lignes**
Suivez le même processus pour une table avec des géométries LINESTRING.
