# À table — planning de menus

Application mobile (page web installable) pour préparer les menus de la semaine :
semainier coloré (midi, goûter, dîner), choix des recettes en photos, totaux nutritionnels
par jour et par semaine, liste des courses à cocher.

> **Version maquette** : les recettes sont des exemples et les modifications ne sont pas
> encore enregistrées (elles disparaissent si on recharge la page).

## Contenu

| Fichier | Rôle |
|---|---|
| `index.html` | L'application (un seul fichier, sans installation) |
| `manifest.webmanifest`, `icons/` | Permet d'ajouter l'application à l'écran d'accueil du téléphone |
| `recettes/recettes-modele.json` | Modèle de fichier pour importer des recettes |
| `recettes/recettes.schema.json` | Règles du format d'import |

## Publication avec GitHub Pages

1. Sur GitHub : **New repository** → nom `a-table` → **Public** → **Create repository**.
2. **Add file → Upload files**, glisser **tout le contenu** du dossier (pas le dossier lui-même), puis **Commit changes**.
3. **Settings → Pages** → Source **Deploy from a branch** → Branch **main** / **/(root)** → **Save**.
4. Après 1 à 2 minutes, l'adresse s'affiche : `https://<votre-compte>.github.io/a-table/`.
5. Sur le téléphone, ouvrir cette adresse puis **Ajouter à l'écran d'accueil**.
