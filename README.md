# Mon Blog — Hugo + Decap CMS

Site statique construit avec [Hugo](https://gohugo.io) (thème
[PaperMod](https://github.com/adityatelange/hugo-PaperMod)) et une interface
d'écriture [Decap CMS](https://decapcms.org), pensé pour être publié
gratuitement sur [Netlify](https://netlify.com).

## Structure du contenu

```
content/
  musique/              → catégorie "Musique"
    concerts/            → sous-catégorie
    vinyles/              → sous-catégorie
  culture/              → catégorie "Culture"
    theatre/              → sous-catégorie
    voyages/               → sous-catégorie
```

Chaque catégorie et sous-catégorie apparaît dans le menu de navigation en
haut du site (menu déroulant pour les catégories qui ont des
sous-catégories).

Des articles d'exemple sont déjà présents dans chaque sous-catégorie — à
modifier ou supprimer librement une fois que la structure est comprise.

## Guides

1. [`guides/1-publier-avec-netlify.md`](guides/1-publier-avec-netlify.md) —
   mettre le blog en ligne gratuitement
2. [`guides/2-creer-un-article.md`](guides/2-creer-un-article.md) — écrire
   et publier un nouvel article
3. [`guides/3-creer-nouvelle-categorie.md`](guides/3-creer-nouvelle-categorie.md)
   — ajouter un nouvel onglet (catégorie ou sous-catégorie)

## Prévisualiser en local (optionnel)

Nécessite d'installer Hugo (version "extended") :
https://gohugo.io/installation/windows/

```powershell
cd C:\Users\lefil\Documents\Python\2026\Blog
hugo server -D
```

Le site est alors visible sur `http://localhost:1313`.
