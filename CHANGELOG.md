# Changelog — Le Guide Ninja Creami

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
