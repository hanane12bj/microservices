Voici le fichier **README** reformulé et sans emojis :

---

# Application E-Commerce Microservices

Cette application e-commerce repose sur une architecture microservices conçue avec Spring Boot et Spring Cloud.
Elle illustre la mise en place d’un écosystème distribué pour la gestion complète d’un système e-commerce.

---

## Architecture générale

L’application est composée de plusieurs microservices indépendants qui communiquent entre eux pour assurer la gestion des clients, des produits et des factures.

### Services d’infrastructure

#### Discovery Service

* Basé sur Netflix Eureka Server
* Permet l’enregistrement et la découverte dynamique des microservices
* Facilite la communication entre services sans configuration statique

#### Config Service

* Service de configuration centralisée basé sur Spring Cloud Config
* Gère les paramètres de configuration de tous les microservices depuis le dépôt `config-repo`
* Supporte différents profils d’environnement (ex. : dev, prod)

#### Gateway Service

* Point d’entrée unique pour l’ensemble des microservices, construit avec Spring Cloud Gateway
* Assure le routage intelligent des requêtes vers les services concernés
* Intègre la découverte dynamique via Eureka

---

### Services métier

#### Customer Service

* Gère les opérations liées aux clients (création, consultation, mise à jour)
* Implémente Spring Data JPA avec H2 comme base de données en mémoire
* Expose une API REST pour les opérations CRUD

#### Inventory Service

* Gère le catalogue des produits et leur stock
* Fournit une API REST pour la gestion des produits

#### Billing Service

* Assure la gestion des factures et des articles de facturation
* Utilise OpenFeign pour communiquer avec Customer Service et Inventory Service
* Crée automatiquement des factures associées aux clients et aux produits

---

## Technologies utilisées

* **Backend** : Spring Boot 3.5.7, Spring Cloud 2025.0.0
* **Base de données** : H2 (in-memory)
* **Service Discovery** : Netflix Eureka
* **API Gateway** : Spring Cloud Gateway
* **Configuration centralisée** : Spring Cloud Config
* **Communication inter-services** : OpenFeign
* **Java** : 21
* **Build** : Maven

---

## Structure du projet

```
ecom/
├── discovery-service/      # Service de découverte Eureka
├── config-service/         # Service de configuration centralisée
├── gateway-service/        # API Gateway
├── customer-service/       # Service de gestion des clients
├── inventory-service/      # Service de gestion des produits
├── billing-service/        # Service de gestion des factures
└── config-repo/            # Dépôt de configurations
```

---

## Démarrage de l’application

1. Démarrer le **Discovery Service**
2. Démarrer le **Config Service**
3. Démarrer le **Gateway Service**
4. Démarrer les services métier (**Customer**, **Inventory**, **Billing**)

Les services doivent être démarrés dans cet ordre afin d’assurer la découverte et la configuration correcte des microservices.
