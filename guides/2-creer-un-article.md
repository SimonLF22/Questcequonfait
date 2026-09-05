# Guide 2 — Créer un nouvel article

## Via l'interface Decap CMS (recommandé, sans code)

1. Aller sur `https://VOTRE-SITE.netlify.app/admin/` et se connecter
2. Dans le menu de gauche, choisir la collection correspondant à la
   sous-catégorie voulue, par exemple **Musique / Concerts**
3. Cliquer **New Musique / Concerts** (ou équivalent selon la collection)
4. Remplir les champs :
   - **Titre**
   - **Date de publication**
   - **Catégories** : déjà pré-rempli avec la bonne catégorie/sous-catégorie
   - **Tags** (facultatif)
   - **Description courte** (facultatif, utile pour le référencement)
   - **Brouillon** : cocher pour ne pas publier tout de suite, décocher pour
     publier
   - **Image de couverture** (facultatif) : vous pouvez glisser-déposer une
     image, elle sera automatiquement rangée dans le dossier
     `static/images/uploads`
   - **Contenu** : l'éditeur Markdown avec mise en forme (gras, titres,
     liens, images...) sans avoir besoin de connaître la syntaxe
5. Cliquer **Publish** (ou **Save** pour un brouillon)

Netlify reconstruit alors automatiquement le site (comptez 30 secondes à
2 minutes selon la taille du site) et l'article apparaît en ligne.

## Via Markdown directement (optionnel, si vous préférez du texte brut)

Créer un fichier dans le dossier de la sous-catégorie voulue, par exemple :

```
content/musique/concerts/nom-de-mon-article.md
```

Avec ce contenu :

```markdown
---
title: "Titre de mon article"
date: 2026-09-05
categories: ["Musique", "Concerts"]
tags: []
description: ""
draft: false
---

Le texte de l'article ici, en Markdown.
```

Puis :

```powershell
git add .
git commit -m "Nouvel article"
git push
```

Netlify republie automatiquement après le `push`.

## Astuce

Le champ `draft: true` permet de préparer un article sans le publier tout de
suite — il n'apparaîtra pas sur le site tant qu'il est à `true`, que ce soit
via l'interface (case "Brouillon" cochée) ou en écriture directe.
