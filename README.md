# TP 8 : Spring @RestController

## Description
Projet Spring Boot mettant en œuvre un service RESTful pour la gestion de comptes bancaires.

## Technologies utilisées
- Spring Boot 3.1.5
- Spring Web (REST Controller)
- Spring Data JPA
- H2 Database (base de données en mémoire)
- Lombok
- Swagger/OpenAPI (springdoc-openapi)
- Jackson (support JSON et XML)

## Configuration
- Port du serveur : 8082
- Base de données H2 en mémoire : `jdbc:h2:mem:banque`
- Console H2 : http://localhost:8082/h2-console
- Swagger UI : http://localhost:8082/swagger-ui.html

## Endpoints REST

### Base URL
```
http://localhost:8082/banque
```

### Endpoints disponibles
- `GET /banque/comptes` - Récupérer tous les comptes (JSON/XML)
- `GET /banque/comptes/{id}` - Récupérer un compte par ID (JSON/XML)
- `POST /banque/comptes` - Créer un nouveau compte (JSON/XML)
- `PUT /banque/comptes/{id}` - Mettre à jour un compte (JSON/XML)
- `DELETE /banque/comptes/{id}` - Supprimer un compte

## Formats supportés
- JSON (application/json)
- XML (application/xml)

Les formats sont déterminés automatiquement selon les en-têtes `Accept` et `Content-Type` de la requête HTTP.

## Exécution

### Prérequis
- Java 17+
- Maven 3.6+

### Lancer l'application
```bash
mvn spring-boot:run
```

### Accéder à la console H2
1. Ouvrir http://localhost:8082/h2-console
2. JDBC URL: `jdbc:h2:mem:banque`
3. Username: `sa`
4. Password: (laisser vide)

### Accéder à Swagger UI
Ouvrir http://localhost:8082/swagger-ui.html dans votre navigateur.

## Structure du projet
```
src/
├── main/
│   ├── java/ma/rest/spring/
│   │   ├── entities/
│   │   │   ├── Compte.java
│   │   │   └── TypeCompte.java
│   │   ├── repositories/
│   │   │   └── CompteRepository.java
│   │   ├── web/
│   │   │   └── CompteController.java
│   │   └── MsBanqueApplication.java
│   └── resources/
│       └── application.properties
└── pom.xml
```

## Exemples de requêtes

### GET tous les comptes (JSON)
```bash
curl -X GET "http://localhost:8082/banque/comptes" -H "Accept: application/json"
```

### GET tous les comptes (XML)
```bash
curl -X GET "http://localhost:8082/banque/comptes" -H "Accept: application/xml"
```

### POST créer un compte (JSON)
```bash
curl -X POST "http://localhost:8082/banque/comptes" \
  -H "Content-Type: application/json" \
  -d '{"solde": 1500.0, "dateCreation": "2024-11-01", "type": "COURANT"}'
```

### POST créer un compte (XML)
```bash
curl -X POST "http://localhost:8082/banque/comptes" \
  -H "Content-Type: application/xml" \
  -d '<compte><solde>1500.0</solde><dateCreation>2024-11-01</dateCreation><type>COURANT</type></compte>'
```

### PUT mettre à jour un compte
```bash
curl -X PUT "http://localhost:8082/banque/comptes/1" \
  -H "Content-Type: application/json" \
  -d '{"solde": 2000.0, "dateCreation": "2024-11-01", "type": "EPARGNE"}'
```

### DELETE supprimer un compte
```bash
curl -X DELETE "http://localhost:8082/banque/comptes/1"
```

## Auteur
TP réalisé dans le cadre du cours : Architecture Microservices : Conception, Déploiement et Orchestration

