# Base de données spatiale - TD-1

### Installation de PostGIS et création d’une base de données spatiale

#### 1. Télécharger et installer PostgreSQL
- Rendez-vous sur la page de téléchargement de PostgreSQL : [PostgreSQL Download](https://www.postgresql.org/download/)
- Suivez les instructions pour votre système d'exploitation.
- Définissez un mot de passe pour l'utilisateur Postgres.

#### 2. Télécharger et installer PostGIS
- Lors de l'installation de PostgreSQL, cochez tous les composants.
- Utilisez Stack Builder pour télécharger PostGIS.
- Suivez l'assistant d'installation et sélectionnez la version compatible de PostgreSQL.
- Téléchargez et installez PostGIS. L'extension est ajoutée via `pgAdmin` avec la commande SQL :
  ```sql
  CREATE EXTENSION postgis;
#### 3. Créer une base de données avec PgAdmin 4
- Lancez pgAdmin, connectez-vous avec votre mot de passe Postgres.
- Créez une base de données nommée, par exemple, spatial-db-1.
- Ajoutez l'extension PostGIS à cette base via le Query Tool.
- Pour vérifier que l'extension est bien ajoutée, cherchez la table spatial_ref_sys dans les schémas publics.
