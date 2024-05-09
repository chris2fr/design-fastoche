# 🇫🇷 Système de Design de l’État

[![GitHub release](https://img.shields.io/github/v/release/gouvernementFR/webfacile.svg)](https://GitHub.com/gouvernementFR/webfacile/releases/) [![Generic badge](https://img.shields.io/badge/npm-yellow.svg)](https://www.npmjs.com/package/@gouvfr/webfacile) [![Generic badge](https://img.shields.io/badge/license-grey.svg)](https://github.com/GouvernementFR/webfacile/blob/main/LICENSE.md) [![Npm package monthly downloads](https://badgen.net/npm/dm/@gouvfr/webfacile)](https://npmjs.com/package/@gouvfr/webfacile)

Le Système de Design de l’État (ci-après, le **webfacile**) est un ensemble de composants web HTML, CSS et Javascript pour faciliter le travail des équipes projets des sites Internet publics, et créer des interfaces numériques de qualité et accessibles.

L'outil est développé, maintenu et géré par le [Service d'Information du Gouvernement (SIG)](https://www.gouvernement.fr/service-d-information-du-gouvernement-sig).

Son utilisation par les administrations est soumise à une demande d'agrément (voir partie 5 des Conditions Générales d'Utilisation).

[Voir la documentation officielle](https://www.systeme-de-design.gouv.fr).

## Licence et droit d'utilisation

Le contenu de ce projet est placé sous licence MIT License, à l'exception de la fonte Marianne. Voir [LICENSE.md](https://github.com/GouvernementFR/webfacile/blob/main/LICENSE.md).

#### ⚠️ Utilisation interdite en dehors des sites Internet de l'État

>Il est formellement interdit à tout autre acteur d’utiliser le Système de Design de l’État (les administrations territoriales ou tout autre acteur privé) pour des sites web ou des applications. Le Système de Design de l’État représente l’identité numérique de l’État. En cas d’usage à des fins trompeuses ou frauduleuses, l'État se réserve le droit d’entreprendre les actions nécessaires pour y mettre un terme.

Voir les [conditions générales d'utilisation](doc/legal/cgu.md).

#### ⚠️ Prohibited Use Outside Government Websites

>This Design System is only meant to be used by official French public services' websites and apps. Its main purpose is to make it easy to identify governmental websites for citizens. See terms.

## Installation

L'installation du Système de Design de l'État (ci-après, le **webfacile**) peut se faire de manières différentes. En téléchargeant l'ensemble des fichiers nécessaires à son utilisation, en utilisant le gestionnaire de paquets **NPM**, ou encore via **git**.

### Fichiers statiques

Il est possible de télécharger l'ensemble du **webfacile** au format zip ci-dessous. Le zip contient un ensemble de fichiers CSS et Javascript, ainsi que les différentes polices web utilisées (Marianne et Spectral), et un ensemble d'icônes et de pictogrammes.

Vous trouverez sur [la page Release de Github](https://github.com/GouvernementFR/webfacile/releases), toutes les sources des versions précédentes et la dernière en date.

### NPM

Le **webfacile** est disponible sur NPM via un ensemble de packages qu'il est possible d'ajouter directement à votre projet. Il est de ce fait nécessaire d'installer [NodeJS](https://nodejs.org), et d'avoir un fichier **package.json** à la racine de votre projet. (Il est possible d'en créer un directement via la commande `npm init`).

Une fois en place, il suffit d'installer le package **@gouvfr/webfacile** contenant l’ensemble des composants:

```
npm install @gouvfr/webfacile
```
Il est également possible d'installer le package avec [Yarn](https://yarnpkg.com/) :
```
yarn add @gouvfr/webfacile
```

Une fois terminé le webfacile sera alors installé dans le dossier ```node_modules/@gouvfr/webfacile/```.

Pour visualiser les exemples, il est nécessaire de lancer un serveur local :

```
npm run serve
```

Une fois le serveur lancé, les exemples sont disponibles à l'adresse : http://localhost:8080/example/

### Structure du webfacile

La structure que nous mettons à disposition , sur le zip ou npm est la suivante:
- **dist** : contient les fichiers css et js à importer en fonction des packages utilisés.
- **src** : contient les sources sass et js des différents composants.
- **example** : contient des snippets html d’example des composants que vous pouvez consulter en local.

### Configuration de votre projet

Lors de la création de votre projet, il est nécessaire d’adopter l’arborescence prévue par celui-ci, à savoir les fichiers HTML à la racine du projets, et les différentes sources du **répertoire dist** dans des dossiers spécifiques :

Une structure minimale serait :

```
/ Racine du projet
└── index.html
└── webfacile.min.css
└── webfacile.module.min.js
└── webfacile.nomodule.min.js
└── icons/
└── favicon/
└── fonts/
└── utility/
  └── utilities.min.css
```

Les polices de caractères utilisées sur le DS, à savoir la Marianne et la Spectral, sont des fichiers .woff et .woff2, ils doivent se trouver dans le répertoire `fonts`. Les dossiers `fonts` et `favicon` doivent être placés au même niveau que le dossier contenant le CSS du core du webfacile (ou au même niveau que le css `webfacile.min.css` à la racine de dist, qui contient le core).

Le fichier `utilities.min.css` doit être placé un niveau plus bas que le dossier `icons`, dans dossier utility par exemple, pour respecter les chemins d'accès vers les icônes.

### Le HTML

Le point de départ de l’utilisation du webfacile  est la création de fichiers HTML, afin de pouvoir utiliser les différents composants. Ces fichiers sont à mettre à la racine de votre projet. L’exemple ci dessous est le code minimal afin de pouvoir utiliser le webfacile.

L’ajout de l’attribut **data-webfacile-scheme** sur la balise html permet d’activer la gestion des thèmes clair et sombre. Les valeurs possibles sont `system`, `light`, `dark`. La valeur “system” permet d’utiliser la configuration définie sur le système d’exploitation de l’utilisateur.

Consulter la [documentation des paramètres d’affichage](https://www.systeme-de-design.gouv.fr/elements-d-interface/composants/parametre-d-affichage) afin d’en savoir plus.

```html
<!doctype html>
<html lang="fr" data-webfacile-scheme="system">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <meta name="format-detection" content="telephone=no">

    <meta name="theme-color" content="#000091"><!-- Défini la couleur de thème du navigateur (Safari/Android) -->
    <link rel="apple-touch-icon" href="favicon/apple-touch-icon.png"><!-- 180×180 -->
    <link rel="icon" href="favicon/favicon.svg" type="image/svg+xml">
    <link rel="shortcut icon" href="favicon/favicon.ico" type="image/x-icon"><!-- 32×32 -->
    <link rel="manifest" href="favicon/manifest.webmanifest" crossorigin="use-credentials">
    <!-- Modifier les chemins relatifs des favicons en fonction de la structure du projet -->
    <!-- Dans le fichier manifest.webmanifest aussi, modifier les chemins vers les images -->
    
    <link rel="stylesheet" href="webfacile.min.css">
    <link rel="stylesheet" href="utility/utility.min.css">

    <title>Titre de la page - Nom du site</title>
  </head>
  <body>

    <!--
      code de la page
     -->

    <!-- Script en version es6 module et nomodule pour les navigateurs le ne supportant pas -->
    <script type="module" src="webfacile.module.min.js"></script>
    <script type="text/javascript" nomodule src="webfacile.nomodule.min.js"></script>
  </body>
</html>
```

**Les CSS**

Afin d’inclure la totalité des composants et des styles du système de design, il est nécessaire d’inclure la feuille de style `dist/webfacile.min.css`.

Les classes utilitaires, notamment les icônes, sont disponibles dans un fichier à part dans `dist/utility/utility.scss`.
```html
<html>
  <head>
    <link rel="stylesheet" href="webfacile.min.css">
    <link rel="stylesheet" href="utility/utility.min.css">
```
Il est aussi possible d’importer uniquement ce que l’on souhaite utiliser. En effet, pour ajouter un composant seul il suffit d’importer son CSS ainsi que celui de chacune des dépendances de ce composant. Ces dépendances sont listés dans le `README.md` de chaque package.

```html
<html>
  <head>
    <link rel="stylesheet" href="core.min.css">
    <link rel="stylesheet" href="link.min.css">
    <link rel="stylesheet" href="button.min.css">
```


**Le Javascript**

L’ensemble du code javascript nécessaire au bon fonctionnement du DS se trouve dans deux fichiers `dist/webfacile.module.min.js` et `dist/webfacile.nomodule.min.js`.


Le fichier webfacile.module.min.js utilise les modules javascript natifs - sa balise script d’appel doit avoir l’attribut **type=”module”**.

Le fichier webfacile.nomodule.min.js est utilisé par les anciens navigateurs ne supportant pas les modules javascript (es6) - sa balise script doit contenir l’attribut **nomodule**.
Il est **impératif** d’appeler les **deux fichiers** javascript afin que le code s’exécute correctement sur l’ensemble des navigateurs supportés :

```html
    <script type="module" src="webfacile.module.min.js"></script>
    <script type="text/javascript" nomodule src="webfacile.nomodule.min.js"></script>
  </body>
</html>
```

> NB : Le package analytics est géré indépendament et doit être ajouté après le js du webfacile. Voir [documention analytics](https://github.com/GouvernementFR/webfacile/blob/main/src/analytics/doc/analytics.md)

De la même façon que le CSS il est possible d’importer uniquement le JS des composants utilisés (et leurs dépendances).

### Icônes

Les icônes sont stockées dans `dist/icons` et classées par catégories.

Le design système utilise principalement des icônes de la librairie remixIcon. Il existe aussi des icônes personnalisées, celles-ci sont préfixée par “webfacile--”.

Afin d’utiliser ces icônes, des classes utilitaires CSS sont associés à chaque icône. Par ex. : `webfacile-icon-error-fill`

Ces classes sont disponibles dans `utility` qui importe `dist/utility/icons/icons.css`.

Il est aussi possible d’importer uniquement certaines catégories d’icônes afin d’optimiser le poids. Par ex. :  `dist/utility/icons/system/system.css` pour les icônes “system”.

Pour plus d’informations : [Voir la documentation des icônes](https://www.systeme-de-design.gouv.fr/elements-d-interface/fondamentaux-techniques/icones).

### Favicon

[La documentation des favicons](https://www.systeme-de-design.gouv.fr/elements-d-interface/fondamentaux-techniques/icone-de-favoris) détaille la façon de les implémenter dans vos pages.

## Fonctionnement

### BEM

Le **webfacile** utilise la méthodologie [**BEM**]([https://css-tricks.com/bem-101/]([http://getbem.com/naming/](http://getbem.com/naming/))) (Block - Element - Modifier) comme convention de nommage des classes CSS. Elle permet aux développeurs une meilleure compréhension de la relation entre HTML et CSS dans un projet donné.

Selon cette méthodologie, un block représente le plus haut niveau d'abstraction d'un nouveau composant, par exemple `.parent`.

Des éléments (ou enfants), peuvent être placés à l'intérieur de ces blocks, et sont désignés par deux underscore précédés du nom du block : `.parent__element`.

Les modifiers quant à eux, servent à manipuler les blocs, de manière à les styliser de manière indépendante en s'assurant de ne pas induire de changement à des blocks sans aucun rapport avec celui-ci. Ils sont notés à l'aide de deux tirets précédés du nom du block comme suit : `.parent--modifier`.

### Utilisation

Le **webfacile** est constitué de différents composants, que vous pouvez utiliser indépendamment au sein de votre projet.

Une documentation spécifique est prévue pour chaque composant, précisant ses principes d’utilisation, ainsi que les snippets de code HTML à utiliser pour votre projet.

🙌 Vous êtes maintenant prêt(e) à utiliser le **webfacile**.

## Contribution

Le processus de contribution est détaillé sur la [page CONTRIBUTING.md](CONTRIBUTING.md).

## Documentation

[Documentation développeurs](https://www.systeme-de-design.gouv.fr/utilisation-et-organisation/developpeurs/)
