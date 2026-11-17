---
name: slidev-presentation
description: Concevoir ou modifier une présentation dans ce template Slidev, du plan au design et à l’implémentation. Ne pas utiliser pour une présentation dans un autre outil.
---

# Créer une présentation Slidev

Lire le README, AGENTS.md et les exemples existants. Identifier le public, l’objectif, la durée et les contraintes ; demander les informations essentielles manquantes. Proposer ou adapter le plan, puis définir une direction visuelle cohérente (couleurs, typographie, contraste) selon le sujet. Utiliser le niveau de collaboration demandé : ne pas imposer une validation intermédiaire si l’utilisateur a demandé une réalisation autonome.

Implémenter les slides dans `slides.md` avec des notes utiles. Choisir les fonctionnalités pour leur valeur pédagogique : révélations pour séquencer, diagrammes pour les relations, code ou composants interactifs pour les démonstrations. Garder les structures en flux et rendre déplaçables seulement les objets indépendants. Préserver les valeurs `dragPos` existantes lors des changements sans rapport avec leur position. Consulter la documentation officielle pour les syntaxes non démontrées et les limites de la version installée.

Lancer `npm ci` si nécessaire et `npm run build`. Vérifier les interactions dans le navigateur si possible ; distinguer compilation et validation interactive dans le compte rendu. Signaler les limites et instructions de test restantes.
