---
name: slidev-plan-design
description: "Concevoir le déroulé, la direction visuelle et les interactions d’une présentation Slidev à partir d’un brief."
disable-model-invocation: true
---

# Plan et direction visuelle d’une présentation Slidev

## 1. Reprendre le cadrage et étudier le catalogue

- Utilise le `presentation-brief.md` du projet ou les éléments équivalents fournis. Vérifie le sujet, l’objectif, le niveau du public, la durée de l’exposé, la place des questions et les contraintes de diffusion. Demande seulement les précisions qui changeraient le déroulé ou le rendu. Si une preuve essentielle manque, indique quoi vérifier et avance sur le reste.
- Lis le code du [catalogue Slidev](../../../catalogue.md) et les indications du [README](../../../README.md). Repère les dispositions, les styles et les fonctionnalités qui servent le sujet. Pour les exemples retenus, examine leur syntaxe, leur déclenchement et leur rendu. Ouvre le catalogue si l’effet ou sa lisibilité mérite d’être vu.
- Adapte la direction visuelle au sujet, au public et aux conditions de présentation. Choisis la palette, la hiérarchie, les dispositions et les modes de rendu utiles. Dans le plan, prévois Barlow pour les titres et IBM Plex Sans pour le texte courant et les chiffres, sauf demande explicite de l’utilisateur. Appuie-toi sur les exemples du catalogue pour rendre ces choix concrets et indique les adaptations nécessaires.
- Pour les cartes et encadrés, prévois un fond uni ou une bordure neutre régulière. N’utilise aucun liseré, bande ou bordure d’accent décorative sur un seul côté, quelle que soit sa couleur.

## 2. Concevoir la mise en scène et le rythme

Organise le déroulé autour du message à retenir. Choisis le nombre de slides et répartis le temps en comptant les étapes à l’écran, les démonstrations et les questions prévues. Pour chaque slide, consigne les éléments suivants.

- Le titre provisoire, le rôle dans le déroulé, le message principal, le temps prévu et les preuves ou exemples avec leurs sources.
- La composition visuelle et les ressources à réutiliser, créer, obtenir ou vérifier. Précise ce qui reste à l’oral ou passe en annexe si cela aide à tenir la durée.
- Ce qui est visible à l’arrivée. Pour une slide interactive, indique dans l’ordre l’action et le résultat de chaque clic, les effets qui se déclenchent ensemble et les éléments qui restent visibles ou disparaissent. Associe chaque effet à un moment de l’oral et nomme le mécanisme Slidev envisagé. Par exemple, le dernier élément d’une comparaison apparaît avec `v-click` et une annotation `v-mark` regroupe au même clic les éléments que le public vient de découvrir.
- La règle de transition entre les slides et les exceptions utiles. Définis une transition par défaut si elle suffit à la plupart des enchaînements.

Dose les interactions selon le public, le temps disponible et le rôle de la slide. Une slide statique convient si le public doit lire des données à son rythme. Si un mode de diffusion repose sur un rendu statique, précise l’état qui doit y être lisible.

## 3. Livrer le plan

Écris `presentation-plan.md` à la racine du clone, sauf si l’utilisateur demande une autre destination ou une réponse dans le chat. Rassemble le déroulé numéroté, le budget de temps, la direction visuelle et les décisions ou ressources encore ouvertes. Vérifie que le total tient dans la durée, que les affirmations importantes renvoient à des sources et que les séquences d’affichage sont assez précises pour être implémentées.

Si seul le plan est demandé, remets-le pour relecture et arrête-toi sans modifier `slides.md`. Pour une demande de présentation complète, transmets-le à l’étape de réalisation. Attends l’accord de l’utilisateur s’il a demandé une revue intermédiaire.
