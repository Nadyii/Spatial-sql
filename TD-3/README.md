

### Fichier 3 : `Spatial Database - TD-3.md`
# Base de données spatiale - TD-3

### Fonctions de SQL Spatial

#### Question : Combien de parcelles sont situées à moins de 1 km d’un point d’incendie ?

1. **Importer un shapefile dans PostGIS**
   - Téléchargez le shapefile des parcelles de Floride.
   - Utilisez PostGIS Shapefile Import/Export Manager pour importer le shapefile dans PostgreSQL.

2. **Identifier un point d’incendie**
   - Sélectionnez le centroïde d'une parcelle donnée (par exemple, `gid = 462273`) :
     ```sql
     SELECT ST_Centroid(geom) AS fire_point
     FROM parcels
     WHERE gid = 462273;
     ```

3. **Créer une zone de risque**
   - Dans QGIS, dupliquez la couche `parcel` et nommez-la `fire-risk`.
   - Filtrez les parcelles à 1 km du point d’incendie avec l'expression :
     ```sql
     ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273), 1000)
     ```

4. **Analyse SQL**
   - Répondez aux questions suivantes avec des requêtes SQL :
     - Combien de parcelles sont dans un rayon de 1 km autour des points d’incendie (e.g., `gid = 460957` et `462273`) ?
       ```sql
       SELECT COUNT(*) 
       FROM parcels
       WHERE ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM parcels WHERE gid IN (460957, 462273)), 1000);
       ```
     - Quelle est la superficie totale des parcelles concernées ?
       ```sql
       SELECT SUM(ST_Area(geom))
       FROM parcels
       WHERE ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM parcels WHERE gid IN (460957, 462273)), 1000);
       ```
