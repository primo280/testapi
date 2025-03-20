Guide d'utilisation de l'API Shop
Cette API RESTful permet la gestion des utilisateurs, des catégories, des produits et des articles.

Prérequis
Python 3.8 ou supérieur
pip (gestionnaire de paquets Python)
virtualenv (optionnel, mais recommandé pour isoler l'environnement)
Installation
Cloner le dépôt :

git clone https://github.com/votre-utilisateur/shop_api.git
Naviguer dans le répertoire du projet :

cd shop_api
Créer et activer un environnement virtuel :

python -m venv env
source env/bin/activate  # Sur Windows : env\Scripts\activate
Installer les dépendances :

pip install -r requirements.txt
Appliquer les migrations de la base de données :

python manage.py makemigrations
python manage.py migrate
Créer un superutilisateur pour accéder à l'interface d'administration :

python manage.py createsuperuser
Lancer le serveur de développement :

python manage.py runserver
Documentation de l'API
Une documentation interactive de l'API est disponible via Swagger.

Accéder à Swagger UI : http://localhost:8000/swagger/
Cette interface vous permet de visualiser et de tester les différents endpoints de l'API.

Authentification
L'API utilise JSON Web Tokens (JWT) pour l'authentification.

Obtenir un token d'accès :

Envoyer une requête POST à /api/token/ avec les identifiants de l'utilisateur :

{
    "username": "votre_nom_utilisateur",
    "password": "votre_mot_de_passe"
}
La réponse contiendra les tokens d'accès et de rafraîchissement :

{
    "refresh": "token_de_refresh",
    "access": "token_d_acces"
}
Utiliser le token d'accès :

Pour accéder aux endpoints protégés, inclure le token d'accès dans le header Authorization :

Authorization: Bearer token_d_acces
Rafraîchir le token d'accès :

Lorsque le token d'accès expire, utiliser le token de rafraîchissement pour en obtenir un nouveau en envoyant une requête POST à /api/token/refresh/ :

{
    "refresh": "token_de_refresh"
}
La réponse fournira un nouveau token d'accès :

{
    "access": "nouveau_token_d_acces"
}
Endpoints Principaux
1. Catégories
Lister toutes les catégories

Requête :

GET /api/categories/
Réponse :

[
    {
        "id": 1,
        "name": "Électronique",
        "description": "Appareils électroniques et gadgets.",
        "active": true,
        "date_created": "2025-03-15T10:00:00Z",
        "date_updated": "2025-03-15T10:00:00Z"
    },
    {
        "id": 2,
        "name": "Vêtements",
        "description": "Vêtements pour hommes et femmes.",
        "active": true,
        "date_created": "2025-03-16T11:30:00Z",
        "date_updated": "2025-03-16T11:30:00Z"
    }
]
Créer une nouvelle catégorie

Requête :

POST /api/categories/
Corps de la requête :

{
    "name": "Livres",
    "description": "Livres de tous genres.",
    "active": true
}
Réponse :

{
    "id": 3,
    "name": "Livres",
    "description": "Livres de tous genres.",
    "active": true,
    "date_created": "2025-03-20T14:00:00Z",
    "date_updated": "2025-03-20T14:00:00Z"
}
Récupérer une catégorie spécifique

Requête :

GET /api/categories/1/
Réponse :

{
    "id": 1,
    "name": "Électronique",
    "description": "Appareils électroniques et gadgets.",
    "active": true,
    "date_created": "2025-03-15T10:00:00Z",
    "date_updated": "2025-03-15T10:00:00Z"
}
Mettre à jour une catégorie

Requête :

PUT /api/categories/1/
Corps de la requête :

{
    "name": "Électronique et Gadgets",
    "description": "Tous les appareils électroniques et gadgets.",
    "active": true
}
Réponse :

{
    "id": 1,
    "name": "Électronique et Gadgets",
    "description": "Tous les appareils électroniques et gadgets.",
    "active": true,
    "date_created": "2025-03-15T10:00:00Z",
    "date_updated": "2025-03-20T14:54 
