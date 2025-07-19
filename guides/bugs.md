# Gestion des Bugs

## Créer un bug

- **Endpoint:** `POST /api/bugs/:projectId`
- **Authentification requise:** Oui
- **Paramètres d’URL:** `projectId` — ID du projet lié
- **Payload:**

```json
{
  "title": "Titre du bug",
  "description": "Description détaillée",
  "type": "log | error | warning | info",
  "status": "en cours | terminée | supprimée"
}

- Réponse: Objet bug créé

## Lister les bugs

- **Endpoint:** `GET /api/bugs/registry/all`

- **Authentification requise:** Oui

- **Query Params (facultatifs):**

| Param     | Description                 |
| --------- | --------------------------- |
| projectId | Filtrer par projet          |
| type      | Filtrer par type de bug     |
| status    | Filtrer par statut          |
| from      | Date début (YYYY-MM-DD)     |
| to        | Date fin (YYYY-MM-DD)       |
| page      | Numéro de page (pagination) |
| limit     | Nombre d’éléments par page  |


- Réponse: Liste paginée de bugs

**Erreurs courantes**

- **403 Forbidden :** Accès interdit au projet

- **401 Unauthorized :** Token manquant ou invalide

## Delete Bug 

- **Endpoint:** `DELETE /api/bugs/:bugId`
- **Authentification requise:** Oui
- **Paramètres d’URL:** `bugId` — ID du bug à supprimer
- **Payload:**

- Réponse: Bug supprimer

## Statistique Bug

- **Endpoint:** `GET /api/bugs/:registry/stats`
- **Authentification requise:** Oui

