# slidev-tplt

Base réutilisable pour créer des présentations [Slidev](https://sli.dev/). Le fichier `slides.md` est à la fois une présentation de démonstration et un point de départ à remplacer pour chaque sujet.

## Démarrage

Installer Node.js et npm, puis :

```sh
npm ci
npm run dev
```

Ouvrir l’adresse indiquée dans le terminal. `npm run build` produit le site statique dans `dist/`. `npm run export` lance l’export PDF : il nécessite les dépendances de navigateur de Slidev/Playwright ; installer `playwright-chromium` est nécessaire pour la commande CLI ; cet export reste à vérifier sur votre machine. Le mode présentateur est accessible par `/presenter/`, la vue d’ensemble par `/overview/`.

## Nouvelle présentation

1. Cloner le dépôt et installer les dépendances avec `npm ci`.
2. Appeler [`$slidev-brief-research`](.agents/skills/slidev-brief-research/SKILL.md) avec le sujet, le public, la durée et les documents disponibles. Confirmer le cadrage proposé pour que l’agent lance la recherche et produise `presentation-brief.md`.
3. Définir un plan et une direction visuelle adaptés, puis remplacer les exemples de `slides.md`. Le composant `components/CounterDemo.vue` est un exemple à adapter ou retirer.
4. Tester les clics, les interactions et la lisibilité en mode présentation, puis lancer le build et contrôler l’export souhaité.

## Palette de couleurs

Au début de `slides.md`, change `htmlAttrs.data-palette`. La touche **D** et le bouton soleil/lune de Slidev basculent entre les modes. Les couleurs sont définies dans `styles/index.css`.

| Valeur | Clair | Sombre |
| --- | --- | --- |
| `default` | Slidev clair | Slidev sombre |
| `catppuccin` | Latte | Mocha |
| `nord` | Snow Storm | Polar Night |
| `gruvbox` | Gruvbox Light | Gruvbox Dark |
| `rose-pine` | Dawn | Rosé Pine |
| `solarized` | Solarized Light | Solarized Dark |

## Catalogue de départ

Le catalogue comprend 23 slides : sommaire, révélations et transitions, Motion, objets déplaçables, Mermaid, flèches, annotations, images, tableaux, formules, code, Monaco, composant Vue, layouts et notes. Utiliser le sommaire ou la vue d’ensemble pour accéder aux exemples. Le style est provisoire.

La compilation ne garantit pas les interactions ni le rendu visuel. Les View Transitions sont expérimentales et dépendent du navigateur ; le Runner Monaco prend en charge JavaScript et TypeScript par défaut.

Pour les autres possibilités et leurs restrictions, voir la [documentation Slidev](https://sli.dev/features/) ; [Monaco Runner](https://sli.dev/features/monaco-run) exécute JavaScript et TypeScript par défaut. Les View Transitions dépendent du navigateur. Le build peut être volumineux avec Monaco et Mermaid.

## Positionnement

En mode développement, double-cliquer un objet déplaçable pour le déplacer, le redimensionner ou le tourner. Les coordonnées sont stockées dans le frontmatter `dragPos` sous la forme `gauche,haut,largeur,hauteur,rotation`. Conserver ces valeurs et leurs identifiants lors des modifications sans rapport avec la position. Préférer le frontmatter aux coordonnées intégrées à la directive : [Slidev signale des limites de mise à jour de ces dernières](https://sli.dev/features/draggable.html). Garder les titres et paragraphes dans le flux normal ; encapsuler un diagramme complet dans un conteneur lorsque son déplacement global est utile.

À vérifier manuellement : déplacer et redimensionner la carte et le diagramme, constater l’écriture de `dragPos`, recharger la page et vérifier la persistance ; contrôler aussi les interactions de tout composant placé dans un conteneur déplaçable. Les ajustements écrivent dans les sources : relire le diff avant commit.

## Dépendances

Le lockfile testé installe Slidev 52.20.1 et le thème default 0.25.0. `npm ci` a signalé 44 vulnérabilités dans l’ensemble des dépendances de développement ; `npm audit --omit=dev` n’en signale aucune. Examiner `npm audit` avant mise à jour ; ne pas appliquer aveuglément de correction majeure.

## État du projet

Le travail commence par un catalogue technique de fonctionnalités, puis une exploration visuelle avec le mainteneur. Le thème par défaut actuel est provisoire : le nombre de thèmes, leurs couleurs, formes et typographies restent à définir. Voir [BACKLOG.md](BACKLOG.md) pour les travaux restants. Les exemples du fichier `slides.md` constituent pour l’instant le catalogue ; une carte distincte pourra être ajoutée si sa taille le justifie.

Le dépôt est destiné à être cloné, sans publication de paquet ni procédure de release définie à ce stade. Les builds sont locaux ; aucune mise en ligne ou CI n’est configurée. Les conventions de branches, de vérification et de livraison figurent dans [AGENTS.md](AGENTS.md).

## Ajouter une image

Placer une capture, par exemple `capture.png`, dans `public/images/` puis la référencer dans une slide : `![Description](/images/capture.png)`. La slide 16 montre une image locale et sa légende dans un même conteneur `<v-drag>` : remplacer le chemin de l’image et adapter son texte alternatif. La position du groupe est enregistrée dans `dragPos`. Le collage direct du presse-papiers dans une slide n’a pas été vérifié ; l’ajout d’un fichier et de sa référence est le parcours documenté.
