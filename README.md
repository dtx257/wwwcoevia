# Site statique — Déploiement sur GitHub Pages et configuration OVH

Ce dépôt contient une page statique simple. Suivez les étapes ci-dessous pour l'héberger et pointer votre nom de domaine OVH.

## 1) Initialiser le dépôt local

```bash
git init
git add .
git commit -m "Initial commit: site statique"
```

## 2) Créer le dépôt distant (GitHub)

- Option recommandée (avec `gh`):

```bash
gh repo create <votre-utilisateur>/<nom-repo> --public --source=. --push
```

- Ou créez le repo sur GitHub via l'interface web, puis ajoutez le remote et poussez :

```bash
git remote add origin https://github.com/<votre-utilisateur>/<nom-repo>.git
ngit push -u origin main
```

Remplacez `<votre-utilisateur>` et `<nom-repo>`.

## 3) Activer GitHub Pages

- Pour un site de projet : activez GitHub Pages sur la branche `gh-pages` ou `main` (root).
- Pour un site utilisateur (ex: `votre-utilisateur.github.io`) nommez le repo `votre-utilisateur.github.io`.

Si vous utilisez un domaine personnalisé, créez un fichier `CNAME` à la racine contenant uniquement votre domaine (`exemple.com`).

## 4) Configurer OVH (DNS)

Pour pointer le domaine apex (`exemple.com`) vers GitHub Pages, ajoutez ces enregistrements A dans l'espace DNS OVH :

- A 185.199.108.153
- A 185.199.109.153
- A 185.199.110.153
- A 185.199.111.153

Puis pour `www.exemple.com`, ajoutez un enregistrement CNAME pointant vers `votre-utilisateur.github.io`.

Remplacez `exemple.com` et `votre-utilisateur.github.io` par vos valeurs.

Après mise à jour DNS, retournez dans les paramètres GitHub Pages et ajoutez votre domaine personnalisé (exemple.com). GitHub émettra automatiquement un certificat HTTPS si DNS est correctement configuré.

## 5) Vérification

- Vérifiez la propagation DNS : `dig +short exemple.com` ou `nslookup exemple.com`.
- Testez l'URL dans un navigateur et activez HTTPS dans GitHub Pages si nécessaire.

---

Besoin que j'initialise le dépôt Git local et fasse le premier commit pour vous ? Ou préférez-vous que je crée aussi le dépôt GitHub si vous avez `gh` configuré ?
