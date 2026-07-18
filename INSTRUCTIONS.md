# Déploiement du site sur GitHub Pages

## Contenu du pack

- `index.html` — le site (une page)
- `sitemap.xml` — plan du site pour Google
- `robots.txt` — autorise l'indexation et pointe vers le sitemap
- `CNAME` — indique à GitHub Pages ton domaine personnalisé

## Étape 1 — Créer le repo et déposer les fichiers

1. Va sur https://github.com/new
2. Nom du repo : `educatrice-vernon` (ou ce que tu veux), visibilité **Public**
3. Coche "Add a README" puis crée le repo
4. Dans le repo : **Add file → Upload files** → glisse les 4 fichiers
   (`index.html`, `sitemap.xml`, `robots.txt`, `CNAME`) → **Commit changes**

## Étape 2 — Activer GitHub Pages

1. Dans le repo : **Settings → Pages** (menu de gauche)
2. Source : **Deploy from a branch** → Branch : `main` / dossier `/ (root)` → **Save**
3. Attends 1-2 minutes : le site est en ligne sur `https://TONPSEUDO.github.io/educatrice-vernon/`

## Étape 3 — Brancher le domaine

1. Toujours dans **Settings → Pages** : champ **Custom domain** →
   saisis `educatrice-liberale-vernon27.fr` → **Save**
   (le fichier CNAME du repo fait déjà ce travail, mais vérifie que le champ est bien rempli)

2. Chez ton registrar (là où tu as ajouté le TXT Google), dans la zone DNS
   du domaine, remplace l'enregistrement A actuel (qui pointe vers ton
   hébergeur WordPress) par les 4 enregistrements A de GitHub Pages :

   | Type | Nom | Cible |
   |------|-----|-------|
   | A | @ | 185.199.108.153 |
   | A | @ | 185.199.109.153 |
   | A | @ | 185.199.110.153 |
   | A | @ | 185.199.111.153 |

   Et pour le sous-domaine www (optionnel mais recommandé) :

   | Type | Nom | Cible |
   |------|-----|-------|
   | CNAME | www | TONPSEUDO.github.io. |

   ⚠️ Ne touche PAS à l'enregistrement TXT `google-site-verification` — il
   sert à garder ta validation Search Console.
   ⚠️ Ne touche PAS aux enregistrements MX s'il y en a (e-mails).

3. Retourne dans **Settings → Pages** : après propagation DNS (de quelques
   minutes à 24h), coche **Enforce HTTPS** dès que la case devient cliquable.

## Étape 4 — Côté Google

1. Search Console → **Sitemaps** → saisir `sitemap.xml` → Envoyer
2. Search Console → **Inspection d'URL** → `https://educatrice-liberale-vernon27.fr/`
   → **Demander une indexation** (pour que Google recharge la nouvelle version)

## Remarques

- L'ancien WordPress reste accessible chez ton hébergeur tant que tu ne
  résilies pas, mais il ne sera plus servi sur le domaine. Garde-le quelques
  semaines le temps de vérifier que tout va bien, puis tu pourras résilier.
- Pour modifier le site plus tard : édite `index.html` directement sur
  GitHub (icône crayon) → Commit → le site se met à jour en ~1 minute.
