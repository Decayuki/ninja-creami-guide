# Le Guide Ninja Creami — mini-app

Application web autonome (un seul fichier `index.html`, aucune dépendance, aucun serveur requis) qui regroupe un guide complet + un livre de recettes Ninja Creami **éditable** avec calcul nutritionnel automatique.

## Lancer l'app

Ouvre simplement `index.html` dans un navigateur (double-clic). Tout est local. Les images sont dans `images/`.

> Astuce : pour un rendu optimal des polices Google, une connexion internet aide, mais l'app fonctionne hors-ligne (police système en repli).

## Fonctionnalités

### Navigation
8 onglets : Accueil · La base · **Recettes** · Réglages · Astuces · Erreurs · Nettoyage · Achats · 🇫🇷 Équivalents.

### Recettes (le cœur)
- **27 recettes** catégorisées (sportive, post-workout, healthy, basses cal, kids, sorbet, vegan, gourmand, café, petit-déj), issues de 4 vidéos + recherche web.
- **Pills multi-catégories** (cumulables) + **tri** (protéines/100 g, calories ↑/↓, A→Z) + **recherche** (nom ou ingrédient).
- **Sélecteur de portion global** : 100 g / 50 g / 25 g / portion entière / libre → recalcule les macros de toutes les cartes en direct.

### Modale recette (clic sur une carte)
- **Deux onglets** : 🇫🇷 **Version France** (par défaut) et 🇺🇸 Recette originale. La version FR substitue les marques US par leurs équivalents (Spéculoos ↔ Graham cracker, etc.).
- Nutrition affichée pour le **pot entier** ET **pour 100 g**, recalculée depuis les ingrédients.
- Préparation, réglage machine, source.

### CRUD complet
- **Éditer** une recette : nom, catégories, temps, image, réglage, ingrédients (quantité + macros/100 g), mix-ins, étapes.
- **Créer** sa propre recette (bouton « + Créer une recette »).
- **Supprimer** une recette.
- **Réinitialiser** aux 27 recettes d'origine (bouton ↺).
- Toute modification **recalcule les valeurs nutritionnelles en temps réel**.

### Autocomplete intelligent
- Saisie d'ingrédient → suggestions depuis la **bibliothèque d'ingrédients** (~55 entrées) ; le choix **pré-remplit les macros/100 g** automatiquement.
- **Moteur de suggestion de préparation** (« cross-thinking ») : selon les ingrédients ajoutés, l'app déduit le **réglage machine** et les **étapes** adaptés :
  - fruits seuls → *Sorbet ×2*
  - protéine en poudre → *Lite Ice Cream + Re-spin*
  - crème / lait entier → *Ice Cream + Re-spin*
  - base épaisse (cottage/yaourt) → ajoute une étape « mixer jusqu'à lisse »
  - mix-ins présents → ajoute *+ Mix-In* et l'étape correspondante
  - Bouton « Appliquer cette préparation ».

### Persistance
Les recettes (créées / modifiées / supprimées) sont sauvegardées dans le **localStorage** du navigateur (clé `creami_v2`). « Réinit. » efface et restaure les défauts.

## Architecture technique

`index.html` — un seul fichier (HTML + CSS + JS vanilla).

### Modèle de données
- **`ING`** : bibliothèque d'ingrédients. Chaque entrée = `{ n (nom US), fr (équivalent FR), u (unité g/ml), cat (catégorie), p:{k,p,c,l} (macros pour 100 g/ml) }`.
- **`SEED`** : 27 recettes de référence, ingrédients exprimés en `{ k: cléING, g: grammes }`.
- À l'init, `expand()` transforme chaque recette en ingrédients « inline » : `{ name, fr, u, cat, g, p:{k,p,c,l} }`. Les macros sont ainsi **portées par chaque ingrédient** → le recalcul ne dépend d'aucune table externe et survit à l'édition.
- **`compute(r)`** : `total = Σ (g/100 × p)` sur ingrédients + mix-ins ; `weight = Σ g`.

### Pour ajouter un ingrédient à la bibliothèque
Ajoute une entrée dans l'objet `ING` (avec ses macros/100 g, son équivalent FR et sa catégorie). Il apparaîtra automatiquement dans l'autocomplete.

### Catégories de préparation (moteur de suggestion)
La logique est dans `suggestPrep(ing, mix)` — modifie/étends les règles `if` pour affiner les déductions.

## Limites connues
- Les **valeurs nutritionnelles sont des estimations** calculées depuis des macros/100 g moyennes — à affiner selon tes marques exactes (chaque ingrédient est éditable).
- Les quantités sont gérées en **grammes/ml** (pas en « cuillères ») pour permettre le recalcul exact.
- Certaines images sont réutilisées entre recettes au parfum visuellement proche.

## Sources
- Vidéos YouTube : Exercise4CheatMeals, Tried Tested and True, Joey Suggs.
- Recettes web : Lifestyle of a Foodie, The Flexible Dieting Lifestyle, Lauren Fit Foodie, Mary's Whole Life, Fit Foodie Finds, Winding Creek Ranch, Food Banjo, Recipes From A Pantry, Kroll's Korner, Feasting on Fruit, The Tasty Travelers, I Dream of Ice Cream, Patii's Page, Lara Clevenger, Cooked & Loved.
- Images générées avec NanoBanana (Gemini), direction artistique cohérente.
