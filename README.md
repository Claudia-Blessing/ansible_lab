
# Infrastructure as Code et intégration continue – Déploiement d’une application Laravel

## Description

Ce projet a pour objectif de mettre en œuvre les bases du DevOps à travers le déploiement automatisé d’une application web.
L’application Laravel est volontairement simple car elle sert uniquement de support technique afin de se concentrer sur les aspects **Infrastructure as Code**, **automatisation**, et **intégration continue**.

L’accent est mis sur :
- la configuration automatisée d’un serveur Linux,
- le déploiement d’une application,
- la mise en place d’une chaîne CI,
- la structuration d’un projet DevOps évolutif.

---

## Objectifs du projet

- Comprendre et appliquer les principes de DevOps
- Automatiser un déploiement applicatif avec **Ansible**
- Séparer clairement :
  - le code applicatif,
  - l’infrastructure,
  - les pipelines CI
- Mettre en place une **intégration continue (CI)** via GitHub Actions
- Poser des fondations solides avant les prochaines étapes :
  - conteneurisation avec Docker,
  - déploiement Cloud

---

## Architecture générale

- **Machine de contrôle** : WSL Ubuntu
- **Serveur cible** : Serveur Linux privé
- **Communication** : SSH avec authentification par clé
- **Automatisation** : Ansible
- **CI** : GitHub Actions

Le déploiement est effectué et déclenché via Ansible  afin de garder le contrôle total du processus et garantir la compréhension de chaque étape avant automatisation complète.

---

## Dépôts GitHub

Le projet est  séparé en deux dépôts distincts, conformément aux bonnes pratiques DevOps.

### 1. Application (support technique)
- Laravel
- CRUD 
- Aucun objectif avancé côté développement

Lien vers le dépôt de l'application :  
https://github.com/Claudia-Blessing/app_laravel

### 2. Infrastructure et déploiement
- Ansible (Infrastructure as Code)
- Rôles par composant (PHP, MySQL, Nginx, déploiement)
- Gestion des variables et des secrets via Ansible Vault


---

## Stack technique

### Application
- Laravel
- MySQL
- Tailwind CSS
- Vite

### DevOps / Systèmes
- Linux
- Ansible
- SSH
- Git
- GitHub Actions
- Ansible Vault

---

## Automatisation avec Ansible

Le déploiement applicatif est entièrement automatisé via Ansible.

### Fonctionnalités automatisées
- Mise en place de l’environnement serveur
- Installation et configuration de :
  - PHP
  - MySQL
  - Nginx
- Déploiement de l’application depuis GitHub
- Installation des dépendances PHP (Composer)
- Configuration du fichier `.env`
- Génération de la clé applicative Laravel
- Exécution des migrations
- Compilation des assets front-end
- Gestion des permissions
- Déploiement reproductible et idempotent

Les privilèges sont gérés via un utilisateur dédié (`deploy`) avec élévation de privilèges non interactive, permettant une automatisation complète sans intervention humaine.

---

## Intégration continue (CI)

Une pipeline CI a été mise en place avec **GitHub Actions**.

### Objectifs de la CI
- Vérifier l’intégrité du code à chaque push
- S’assurer que le projet est installable
- Valider la cohérence de l’application avant déploiement

### Étapes principales
- Récupération du code
- Installation de l’environnement PHP
- Installation des dépendances Composer
- Initialisation minimale de Laravel
- Build des assets front-end

---

## Gestion des secrets - aspect sécurité

Les informations sensibles ne sont jamais stockées en clair dans les dépôts Git.

- Gestion des mots de passe : `Ansible Vault`
- Accès SSH et secrets CI/CD : `GitHub Secrets`
- Aucun secret n’est versionné

Cette approche garantit un niveau de sécurité cohérent avec des environnements professionnels.

---

## Évolutivité 

- Conteneurisation de l’application avec Docker
- Introduction de Docker Compose
- Déploiement dans un environnement Cloud
- Automatisation complète du CD via runner auto-hébergé

---

## Compétences acquises

Ce projet m’a permis de développer et consolider des compétences orientées **DevOps / systèmes/OPS** :

- Compréhension des principes DevOps
- Infrastructure as Code avec Ansible
- Automatisation de déploiement applicatif
- Gestion des accès et des privilèges (SSH, sudo)
- Sécurisation des secrets
- Mise en place d’une intégration continue (CI)
- Lecture et analyse des logs applicatifs et systèmes
- Structuration d’un projet DevOps évolutif
- Approche progressive et réaliste de l’automatisation

---

## Conclusion

Ce projet constitue une base pour une démarche DevOps.
Il s’inscrit dans une logique d’apprentissage continu et de montée en compétences vers des environnements plus complexes.

