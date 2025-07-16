# Error Handling

L’API utilise les **codes HTTP standards** pour signaler le succès ou l’échec d’une requête.  
Les erreurs retournent généralement une réponse JSON avec une clé `message` (et parfois `code` si pertinent).

---

## Structure de réponse d'erreur

### Erreur simple (ex. authentification)

```json
{
  "message": "Identifiants invalides"
}

### Erreur de validation (ex. champ manquant)

{
  "message": "Email déjà utilisé"
}

🔢 Principaux codes HTTP utilisés

| HTTP Status Code            | Exemple de message           |Description                                          |
| --------------------------- | ---------------------------- | --------------------------------------------------- |
| `200 OK`                    | *N/A*                        | Requête réussie                                     |
| `201 Created`               | *N/A*                        | Ressource créée (projet ou bug)                     |
| `400 Bad Request`           | `"Champs manquants"`         | Données invalides ou incomplètes                    |
| `401 Unauthorized`          | `"Non autorisé"`             | Token JWT manquant, invalide ou expiré              |
| `403 Forbidden`             | `"Accès interdit au projet"` | L’utilisateur ne possède pas les droits nécessaires |
| `404 Not Found`             | `"Ressource introuvable"`    | Projet ou bug non trouvé                            |
| `429 Too Many Requests`     | `"Trop de requêtes"`         | (à implémenter si rate limiting actif)              |
| `500 Internal Server Error` | `"Erreur serveur"`           | Erreur inattendue côté serveur                      |


📌 Cas spécifiques

🔐 Authentification

**Token manquant ou invalide :**
json
{
  "message": "Non autorisé"
}

**Mauvais identifiants :**
json
{
  "message": "Identifiants invalides"
}

📁 Projet

**Dépassement de limite :**
json
{
  "message": "Limite de projets atteinte"
}

🐛 Bug

**Tentative d’accès à un projet d’un autre utilisateur :**
json
{
  "message": "Accès interdit au projet"
}
