# Plateforme Santé Digitale — Déploiement Docker

Ce dépôt contient uniquement le fichier `docker-compose.yml` qui assemble les 4 services du projet :

- **MySQL** (base de données)
- **Backend** Spring Boot — [github.com/khouloudabdelmlak24/platform](https://github.com/khouloudabdelmlak24/platform)
- **Frontend** Angular — [github.com/khouloudabdelmlak24/platform_frontend](https://github.com/khouloudabdelmlak24/platform_frontend)
- **Service IA** FastAPI — [github.com/khouloudabdelmlak24/platform_ia](https://github.com/khouloudabdelmlak24/platform_ia)

## Prérequis

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) installé et démarré
- Le port 3306 libre (arrêter MySQL dans XAMPP si besoin)

## Structure attendue

Ce fichier `docker-compose.yml` doit être placé dans un dossier contenant aussi les trois projets suivants, clonés côte à côte :

```
Downloads/
  docker-compose.yml
  platform/        (backend)
  frontend/        (frontend)
../ia_service/     (service IA, un niveau au-dessus)
```

## Lancer le projet

```bash
docker compose up --build
```

Au premier lancement, la construction peut prendre plusieurs minutes (téléchargement des images de base).

## Accès une fois démarré

| Service | URL |
|---|---|
| Frontend | http://localhost:4200 |
| Backend (santé) | http://localhost:8082/actuator/health |
| Service IA (santé) | http://localhost:8001/health |

La base de données MySQL créée par Docker est **vide** au premier lancement : créer un compte via la page `/register` pour tester.

## Arrêter le projet

```bash
docker compose down
```