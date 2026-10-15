# tp-jwt-spring

Authentification JWT avec Spring Boot 3, Spring Security 6, Spring Data JPA (H2) et JJWT 0.12.
Reconstitué à partir de 3 enregistrements du TP (08/10/2026).

## Lancer

Java 21 requis (Maven est inclus dans IntelliJ) :

    mvn spring-boot:run

(ou ouvrir le dossier dans IntelliJ et lancer `TpJwtSpringApplication`).
Console H2 : http://localhost:8080/h2-console  (JDBC URL : `jdbc:h2:mem:securitydb`, user `sa`, mot de passe vide)

## Tester

    # 1. Créer un compte
    curl -X POST http://localhost:8080/auth/register \
         -H "Content-Type: application/json" \
         -d '{"email":"sanae@test.ma","password":"1234"}'

    # 2. Se connecter -> renvoie {"token":"..."}
    curl -X POST http://localhost:8080/auth/login \
         -H "Content-Type: application/json" \
         -d '{"email":"sanae@test.ma","password":"1234"}'

    # 3. Appeler l'API protégée avec le token
    curl http://localhost:8080/api/profile -H "Authorization: Bearer <TOKEN>"

Sans token, `/api/profile` répond 401.

## Origine du code

| Fichier | Source |
|---|---|
| `application.properties`, `UserRepository`, DTO, `CustomUserDetailsService`, `JwtService` | diapositives et IntelliJ (vidéos 1 à 3) |
| `AppUser`, `AuthController` (`register`, `login`), `PasswordEncoder` et `AuthenticationManager` de `SecurityConfig` | IntelliJ (vidéos 1 à 3) |
| `pom.xml`, `JwtFilter`, `UserController`, `SecurityFilterChain`, champs et constructeur de `AuthController` | **reconstruits**, jamais montrés en entier dans les vidéos |
