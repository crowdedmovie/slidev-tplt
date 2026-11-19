---
name: slidev-build-verify
description: "Implémenter un plan Slidev, rédiger les notes d’oral et vérifier la compilation, le rendu et les interactions."
disable-model-invocation: true
---

# Réalisation et vérification d’une présentation Slidev

## Implémenter le plan

Lis `presentation-plan.md` ou son équivalent, ainsi que `presentation-brief.md` s’il existe. Vérifie le sujet et applique l’ordre, le contenu, les choix visuels, les séquences de clics et les transitions du plan. Si l’utilisateur a demandé une validation intermédiaire, attends son accord avant de construire.

Travaille dans [`slides.md`](../../../slides.md) ou dans l’entrée indiquée par l’utilisateur. Consulte le code des exemples prévus dans le [catalogue](../../../catalogue.md) et les conventions du [README](../../../README.md). Préserve les identifiants et valeurs `dragPos` existants quand la position de l’élément reste hors du changement demandé.

Ajuste les détails de réalisation pour la lisibilité et la fiabilité. Si une limite technique impose un écart sur un effet prévu ou sur le déroulé, explique l’impact et soumets une solution de remplacement si elle change sensiblement l’oral ou le rendu. Signale toute donnée manquante dont dépend la présentation.

Pour les cartes et encadrés, utilise un fond uni ou une bordure neutre régulière. N’ajoute ni liseré, ni bande, ni bordure d’accent décorative sur un seul côté, quelle que soit sa couleur ou sa technique de réalisation.

Conserve le bloc `fonts` du frontmatter quand tu remplaces les slides de démonstration. Les titres utilisent Barlow via la feuille de style du template. Le texte courant et les chiffres utilisent IBM Plex Sans via `fonts.sans`, sauf choix différent demandé par l’utilisateur. Lors du contrôle dans Playwright, vérifie que les polices prévues ont effectivement chargé.

## Écrire les notes d’oral

Ajoute les notes à la fin de chaque slide, dans un commentaire HTML avant le séparateur suivant. Écris des repères de prise de parole en fragments courts et reliés. Garde l’idée à transmettre, les chiffres utiles, les nuances et le lien avec la suite. Chaque ligne doit permettre à l’orateur de reformuler naturellement. Évite les phrases prêtes à lire et les mots-clés isolés. Utilise des flèches ou des symboles pour rendre les liens explicites et place les repères de temps et de clic là où ils servent.

```html
<!--
- Seuil : 80 → 60
- Moins de cas manqués → plus de vérifications manuelles
- [click] Cas limite → transition vers les résultats
-->
```

## Vérifier et livrer

1. Exécute `npm ci` si les dépendances manquent, puis `npm run build`. Corrige les erreurs liées à la présentation.
2. Lance Slidev avec `npm run dev` et ouvre l’adresse locale affichée avec `playwright-cli open <url>` ou avec le Playwright configuré dans l’environnement. Attends le chargement des visuels et des polices. Utilise un viewport représentatif de la projection ou de la diffusion.
3. Parcours et inspecte chaque slide. Compare le rendu au plan, y compris les thèmes ou modes de rendu prévus. Cherche les textes coupés, les chevauchements, les éléments hors cadre, les visuels manquants et les problèmes de lisibilité. Vérifie l’absence de liseré décoratif sur les cartes et encadrés. Contrôle la console. En vue présentateur, vérifie que les notes se parcourent d’un coup d’œil et permettent de reformuler sans lire un texte préparé.
4. Pour les slides interactives, vérifie l’état initial, l’ordre des clics, les effets simultanés, le placement des annotations et le retour en arrière selon le plan. Vérifie les transitions et autres interactions prévues, dont la persistance du placement après rechargement quand un objet doit pouvoir être ajusté.
5. Corrige les problèmes observés et vérifie à nouveau les éléments touchés. Remets la présentation avec un bilan distinct de la compilation, du rendu et des interactions, et indique les écarts au plan. Si l’environnement bloque un contrôle, précise le blocage et ce qui reste à vérifier.
