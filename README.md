ma.enset.jwtdemo
├── config
│   └── SecurityConfig.java         # Configuration de Spring Security & Filter Chain
├── controller
│   ├── AuthController.java         # Endpoints d'inscription et de connexion
│   └── UserController.java         # Endpoints sécurisés de démonstration
├── dto
│   ├── AuthResponse.java           # DTO de retour contenant le token JWT
│   ├── LoginRequest.java           # DTO pour la connexion
│   └── RegisterRequest.java        # DTO pour l'inscription
├── entity
│   └── AppUser.java                # Entité JPA Utilisateur
├── repository
│   └── UserRepository.java         # Interface Repository Spring Data
├── security
│   ├── JwtFilter.java              # Filtre HTTP d'interception et validation du JWT
│   └── JwtService.java             # Service de génération et de parsing des tokens JWT
└── service
    └── CustomUserDetailsService.java# Implémentation personnalisée de UserDetailsService
```[cite: 1]

---

## ⚙️ Configuration (`application.properties`)

```properties
spring.application.name=jwt-demo
spring.datasource.url=jdbc:h2:mem:securitydb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.jpa.hibernate.ddl-auto=update
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

jwt.secret=VGhpcy1pcy1hLXZlcnktbG9uZy1zZWNyZXQta2V5LWZvci1qd3QtZGVtby0yMDI2
jwt.expiration=3600000
```

---

## 🚀 Lancement de l'Application

1. Cloner le projet :
   ```bash
   git clone https://github.com/sanaetimourti/tp-jwt-spring-.git
   cd tp-jwt-spring-
