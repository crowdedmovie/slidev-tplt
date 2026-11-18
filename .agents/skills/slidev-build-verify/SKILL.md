---
name: slidev-build-verify
description: "Réaliser une présentation dans ce template Slidev à partir du plan et de sa direction visuelle, rédiger les notes d’oral et vérifier le build et le rendu avec Playwright."
disable-model-invocation: true
---

# Création et vérification d’une présentation Slidev

## Réaliser le plan

Lis `presentation-plan.md` ou le plan équivalent fourni, ainsi que `presentation-brief.md` s’il existe. Vérifie que le plan concerne la présentation demandée et reprend le bon déroulé, les sources, les visuels et la direction graphique. Demande une précision si une décision manquante bloque la réalisation. Si l’utilisateur a demandé une revue du plan avant la création, attends son accord.

Travaille dans le [fichier de slides](../../../slides.md) du projet, sauf si l’utilisateur indique une autre entrée Slidev. Reprends l’ordre, le message de chaque slide, les sources et la palette du plan. Utilise les exemples du catalogue et les conventions du [README](../../../README.md). Préserve les identifiants et valeurs `dragPos` des éléments existants, sauf si leur repositionnement est demandé. Signale les écarts au plan et les éléments manquants, sans inventer de données ou de sources.

## Écrire les notes d’oral

Ajoute les notes à la fin de chaque slide, dans un commentaire HTML, avant le séparateur de la slide suivante. Écris de courtes phrases ou propositions qu’on peut retrouver d’un coup d’œil en parlant. Chaque ligne doit porter une idée cohérente. Garde les chiffres à dire, les nuances utiles et les transitions. Évite le script rédigé mot à mot et les suites de mots-clés décousus. Utilise des flèches ou des symboles quand ils aident à lire un enchaînement.

```html
<!--
- Le seuil passe de 80 à 60.
- Moins de faux négatifs → plus de vérifications manuelles.
- Montrer le cas limite avant de passer aux résultats.
-->
```

## Vérifier et livrer

1. Exécute `npm ci` si les dépendances manquent, puis `npm run build`. Corrige les erreurs liées à la présentation et vérifie à nouveau après les corrections.
2. Lance Slidev avec `npm run dev` et ouvre l’adresse locale affichée avec `playwright-cli open <url>` si cette CLI est disponible, ou avec le Playwright déjà configuré dans l’environnement. Attends que la slide et ses visuels soient chargés avant de capturer son rendu. Utilise un viewport représentatif de la projection ou de la diffusion prévue.
3. Parcours chaque slide et inspecte les captures. Compare le rendu au plan et à la direction visuelle. Cherche les textes coupés, éléments hors du cadre, chevauchements involontaires, placements gênants, visuels manquants et défauts de lisibilité. Vérifie les modes clair et sombre prévus, les états utiles des révélations et les interactions importantes. Examine les erreurs de page ou de ressources dans la console et ouvre la vue présentateur pour vérifier les notes.
4. Corrige les problèmes constatés et contrôle de nouveau les slides et interactions touchées. Remets la présentation avec un bilan bref des vérifications et des écarts éventuels. Si Playwright ou son navigateur manque, indique précisément ce qui bloque et quels contrôles visuels ou interactifs restent à faire. Un build réussi valide la compilation, pas le rendu.
