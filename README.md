# DevOps Pipeline pour le Projet Station de Ski

Ce projet implémente un pipeline CI/CD complet pour l'application **Station de Ski**, en utilisant plusieurs outils DevOps. Le pipeline inclut des étapes pour le contrôle de version, la compilation, les tests, l'analyse de code, le déploiement sur Nexus, la gestion des conteneurs Docker, et la surveillance avec Grafana et Prometheus.

## Fonctionnalités Principales
- **Contrôle de version avec Git** : Synchronisation du code source depuis un dépôt GitHub.
- **Build Maven** : Nettoyage et compilation du projet Java avec Maven.
- **Tests unitaires avec JaCoCo** : Exécution des tests et génération de rapports de couverture de code.
- **Analyse statique avec SonarQube** : Évaluation de la qualité du code pour détecter les problèmes de sécurité et de performance.
- **Déploiement Nexus** : Publication des artefacts Maven dans un repository Nexus.
- **Gestion des conteneurs avec Docker** : Construction, déploiement et gestion des conteneurs Docker.
- **Surveillance avec Grafana et Prometheus** : Surveillance des performances et des métriques système.

---

## Technologies Utilisées
- **Jenkins** : Automatisation du pipeline CI/CD.
- **Git** : Gestion du code source.
- **Maven** : Outil de build et de gestion de dépendances.
- **SonarQube** : Analyse de la qualité du code.
- **Docker** : Conteneurisation des applications.
- **Grafana** : Visualisation des métriques.
- **Prometheus** : Collecte et stockage des métriques.
- **Nexus** : Repository pour la gestion des artefacts.

---

## Structure du Pipeline Jenkins

### 1. **Checkout Git**
Clonage du code source depuis le dépôt Git :
```groovy
git branch: 'Wael', credentialsId: '486a5359-e642-41df-bbc8-d1cfd0e3ad20', url: 'https://github.com/yasminenasfi2001/DevOps_Station_Ski.git'
