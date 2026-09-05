# Guide 3 — Créer une nouvelle catégorie ou sous-catégorie

Cette opération demande de modifier 2 à 3 fichiers texte. Pas besoin de
savoir coder : il s'agit surtout de copier-coller des blocs déjà présents en
changeant les noms.

Exemple utilisé ci-dessous : ajouter une nouvelle catégorie **"Cinéma"** avec
une sous-catégorie **"Sorties"**.

## Étape 1 — Créer les dossiers de contenu

Dans `content/`, créer :

```
content/cinema/_index.md
content/cinema/sorties/_index.md
```

Contenu de `content/cinema/_index.md` :

```markdown
---
title: "Cinéma"
---

Description de la catégorie.
```

Contenu de `content/cinema/sorties/_index.md` :

```markdown
---
title: "Sorties"
---

Description de la sous-catégorie.
```

## Étape 2 — Ajouter les entrées de menu dans `hugo.toml`

Ouvrir `hugo.toml`, et dans la section `[menu]`, ajouter (sur le modèle des
blocs "Musique" et "Culture" déjà présents) :

```toml
  [[menu.main]]
    identifier = "cinema"
    name = "Cinéma"
    url = "/cinema/"
    weight = 30

  [[menu.main]]
    identifier = "cinema-sorties"
    name = "Sorties"
    url = "/cinema/sorties/"
    parent = "cinema"
    weight = 31
```

Le `weight` détermine l'ordre d'affichage dans le menu (plus le chiffre est
petit, plus l'onglet apparaît à gauche). Pour ajouter une deuxième
sous-catégorie sous "Cinéma", dupliquer le second bloc en changeant
`identifier`, `name`, `url`, et en gardant `parent = "cinema"`.

## Étape 3 — Ajouter une collection dans Decap CMS

Ouvrir `static/admin/config.yml`, et ajouter un nouveau bloc de collection
(copier un bloc existant comme `musique-concerts` et l'adapter) :

```yaml
  - name: "cinema-sorties"
    label: "Cinéma / Sorties"
    folder: "content/cinema/sorties"
    create: true
    slug: "{{slug}}"
    fields:
      - { label: "Titre", name: "title", widget: "string" }
      - { label: "Date de publication", name: "date", widget: "datetime" }
      - label: "Catégories"
        name: "categories"
        widget: "list"
        default: ["Cinéma", "Sorties"]
      - { label: "Tags", name: "tags", widget: "list", required: false }
      - { label: "Description courte", name: "description", widget: "text", required: false }
      - { label: "Brouillon (non publié)", name: "draft", widget: "boolean", default: true }
      - { label: "Image de couverture", name: "cover", widget: "image", required: false }
      - { label: "Contenu", name: "body", widget: "markdown" }
```

## Étape 4 — Publier les changements

```powershell
cd C:\Users\lefil\Documents\Python\2026\Blog
git add .
git commit -m "Ajout de la catégorie Cinéma"
git push
```

Netlify republie automatiquement le site avec le nouvel onglet dans la
navigation, et la nouvelle collection apparaît dans l'interface `/admin/`.

## Ajouter une catégorie SANS sous-catégorie

Si une catégorie n'a pas besoin d'être subdivisée, ne créer qu'un seul bloc
de menu (sans `parent`) et un seul dossier de contenu — elle s'affichera
comme un onglet simple, sans menu déroulant.
