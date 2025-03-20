
# Documentation de l'API

## Accéder à Swagger UI
Une documentation interactive de l'API est disponible via Swagger. Vous pouvez y accéder à l'adresse suivante :

Swagger UI : [http://localhost:8000/swagger/](http://localhost:8000/swagger/)

## Authentification
L'API utilise JSON Web Tokens (JWT) pour l'authentification. Voici comment obtenir et utiliser un token d'accès.

### 1. Obtenir un token d'accès
Envoyez une requête POST à `/api/token/` avec les identifiants de l'utilisateur.

#### Requête :
```json
POST /api/token/
Content-Type: application/json

{
    "username": "votre_nom_utilisateur",
    "password": "votre_mot_de_passe"
}
```

#### Réponse :
```json
{
    "refresh": "token_de_refresh",
    "access": "token_d_acces"
}
```

### 2. Utiliser le token d'accès
Pour accéder aux endpoints protégés, incluez le token d'accès dans le header `Authorization`.

#### Exemple :
```http
Authorization: Bearer token_d_acces
```

### 3. Rafraîchir le token d'accès
Lorsque le token d'accès expire, utilisez le token de rafraîchissement pour en obtenir un nouveau.

#### Requête :
```json
POST /api/token/refresh/
Content-Type: application/json

{
    "refresh": "token_de_refresh"
}
```

#### Réponse :
```json
{
    "access": "nouveau_token_d_acces"
}
```

## Endpoints Principaux

### 1. Catégories

#### 1.1. Lister toutes les catégories
**Requête** :
```http
GET /api/categories/
Authorization: Bearer token_d_acces
```
**Réponse** :
```json
[
    {
        "id": 1,
        "name": "Électronique",
        "description": "Catégorie pour les produits électroniques",
        "active": true,
        "date_created": "2023-10-01T12:00:00Z",
        "date_updated": "2023-10-01T12:00:00Z"
    },
    {
        "id": 2,
        "name": "Vêtements",
        "description": "Catégorie pour les vêtements",
        "active": true,
        "date_created": "2023-10-01T12:00:00Z",
        "date_updated": "2023-10-01T12:00:00Z"
    }
]
```

#### 1.2. Créer une nouvelle catégorie
**Requête** :
```http
POST /api/categories/
Authorization: Bearer token_d_acces
Content-Type: application/json

{
    "name": "Électronique",
    "description": "Catégorie pour les produits électroniques",
    "active": true
}
```
**Réponse** :
```json
{
    "id": 1,
    "name": "Électronique",
    "description": "Catégorie pour les produits électroniques",
    "active": true,
    "date_created": "2023-10-01T12:00:00Z",
    "date_updated": "2023-10-01T12:00:00Z"
}
```

#### 1.3. Récupérer une catégorie spécifique
**Requête** :
```http
GET /api/categories/1/
Authorization: Bearer token_d_acces
```
**Réponse** :
```json
{
    "id": 1,
    "name": "Électronique",
    "description": "Catégorie pour les produits électroniques",
    "active": true,
    "date_created": "2023-10-01T12:00:00Z",
    "date_updated": "2023-10-01T12:00:00Z"
}
```

#### 1.4. Mettre à jour une catégorie
**Requête** :
```http
PUT /api/categories/1/
Authorization: Bearer token_d_acces
Content-Type: application/json

{
    "name": "Électronique Modifié",
    "description": "Nouvelle description",
    "active": false
}
```
**Réponse** :
```json
{
    "id": 1,
    "name": "Électronique Modifié",
    "description": "Nouvelle description",
    "active": false,
    "date_created": "2023-10-01T12:00:00Z",
    "date_updated": "2023-10-01T12:00:00Z"
}
```

#### 1.5. Supprimer une catégorie
**Requête** :
```http
DELETE /api/categories/1/
Authorization: Bearer token_d_acces
```
**Réponse** :
```http
HTTP 204 No Content
```

### 2. Produits

#### 2.1. Lister tous les produits
**Requête** :
```http
GET /api/products/
Authorization: Bearer token_d_acces
```
**Réponse** :
```json
[
    {
        "id": 1,
        "name": "Smartphone",
        "description": "Un smartphone haut de gamme",
        "active": true,
        "category": 1,
        "date_created": "2023-10-01T12:00:00Z",
        "date_updated": "2023-10-01T12:00:00Z"
    }
]
```

#### 2.2. Créer un nouveau produit
**Requête** :
```http
POST /api/products/
Authorization: Bearer token_d_acces
Content-Type: application/json

{
    "name": "Smartphone",
    "description": "Un smartphone haut de gamme",
    "active": true,
    "category": 1
}
```
**Réponse** :
```json
{
    "id": 1,
    "name": "Smartphone",
    "description": "Un smartphone haut de gamme",
    "active": true,
    "category": 1,
    "date_created": "2023-10-01T12:00:00Z",
    "date_updated": "2023-10-01T12:00:00Z"
}
```

#### 2.3. Récupérer un produit spécifique
**Requête** :
```http
GET /api/products/1/
Authorization: Bearer token_d_acces
```
**Réponse** :
```json
{
    "id": 1,
    "name": "Smartphone",
    "description": "Un smartphone haut de gamme",
    "active": true,
    "category": 1,
    "date_created": "2023-10-01T12:00:00Z",
    "date_updated": "2023-10-01T12:00:00Z"
}
```

#### 2.4. Mettre à jour un produit
**Requête** :
```http
PUT /api/products/1/
Authorization: Bearer token_d_acces
Content-Type: application/json

{
    "name": "Smartphone Modifié",
    "description": "Nouvelle description",
    "active": false,
    "category": 1
}
```
**Réponse** :
```json
{
    "id": 1,
    "name": "Smartphone Modifié",
    "description": "Nouvelle description",
    "active": false,
    "category": 1,
    "date_created": "2023-10-01T12:00:00Z",
    "date_updated": "2023-10-01T12:00:00Z"
}
```

#### 2.5. Supprimer un produit
**Requête** :
```http
DELETE /api/products/1/
Authorization: Bearer token_d_acces
```
**Réponse** :
```http
HTTP 204 No Content
```

### 3. Articles

#### 3.1. Lister tous les articles
**Requête** :
```http
GET /api/articles/
Authorization: Bearer token_d_acces
```
**Réponse** :
```json
[
    {
        "id": 1,
        "name": "iPhone 15",
        "description": "Dernier modèle d'iPhone",
        "active": true,
        "price": "999.99",
        "product": 1,
        "date_created": "2023-10-01T12:00:00Z",
        "date_updated": "2023-10-01T12:00:00Z"
    }
]
```

#### 3.2. Créer un nouvel article
**Requête** :
```http
POST /api/articles/
Authorization: Bearer token_d_acces
Content-Type: application/json

{
    "name": "iPhone 15",
    "description": "Dernier modèle d'iPhone",
    "active": true,
    "price": "999.99",
    "product": 1
}
```
**Réponse** :
```json
{
    "id": 1,
    "name": "iPhone 15",
    "description": "Dernier modèle d'iPhone",
    "active": true,
    "price": "999.99",
    "product": 1,
    "date_created": "2023-10-01T12:00:00Z",
    "date_updated": "2023-10-01T12:00:00Z"
}
```

#### 3.3. Récupérer un article spécifique
**Requête** :
```http
GET /api/articles/1/
Authorization: Bearer token_d_acces
```
**Réponse** :
```json
{
    "id": 1,
    "name": "iPhone 15",
    "description": "Dernier modèle d'iPhone",
    "active": true,
    "price": "999.99",
    "product": 1,
    "date_created": "2023-10-01T12:00:00Z",
    "date_updated": "2023-10-01T12:00:00Z"
}
```

#### 3.4. Mettre à jour un article
**Requête** :
```http
PUT /api/articles/1/
Authorization: Bearer token_d_acces
Content-Type: application/json

{
    "name": "iPhone 15 Pro",
    "description": "Modèle haut de gamme",
    "active": false,
    "price": "1199.99",
    "product": 1
}
```
**Réponse** :
```json
{
    "id": 1,
    "name": "iPhone 15 Pro",
    "description": "Modèle haut de gamme",
    "active": false,
    "price": "1199.99",
    "product": 1,
    "date_created": "2023-10-01T12:00:00Z",
    "date_updated": "2023-10-01T12:00:00Z"
}
```

#### 3.5. Supprimer un article
**Requête** :
```http
DELETE /api/articles/1/
Authorization: Bearer token_d_acces
```
**Réponse** :
```http
HTTP 204 No Content
```

## Tests
Pour exécuter les tests unitaires, utilisez la commande suivante :
```bash
python manage.py test
```
