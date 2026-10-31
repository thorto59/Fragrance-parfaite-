# Site CHOGAN Lille – guide pas à pas

Ce dossier est un site complet : aucune installation, aucune base de données, aucun paiement.

## 1. Créer ta clé Web3Forms (gratuit)
1. Va sur **web3forms.com** et clique sur « Create your Access Key ».
2. Saisis l'adresse e-mail où tu veux recevoir les demandes. Cette adresse reste chez Web3Forms : elle n'apparaît nulle part dans le site.
3. Tu reçois par e-mail une **clé d'accès** (une suite de lettres et de chiffres). Garde-la.

## 2. La coller dans le site
1. Ouvre le fichier `js/config.js` avec le Bloc-notes (ou TextEdit).
2. Remplace `VOTRE_CLE_WEB3FORMS` par ta clé, en gardant les guillemets.
3. Enregistre.

## 3. Mettre en ligne gratuitement sur Netlify
1. Crée un compte gratuit sur **netlify.com**.
2. Va dans « Sites », puis « Add new site » > « Deploy manually ».
3. **Glisse-dépose le dossier entier** du site dans la zone indiquée.
4. Netlify te donne une adresse en `.netlify.app`. Tu peux la renommer dans les réglages.

## 4. Tester avec 2 fausses demandes
1. Ouvre le site, ajoute 2 ou 3 produits, va dans « Ma demande ».
2. Test A : retrait en main propre, avec e-mail seulement. Test B : livraison, avec adresse et téléphone seulement.
3. Vérifie que tu reçois les 2 e-mails et que la page « Merci » s'affiche.
4. Si le message « clé manquante » apparaît, retourne à l'étape 2 et re-déploie le dossier.

## 5. Modifier un prix ou ajouter un produit
Tout est dans `data/catalogue.json`. Ouvre-le avec un éditeur de texte.
- **Changer un prix** : trouve le produit (Ctrl+F sur son nom), modifie le nombre après `"prix":`. Utilise un point pour les décimales (15.9).
- **Ajouter un produit** : copie un bloc complet `{ ... }` d'un produit similaire (avec la virgule entre les blocs), change `id` (unique), `nom`, `reference`, `formats`. Les mots `famille`, `categorie` (Femme / Homme / Mixte) servent aux filtres.
- **Gel douche ou crème** : bloc `"gel_douche": {"ml": 250, "prix": 15.9}` ; supprime-le s'il n'existe pas.
- Après chaque changement, re-glisse le dossier dans Netlify. Un seul oubli de virgule casse le fichier : vérifie-le sur jsonlint.com.

## Ajouter ou changer une photo
Dépose l'image (de préférence en .webp ou .jpg, 500 px de large environ) dans `assets/p/`, puis, dans `data/catalogue.json`, mets son chemin dans le champ `"image"` du produit, par exemple `"image":"assets/p/076.webp"`.

## À compléter avant d'ouvrir au public
- `mentions.html` : les champs `[À COMPLÉTER]` (identité, SIRET, hébergeur, durée de conservation, contact RGPD).
- `TODO_A_VERIFIER.md` : données manquantes du catalogue (prix des huiles, enfant, etc.).
- Textes comparatifs et allégations santé du PDF : volontairement non repris, à valider avant publication.
