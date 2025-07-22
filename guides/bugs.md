# Gestion des Bugs

## Créer un bug

Méthode : POST

URL : /api/bugs/:projectId

Authentification requise : ✅ Oui

Paramètre d'URL :

projectId (string) — ID du projet concerné

📨 Payload (body JSON)
json

{
"title": "Titre du bug",
"description": "Description détaillée",
"type": "log | error | warning | info",
"status": "en cours | terminée | supprimée"
}
✅ Réponse :

Un objet bug créé avec son ID, la date de création, etc.

## Lister les bugs (filtrés et paginés)

Méthode : GET

URL : /api/bugs

Authentification requise : ✅ Oui

Query parameters (facultatifs) :

Paramètre Description
projectId Filtrer les bugs d’un projet
type log, error, warning, info
status en cours, terminée, supprimée
from Date de début (format : YYYY-MM-DD)
to Date de fin (format : YYYY-MM-DD)
offset Index de départ (pagination, par défaut : 0)
limit Nombre d’éléments (pagination, par défaut : 10)

✅ Réponse :
json
{
"total": 42,
"limit": 10,
"offset": 0,
"bugs": [ ... ]
}

## Supprimer un bug
Méthode : DELETE

URL : /api/bugs/:bugId

Authentification requise : ✅ Oui

Paramètre d'URL :

bugId (string) — ID du bug à supprimer

✅ Réponse :

json
{
"message": "Bug supprimé avec succès"
}

### Erreurs courantes

Code Signification

401 Unauthorized Token manquant ou invalide

403 Forbidden Accès refusé (projet non appartenant à l'utilisateur)

404 Not Found Bug ou projet introuvable

500 Internal Server Error Erreur serveur inattendue
