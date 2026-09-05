# Guide 1 — Publier le blog avec Netlify (gratuit)

Ce guide suppose que le dossier `Blog` est bien dans
`C:\Users\lefil\Documents\Python\2026\Blog`.

## Étape 1 — Installer Git (si pas déjà fait)

Télécharger et installer : https://git-scm.com/download/win

## Étape 2 — Créer un compte GitHub

Aller sur https://github.com et créer un compte gratuit si nécessaire.

## Étape 3 — Créer un dépôt (repository) GitHub

1. Sur GitHub, cliquer sur **New repository**
2. Nom : `blog` (ou ce que vous voulez)
3. Laisser en **Public** (nécessaire pour rester dans les usages gratuits sans
   configuration supplémentaire)
4. Ne cochez **aucune** case d'initialisation (pas de README, pas de
   `.gitignore`) — le projet en contient déjà un
5. Cliquer **Create repository**

## Étape 4 — Envoyer le projet sur GitHub

Ouvrir un terminal (PowerShell) dans le dossier du projet :

```powershell
cd C:\Users\lefil\Documents\Python\2026\Blog
git init
git add .
git commit -m "Premier commit du blog"
git branch -M main
git remote add origin https://github.com/VOTRE-PSEUDO/blog.git
git push -u origin main
```

Remplacer `VOTRE-PSEUDO` par votre nom d'utilisateur GitHub.

> Le dossier `themes/PaperMod` est fourni tel quel dans le projet (le thème
> visuel du site). Il partira avec le reste lors du `git push`.

## Étape 5 — Créer un compte Netlify

Aller sur https://app.netlify.com et créer un compte gratuit (le plus simple
est de choisir "Sign up with GitHub" pour lier directement les deux comptes).

## Étape 6 — Connecter le dépôt à Netlify

1. Dans Netlify, cliquer **Add new site → Import an existing project**
2. Choisir **GitHub**, autoriser l'accès, puis sélectionner le dépôt `blog`
3. Netlify détecte automatiquement les réglages grâce au fichier
   `netlify.toml` déjà présent dans le projet (commande `hugo --gc --minify`,
   dossier de sortie `public`) — ne rien changer
4. Cliquer **Deploy site**

Après 1 à 2 minutes, le site est en ligne sur une adresse du type
`nom-aleatoire.netlify.app`. Vous pouvez la renommer dans
**Site settings → Change site name**.

## Étape 7 — Activer l'authentification (Netlify Identity + Git Gateway)

C'est ce qui permet à Decap CMS de fonctionner sans écrire de code.

1. Dans le tableau de bord du site sur Netlify, aller dans **Site
   configuration → Identity**
2. Cliquer **Enable Identity**
3. Descendre à **Registration** → choisir **Invite only** (pour être seul à
   pouvoir vous connecter à l'admin)
4. Descendre à **Git Gateway** → cliquer **Enable Git Gateway**
   (aucune configuration à saisir, Netlify fait le lien avec GitHub tout seul)

## Étape 8 — Vous inviter vous-même comme éditeur

1. Toujours dans **Identity**, cliquer **Invite users**
2. Entrer votre propre adresse email
3. Vous recevrez un email "You've been invited" → cliquer le lien,
   définir un mot de passe

## Étape 9 — Se connecter à l'interface d'écriture

Aller sur `https://VOTRE-SITE.netlify.app/admin/`, se connecter avec l'email
et le mot de passe définis à l'étape précédente.

Vous arrivez sur l'interface Decap CMS avec vos collections
(Musique/Concerts, Musique/Vinyles, Culture/Théâtre, Culture/Voyages, Pages).

## Contraintes du plan gratuit à connaître

- **300 minutes de build/mois** : chaque publication relance une
  construction du site (quelques secondes à quelques dizaines de secondes
  pour un blog de cette taille) — largement suffisant pour un usage normal
- **100 Go de bande passante/mois** — suffisant sauf trafic très important
- **1 seul build à la fois** : si vous publiez deux articles à quelques
  secondes d'écart, le second attend que le premier se termine
- Le dépôt GitHub doit rester **public** pour éviter toute configuration
  supplémentaire (les identifiants de connexion admin, eux, restent privés
  et gérés par Netlify Identity)

## Nom de domaine personnel (optionnel, plus tard)

Le sous-domaine `.netlify.app` est gratuit à vie. Si vous achetez un nom de
domaine plus tard, vous pourrez le brancher gratuitement dans **Domain
settings** de Netlify (le HTTPS est généré automatiquement, sans frais).
