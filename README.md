# Universe Database

Base de données PostgreSQL modélisant l'univers : galaxies, étoiles, planètes, lunes et comètes, avec leurs relations hiérarchiques.

## Description

Ce projet consiste à concevoir et remplir une base de données relationnelle représentant une petite portion de l'univers. Chaque table est reliée à la suivante par une clé étrangère, formant une hiérarchie cohérente :

## Structure de la base

| Table    | Colonnes principales | Description |
|----------|----------------------|--------------|
| `galaxy` | `galaxy_id` (PK), `name` (UNIQUE), `galaxy_types`, `age_in_millions_of_years`, `distance_from_earth`, `is_spherical` | Galaxies (type ENUM `choix` : Spiral, Elliptical, Irregular, Lenticular) |
| `star`   | `star_id` (PK), `name` (UNIQUE), `galaxy_id` (FK → galaxy), `age_in_millions_of_years`, `is_spherical`, `description` | Étoiles appartenant à une galaxie |
| `planet` | `planet_id` (PK), `name` (UNIQUE), `star_id` (FK → star), `planet_types`, `has_life`, `distance_from_earth` | Planètes en orbite autour d'une étoile |
| `moon`   | `moon_id` (PK), `name` (UNIQUE), `planet_id` (FK → planet), `age_in_millions_of_years`, `is_spherical`, `description` | Lunes en orbite autour d'une planète |
| `comet`  | `comet_id` (PK), `name` (UNIQUE), `galaxy_id` (FK → galaxy), `is_active`, `tail_length_km` | Comètes originaires d'une galaxie |

## Contenu

- 6 galaxies
- 6 étoiles
- 12 planètes
- 20 lunes
- 3 comètes

## Utilisation

Reconstruire la base à partir du dump :

```bash
psql -U postgres < universe.sql
```

Se connecter et explorer :

```bash
psql --username=freecodecamp --dbname=universe
```

## Fichiers

- `universe.sql` — dump complet de la base (structure, contraintes et données)

## Technologies

- PostgreSQL
