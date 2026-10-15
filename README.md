# 🔐 Spring Boot JWT Authentication & Authorization API

Ce projet est une application web RESTful développée avec **Spring Boot 3**, **Spring Security** et **JWT (JSON Web Tokens)**. Il fournit un système complet d'inscription, de connexion et de sécurisation des endpoints d'API via des tokens stateless[cite: 1, 13, 14, 15, 16].

---

## 🚀 Fonctionnalités
- **Inscription (`/auth/register`)** : Création de nouveaux comptes utilisateurs avec hachage des mots de passe BCrypt[cite: 12, 14].
- **Connexion (`/auth/login`)** : Authentification et génération d'un jeton JWT signé[cite: 8, 15].
- **Protection des endpoints (`/api/**`)** : Interception des requêtes par un filtre JWT personnalisée et vérification de la validité du token[cite: 10, 11, 13].
- **Gestion des utilisateurs** : Récupération des informations du profil de l'utilisateur connecté via le contexte de sécurité[cite: 11, 16].
- **Console H2** : Base de données en mémoire intégrée pour faciliter le développement et le débogage.

---

## 🛠️ Stack Technique & Dépendances
- **Java** : Version 17 ou supérieure
- **Framework** : Spring Boot 3[cite: 1]
- **Sécurité** : Spring Security & Spring Data JPA[cite: 3, 12]
- **Base de données** : H2 Database (In-Memory)
- **Token JWT** : `io.jsonwebtoken` (JJWT v0.13.0)[cite: 2]

---

## Structure du Projet

```text
ma.enset.jwtdemo
├── config
│   └── SecurityConfig.java          # Configuration de la chaîne de filtres Spring Security
├── controller
│   ├── AuthController.java          # Contrôleur pour /auth/register et /auth/login
│   └── UserController.java          # Endpoints REST protégés (/api/hello, /api/profile)
├── dto
│   ├── AuthResponse.java            # DTO de réponse avec le jeton JWT
│   ├── LoginRequest.java            # DTO pour les requêtes de connexion
│   └── RegisterRequest.java         # DTO pour les requêtes d'inscription
├── entity
│   └── AppUser.java                 # Entité Utilisateur JPA
├── repository
│   └── UserRepository.java          # Interface Spring Data JPA pour AppUser
├── security
│   ├── JwtFilter.java               # Filtre personnalisé interceptant les requêtes HTTP
│   └── JwtService.java              # Utility Class pour la création et la validation des JWT
└── service
    └── CustomUserDetailsService.java # Service chargeant les utilisateurs depuis la base H2
```file:///C:/Users/SANAE%20PC/Desktop/Capture%20d%E2%80%99%C3%A9cran%202026-10-15%20193950.png


---

## Configuration (`application.properties`)

```properties
spring.application.name=jwt-demo

# Configuration de la BDD H2
spring.datasource.url=jdbc:h2:mem:securitydb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# Activation de la console Web H2
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

# Propriétés du JWT
jwt.secret=VGhpcy1pcy1hLXZlcnktbG9uZy1zZWNyZXQta2V5LWZvci1qd3QtZGVtby0yMDI2
jwt.expiration=3600000
```

---

##  Démarrage du Projet

### Prérequis
- **JDK 17** ou plus récent installé.
- **Maven** (ou le wrapper `./mvnw` inclus dans le projet).

### Étapes de lancement

1. **Cloner le dépôt :**
   ```bash
   git clone [https://github.com/sanaetimourti/tp-jwt-spring-.git](https://github.com/sanaetimourti/tp-jwt-spring-.git)
   cd tp-jwt-spring-
