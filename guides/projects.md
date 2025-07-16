# Gestion des Projets

## Création d’un projet

- **Endpoint:** `POST /api/projects`
- **Authentification requise:** Oui (JWT dans header `Authorization`)
- **Payload:**

```json
{
  "name": "Nom du projet",
  "type": "Type du projet (ex: web, mobile)"
}

* Limite: 5 projets max par utilisateur

- Réponse: Objet projet créé avec ID, timestamps, etc.

## Récupérer les projets

- **Endpoint:** `GET /api/projects`

- **Authentification requise:** Oui 

Réponse: Liste des projets de l’utilisateur connecté

** Erreurs courantes ** 

- **403 Forbidden :** Limite de projets atteinte

- **401 Unauthorized :** Token manquant ou invalide