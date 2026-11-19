# slidev-tplt

Base réutilisable pour créer des présentations [Slidev](https://sli.dev/). Le fichier `slides.md` est l’entrée du diaporama. Il affiche le [catalogue d’exemples](catalogue.md) au départ et peut être remplacé pour chaque sujet.

## Démarrage

Installer Node.js et npm, puis :

```sh
npm ci
npm run dev
```

Ouvrir l’adresse indiquée dans le terminal. `npm run build` produit le site statique dans `dist/`. `npm run export` lance l’export PDF : il nécessite les dépendances de navigateur de Slidev/Playwright ; installer `playwright-chromium` est nécessaire pour la commande CLI ; cet export reste à vérifier sur votre machine. Le mode présentateur est accessible par `/presenter/`, la vue d’ensemble par `/overview/`.

## Nouvelle présentation

1. Cloner le dépôt et installer les dépendances avec `npm ci`.
2. Appeler [`$slidev-brief-research`](.agents/skills/slidev-brief-research/SKILL.md) avec le sujet, le public, la durée et les documents disponibles. Répondre aux questions de cadrage avant que l’agent lance la recherche et produise `presentation-brief.md`.
3. Appeler [`$slidev-plan-design`](.agents/skills/slidev-plan-design/SKILL.md) avec le brief pour préparer le déroulé, le rendu, les séquences de clics et les transitions dans `presentation-plan.md`.
4. Appeler [`$slidev-build-verify`](.agents/skills/slidev-build-verify/SKILL.md) avec le plan pour réaliser les slides, rédiger les notes d’oral et vérifier la compilation, le rendu et les interactions.

## Palette de couleurs

Pour changer de palette, règle `htmlAttrs.data-palette` dans le frontmatter initial du fichier ouvert dans Slidev. Pour une présentation en cours, il s’agit par défaut de `slides.md`. La touche **D** et le bouton soleil/lune de Slidev basculent entre les modes. Les couleurs sont définies dans `styles/index.css`.

| Valeur | Clair | Sombre |
| --- | --- | --- |
| `default` | Slidev clair | Slidev sombre |
| `catppuccin` | Latte | Mocha |
| `nord` | Snow Storm | Polar Night |
| `gruvbox` | Gruvbox Light | Gruvbox Dark |
| `rose-pine` | Dawn | Rosé Pine |
| `solarized` | Solarized Light | Solarized Dark |

## Typographie

Le template utilise [Barlow](https://tribby.com/fonts/barlow/) pour les titres et [IBM Plex Sans](https://www.ibm.com/design/language/typography/typeface/) pour le texte et les chiffres. Conserve le bloc `fonts` en tête de `slides.md` lorsque tu remplaces les slides de démonstration. `fonts.sans` définit la police du texte et `fonts.custom` charge Barlow, appliquée aux titres dans `styles/index.css`. Slidev charge ces polices depuis Google Fonts.

## Catalogue de départ

Les 23 exemples restent disponibles dans [`catalogue.md`](catalogue.md) après le remplacement de `slides.md`. Lance `npm run dev -- catalogue.md` depuis la racine pour les consulter. Le sommaire et la vue d’ensemble donnent accès aux exemples de révélations, transitions, annotations, objets déplaçables, diagrammes, code et autres fonctionnalités. Le style sert de point de départ.

La compilation ne garantit pas les interactions ni le rendu visuel. Les View Transitions sont expérimentales et dépendent du navigateur ; le Runner Monaco prend en charge JavaScript et TypeScript par défaut.

Pour les autres possibilités et leurs restrictions, voir la [documentation Slidev](https://sli.dev/features/) ; [Monaco Runner](https://sli.dev/features/monaco-run) exécute JavaScript et TypeScript par défaut. Les View Transitions dépendent du navigateur. Le build peut être volumineux avec Monaco et Mermaid.

## Icônes

Utilise les icônes avec parcimonie, par exemple pour distinguer deux catégories ou signaler un avertissement. Garde une seule famille pour les icônes comparables sur une même slide et un libellé visible si le sens est important. Évite les émojis sur les slides.

| Besoin | Source et intégration |
| --- | --- |
| Action, état ou concept courant | [Carbon](https://icon-sets.iconify.design/carbon/) par défaut, par exemple `<carbon-warning />`. |
| Concept ou objet mieux représenté | [Material Design Icons](https://icon-sets.iconify.design/mdi/) en complément de Carbon, par exemple `<mdi-account-circle />`. |
| Illustration ponctuelle d’une idée | [Unicons Monochrome](https://icon-sets.iconify.design/uim/), par exemple `<uim-rocket />`. |
| Produit, projet ou marque nommée | [SVG Logos](https://icon-sets.iconify.design/logos/), par exemple `<logos-vue />`. Si un fichier ou une variante officielle est requis, vérifie ses conditions d’usage et place le SVG officiel dans `public/images/`. |
| Symbole propre au sujet | Si les collections ne proposent rien d’assez clair, crée un SVG simple assorti aux autres icônes. Intègre-le dans la slide ou place-le dans `public/images/` s’il sert ailleurs. |

La slide [« Choisir une icône »](catalogue.md#choisir-une-icône) montre les quatre collections déjà installées et un SVG sur mesure. Les icônes redondantes avec un libellé portent `aria-hidden="true"`. Si un logo est affiché seul, donne-lui un nom accessible. Pour une autre collection, suis le [guide Slidev](https://sli.dev/features/icons) et ajoute son paquet Iconify si le besoin le justifie.

## Positionnement

En mode développement, double-cliquer un objet déplaçable pour le déplacer, le redimensionner ou le tourner. Les coordonnées sont stockées dans le frontmatter `dragPos` sous la forme `gauche,haut,largeur,hauteur,rotation`. Conserver ces valeurs et leurs identifiants lors des modifications sans rapport avec la position. Préférer le frontmatter aux coordonnées intégrées à la directive : [Slidev signale des limites de mise à jour de ces dernières](https://sli.dev/features/draggable.html). Garder les titres et paragraphes dans le flux normal ; encapsuler un diagramme complet dans un conteneur lorsque son déplacement global est utile.

À vérifier manuellement : déplacer et redimensionner la carte et le diagramme, constater l’écriture de `dragPos`, recharger la page et vérifier la persistance ; contrôler aussi les interactions de tout composant placé dans un conteneur déplaçable. Les ajustements écrivent dans les sources : relire le diff avant commit.

## Dépendances

Le lockfile testé installe Slidev 52.20.1 et le thème default 0.25.0. `npm ci` a signalé 44 vulnérabilités dans l’ensemble des dépendances de développement ; `npm audit --omit=dev` n’en signale aucune. Examiner `npm audit` avant mise à jour ; ne pas appliquer aveuglément de correction majeure.

## État du projet

Le travail commence par un catalogue technique de fonctionnalités, puis une exploration visuelle avec le mainteneur. Le thème par défaut actuel est provisoire : le nombre de thèmes, leurs couleurs, formes et typographies restent à définir. Voir [BACKLOG.md](BACKLOG.md) pour les travaux restants.

Le dépôt est destiné à être cloné, sans publication de paquet ni procédure de release définie à ce stade. Les builds sont locaux ; aucune mise en ligne ou CI n’est configurée. Les conventions de branches, de vérification et de livraison figurent dans [AGENTS.md](AGENTS.md).

## Ajouter une image

Placer une capture, par exemple `capture.png`, dans `public/images/` puis la référencer dans une slide : `![Description](/images/capture.png)`. La slide 16 du [catalogue](catalogue.md) montre une image locale et sa légende dans un même conteneur `<v-drag>` : remplacer le chemin de l’image et adapter son texte alternatif. La position du groupe est enregistrée dans `dragPos`. Le collage direct du presse-papiers dans une slide n’a pas été vérifié ; l’ajout d’un fichier et de sa référence est le parcours documenté.
