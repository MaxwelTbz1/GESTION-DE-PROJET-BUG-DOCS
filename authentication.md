🔐 Authentification
Cette API utilise des JSON Web Tokens (JWT) pour sécuriser les endpoints. Une stratégie à jeton unique est utilisée : un Access Token (jeton d'accès).

🎫 Jeton d’accès (Access Token)
Utilisation : Obligatoire pour accéder aux routes protégées de l’API.

Format : JWT standard (JSON Web Token).

Transmission : Doit être inclus dans l’en-tête Authorization avec le schéma Bearer.

http
Authorization: Bearer <votre_token_d'accès>
Durée de vie : Les jetons ont une expiration prédéfinie (7 jours, configurée côté serveur).

Obtention : Vous recevez un jeton lors d’un enregistrement ou d’une connexion réussie (/auth/register ou /auth/login).

🔁 Flux d’authentification
S’inscrire ou se connecter : Appelez l’un des endpoints :

POST /api/auth/register

POST /auth/login

👉 En cas de succès, un accessToken est retourné dans le corps de la réponse.

Accéder aux routes protégées :

Incluez le jeton dans l’en-tête HTTP :

http
Authorization: Bearer <accessToken>
Gérer l’expiration du token :

Si vous recevez une erreur 401 Unauthorized, cela signifie que :

- le token est expiré,
  ou 
- invalide.

➡️ L’utilisateur doit se reconnecter via /auth/login.

