# Application Bancaire Spring Boot

Une application REST API pour la gestion de comptes bancaires développée avec Spring Boot, H2 Database et Swagger.

## 📋 Description

Cette application permet de gérer des comptes bancaires (COURANT et EPARGNE) avec des opérations CRUD complètes via une API RESTful.

## 🛠️ Technologies Utilisées

- **Spring Boot 2.7.18**
- **Spring Data JPA** - Persistance des données
- **H2 Database** - Base de données en mémoire
- **Lombok** - Réduction du code boilerplate
- **Swagger/OpenAPI** - Documentation de l'API
- **Jackson XML** - Support XML/JSON
- **Maven** - Gestion des dépendances

## 📦 Prérequis

- Java 11 ou supérieur
- Maven 3.6+ (ou utiliser le Maven wrapper inclus)

## 🚀 Installation et Lancement

### 1. Cloner le projet
```bash
git clone <url-du-repo>
cd spring
```

### 2. Compiler le projet
```bash
./mvnw clean install
```

### 3. Lancer l'application
```bash
./mvnw spring-boot:run
```

L'application démarre sur le port **8086** : `http://localhost:8086`

## 📚 Endpoints API

### Base URL : `/banque`

| Méthode | Endpoint | Description |
|---------|----------|-------------|
| GET | `/banque/comptes` | Récupérer tous les comptes |
| GET | `/banque/comptes/{id}` | Récupérer un compte par ID |
| POST | `/banque/comptes` | Créer un nouveau compte |
| PUT | `/banque/comptes/{id}` | Mettre à jour un compte |
| DELETE | `/banque/comptes/{id}` | Supprimer un compte |

### Formats supportés
- **JSON** : `Content-Type: application/json`
- **XML** : `Content-Type: application/xml`

## 📄 Exemple de Requêtes

### Créer un compte (JSON)
```bash
curl -X POST http://localhost:8086/banque/comptes \
  -H "Content-Type: application/json" \
  -d '{
    "solde": 5000.0,
    "dateCreation": "2025-10-30",
    "type": "COURANT"
  }'
```

### Récupérer tous les comptes
```bash
curl http://localhost:8086/banque/comptes
```

### Récupérer un compte par ID
```bash
curl http://localhost:8086/banque/comptes/1
```

### Mettre à jour un compte
```bash
curl -X PUT http://localhost:8086/banque/comptes/1 \
  -H "Content-Type: application/json" \
  -d '{
    "solde": 7500.0,
    "dateCreation": "2025-10-30",
    "type": "EPARGNE"
  }'
```

### Supprimer un compte
```bash
curl -X DELETE http://localhost:8086/banque/comptes/1
```

## 🗄️ Base de Données H2

### Console H2
Accéder à la console H2 : `http://localhost:8086/h2-console`

**Configuration de connexion :**
- **JDBC URL** : `jdbc:h2:mem:banque`
- **Username** : `sa`
- **Password** : *(laisser vide)*

## 📖 Documentation Swagger

Accéder à la documentation interactive de l'API :
- **Swagger UI** : `http://localhost:8086/swagger-ui.html`
- **OpenAPI JSON** : `http://localhost:8086/v3/api-docs`

## 🏗️ Structure du Projet

```
src/main/java/ma/rest/spring/
├── Application.java              # Point d'entrée de l'application
├── controllers/
│   └── CompteController.java     # Contrôleur REST
├── entities/
│   ├── Compte.java               # Entité JPA Compte
│   └── TypeCompte.java           # Énumération des types de compte
└── repositories/
    └── CompteRepository.java     # Repository JPA
```

## 🔧 Configuration

Le fichier `application.properties` contient toutes les configurations :

```properties
# Port du serveur
server.port=8086

# Configuration H2
spring.datasource.url=jdbc:h2:mem:banque
spring.datasource.username=sa
spring.datasource.password=

# Console H2
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

# JPA/Hibernate
spring.jpa.hibernate.ddl-auto=update
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
```

## 📊 Modèle de Données

### Entité Compte

| Champ | Type | Description |
|-------|------|-------------|
| id | Long | Identifiant unique (auto-généré) |
| solde | double | Solde du compte |
| dateCreation | Date | Date de création du compte |
| type | TypeCompte | Type de compte (COURANT/EPARGNE) |

### Types de Compte
- **COURANT** : Compte courant
- **EPARGNE** : Compte épargne

## 🎯 Fonctionnalités

- ✅ CRUD complet pour les comptes bancaires
- ✅ Support JSON et XML
- ✅ Base de données H2 en mémoire
- ✅ Documentation API avec Swagger
- ✅ Console H2 pour la gestion de la base
- ✅ Initialisation automatique avec des données de test
- ✅ Gestion des erreurs (404 Not Found, etc.)
- ✅ Architecture REST standard

## 🧪 Tests

### Lancer les tests
```bash
./mvnw test
```

## 📝 Notes

- Les données sont stockées en mémoire et sont perdues au redémarrage
- Trois comptes sont créés automatiquement au démarrage pour les tests
- L'application utilise Lombok pour réduire le code boilerplate

## 👥 Auteur

Développé dans le cadre du cours de Spring Boot

## 📄 Licence

Ce projet est à usage éducatif.

