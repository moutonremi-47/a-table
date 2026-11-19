# À table — planning de menus

Application mobile (page web installable) pour préparer les menus de la semaine :
semainier coloré (midi, goûter, dîner), choix des recettes en photos, totaux nutritionnels
par jour et par semaine, liste des courses à cocher.

> Les plannings, les courses cochées et les recettes importées sont **enregistrés
> automatiquement sur le téléphone** (stockage du navigateur). Pensez à exporter une
> sauvegarde de temps en temps : vider les données du navigateur efface tout.

## Contenu

| Fichier | Rôle |
|---|---|
| `index.html` | L'application (un seul fichier, sans installation) |
| `manifest.webmanifest`, `icons/` | Permet d'ajouter l'application à l'écran d'accueil du téléphone |
| `recettes/recettes-modele.json` | Modèle de fichier pour importer des recettes |
| `recettes/recettes.schema.json` | Règles du format d'import |

## Publication avec GitHub Pages

1. Sur GitHub : **New repository** → nom `a-table` → **Public** → **Create repository**.
2. Sur la page du dépôt vide, cliquer sur **uploading an existing file** (ou ouvrir `https://github.com/<votre-compte>/a-table/upload`), glisser **tout le contenu** du dossier (pas le dossier lui-même), puis **Commit changes**.
3. **Settings → Pages** → Source **Deploy from a branch** → Branch **main** / **/(root)** → **Save**.
4. Après 1 à 2 minutes, l'adresse s'affiche : `https://<votre-compte>.github.io/a-table/`.
5. Sur le téléphone, ouvrir cette adresse puis **Ajouter à l'écran d'accueil**.

## Importer des recettes

1. Dans l'application : **➕ Recette → Télécharger le modèle .json**, ou partir de `recettes/recettes-modele.json`.
2. Compléter une entrée par recette dans `"recettes": [ ... ]`. Obligatoire : `nom`, `ingredients`
   (`nom`, `quantite`, `unite`), `etapes`, `nutrition_par_portion` (`kcal`, `proteines_g`, `fibres_g`, `sucres_g`).
   Les quantités sont celles de la recette entière : l'application les divise par `portions`.
3. Photo : mettre dans `"photo"` le **nom du fichier image** (ex. `poulet.jpg`) ou une adresse `https://…`.
4. **➕ Recette → Importer recettes + photos** : sélectionner le `.json` **et** les photos en même temps.
   Les photos sont réduites puis stockées sur le téléphone. Une recette dont l'`id` existe déjà est remplacée.
5. Les erreurs (champ manquant, JSON illisible) sont listées recette par recette.

## Sauvegarde

- **Exporter une sauvegarde** : télécharge `a-table-sauvegarde-AAAA-MM-JJ.json` (plannings, courses, recettes importées et photos).
- **Restaurer une sauvegarde** : choisir ce fichier ; il remplace les données de l'appareil (confirmation demandée).

## Sauvegarde dans GitHub (Gist secret)

1. Sur github.com : photo de profil → **Settings** → **Developer settings** → **Personal access tokens**
   → **Tokens (classic)** → **Generate new token (classic)**.
2. Nom : `À table`, expiration au choix, cocher **uniquement `gist`** → **Generate token**, puis copier le jeton
   (il ne s'affiche qu'une fois).
3. Dans l'application : **➕ Recette** → **Sauvegarde GitHub** → coller le jeton → **Connecter**.
   Un Gist **secret** `a-table-sauvegarde.json` est créé ; il est mis à jour automatiquement après chaque modification.
4. Sur un autre téléphone : coller le même jeton → **Connecter** → **Récupérer depuis GitHub**.

À savoir : un Gist secret n'apparaît pas dans les recherches, mais toute personne qui possède son lien peut le lire.
Le jeton reste sur l'appareil (jamais dans les sauvegardes) ; s'il est perdu ou exposé, le supprimer dans GitHub
(**Personal access tokens → Delete**) et en créer un nouveau.
