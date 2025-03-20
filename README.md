Documentation de l'API
Accéder à Swagger UI
Une documentation interactive de l'API est disponible via Swagger. Vous pouvez y accéder à l'adresse suivante :

Swagger UI : http://localhost:8000/swagger/

Authentification
L'API utilise JSON Web Tokens (JWT) pour l'authentification. Voici comment obtenir et utiliser un token d'accès.

1. Obtenir un token d'accès
Envoyez une requête POST à /api/token/ avec les identifiants de l'utilisateur.

Requête :

POST /api/token/
Content-Type: application/json

{
    "username": "votre_nom_utilisateur",
    "password": "votre_mot_de_passe"
}


Réponses:

{
    "refresh": "token_de_refresh",
    "access": "token_d_acces"
}
