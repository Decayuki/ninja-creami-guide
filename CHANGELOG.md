# Changelog — Le Guide Ninja Creami

## v4 — Perf, courses & PWA (2026-06-21)
Suite à la revue de l'app, 6 lots livrés (dev → quality → doc) :
- **Performance** : images PNG → **WebP** (9 Mo → ~0,8 Mo, -91 %), `loading="lazy"`, `fetchpriority` sur le hero.
- **Recherche & filtres** : recherche **insensible aux accents**, filtres rapides (★ Favoris, 🍦 Mes recettes, 💪 Protéiné, 🪶 Léger), **favoris** persistés.
- **Liste de courses** : onglet 🛒 Courses — sélection multi-recettes → agrégation des ingrédients (FR) par rayon, copier/décocher.
- **PWA** : manifest + service worker (installable, hors-ligne), icônes 192/512 + apple-touch-icon.
- **Partage** : `og:image` + `twitter:card`.
- **Accessibilité** : `role="dialog"`/`aria-modal`, focus-trap + restauration du focus, autocomplete navigable au clavier (↑/↓/Entrée/Échap), `aria-label` sur les icônes.
- **Sécurité** : échappement HTML des contenus dynamiques (protège l'import JSON).

## v3.1 — Outils & déploiement (2026-06-21)
- **Objectif nutritionnel inverse** : « je veux X g de protéines / kcal / glucides / lipides → quelle portion ? » directement dans la modale.
- **Export / Import JSON** des recettes (sauvegarde et partage).
- **Responsive design** complet (breakpoints 780 px et 480 px, hero/modale/édition adaptés mobile).
- Favicon + métadonnées Open Graph.
- **Déploiement Vercel** : https://ninja-creami-app.vercel.app · dépôt GitHub Decayuki/ninja-creami-guide.

## v3 — Mini-app éditable (2026-06-21)
Passage en vraie mini-app.
- **Modale recette** au clic, avec **deux onglets** : 🇫🇷 Version France (par défaut) / 🇺🇸 Recette originale.
- **CRUD complet** : éditer / créer / supprimer une recette, + réinitialisation aux défauts.
- **Recalcul nutritionnel en temps réel** : restructuration des recettes en ingrédients quantifiés portant leurs macros/100 g ; modifier une quantité ou un ingrédient recalcule tout.
- **Autocomplete intelligent** d'ingrédients (bibliothèque ~55 entrées, pré-remplit les macros).
- **Moteur de suggestion de préparation** : déduit réglage machine + étapes selon les ingrédients (sorbet / protéiné / crémeux / mix-ins…), avec bouton « Appliquer ».
- **Persistance localStorage** (clé `creami_v2`).
- Fix CSS flexbox : champ ingrédient écrasé par la spécificité de `input[type=number]` → bases flex explicites.
- Doc : README + CHANGELOG.

## v2 — Catalogue enrichi (2026-06-20)
- 27 recettes catégorisées (21 ajoutées via recherche web).
- Système de **pills** multi-catégories + **tri** + **recherche**.
- **Sélecteur de portion** (100/50/25 g, portion entière, libre) recalculant les macros des cartes.
- Onglet **🇫🇷 Équivalents** (tables produits US → FR).
- 9 visuels supplémentaires (NanoBanana), DA cohérente.

## v1 — Guide initial (2026-06-20)
- App à onglets : Accueil, Base, Recettes (6), Réglages, Astuces, Erreurs, Nettoyage, Achats.
- 8 images générées, design éditorial crème/rose.
- Issu de l'analyse de 4 vidéos YouTube.
