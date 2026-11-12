# C113 — Démo Flexbox : la barre de navigation

Démo du cours 113 (séance 9) : une liste de liens brute devient une barre de navigation
grâce à Flexbox.

Tu es sur la branche **`seance-13-depart`** : le point de départ de la démo « casser, lire,
réparer » (séance 13). Trois pages sont propres. La page **À propos** contient les erreurs
classiques d'un projet d'élève, une pour chaque outil de contrôle du Jalon 3. Le résultat corrigé
est sur [`seance-13-solution`](https://github.com/fallinov/c113-demo-nav-flex/tree/seance-13-solution).

## La démo contrôle, quatre outils

1. **Un site propre d'abord** : `index.html` collé dans le
   [validateur W3C](https://validator.w3.org/#validate_by_input), zéro erreur.
2. **`a-propos.html` dans le validateur** : huit messages pour cinq fautes. On lit le premier, on
   corrige, on revalide. Une balise `<a>` non fermée fait apparaître trois erreurs à elle seule.
3. **WAVE** sur la page en ligne : icônes rouges, panneau Structure pour l'ordre des titres,
   onglet Contraste.
4. **Le téléphone** : DevTools en mode appareil, 375 px. La page défile horizontalement et
   l'onglet Réseau montre une image de 3,9 Mo.

| Faute dans `a-propos.html` | Qui la voit | Ce que l'outil dit |
|---|---|---|
| `<html>` sans `lang="fr"` | W3C (avertissement), WAVE (erreur) | « Consider adding a lang attribute » / « Language missing » |
| `<meta name="viewport">` absent | Le téléphone | Page dézoomée, texte minuscule |
| `<img>` sans `alt` | W3C, WAVE | « An img element must have an alt attribute » / « Missing alternative text » |
| `creux-du-van.jpg` de 3,9 Mo, 5488 px | DevTools Réseau, défilement à 375 px | 3,9 Mo au lieu de 217 Ko ; la page fait 5512 px de large |
| `<h3>` juste après le `<h1>` | W3C, WAVE | « skipping 1 heading level » / « Skipped heading level » |
| `<h2>` dans un `<p>` | W3C | « No p element in scope but a p end tag seen » |
| Texte nu dans le `<ul>` (le `<li>` oublié) | W3C | « Text not allowed in element ul in this context » |
| `<a>` jamais fermé | W3C | « Unclosed element a », puis deux erreurs de plus sur `</p>` et `</main>` |
| Légende en gris clair `#9ca3af` sur fond clair | WAVE | « Very low contrast », 2,5:1 au lieu de 4,5:1 |

Note : du texte posé directement dans `<body>` n'est **pas** une erreur pour le validateur. C'est
dans une liste (`<ul>`) ou un tableau qu'un texte sans balise est refusé.

## La démo images, quatre étapes

Sur `index.html` et `style.css`, DevTools ouverts sur l'onglet Réseau.

| Étape | Ce qu'on fait | Ce qu'on voit |
|-------|---------------|---------------|
| 1 | `<img src="img/creux-du-van.jpg">` dans la bannière | Réseau : 3,9 Mo, plusieurs secondes en « 3G lente » |
| 2 | Squoosh : 1600 px de large, WebP, qualité 65 à 75 | Réseau : 217 Ko au lieu de 3,9 Mo, la même photo à l'œil |
| 3 | La photo passe en fond : `background-image`, `background-size: cover`, `background-position`, `background-color` de secours | La bannière est remplie, le texte est posé dessus |
| 4 | Un voile sombre et du texte blanc | Le titre reste lisible, contraste vérifié |

Photo : le Creux du Van, par [Joël Brunner sur Unsplash](https://unsplash.com/photos/QAzZmjwcWKw),
licence Unsplash.

## La démo Grid, trois étapes

Tout se passe dans `style.css`, sur `.galerie`, la `<section>` qui contient les sept `<article>`.
Teste à 375 px après chaque étape, puis élargis la fenêtre.

| Étape | Règle | Ce qui change à l'écran |
|-------|-------|-------------------------|
| 1 | `display: grid` et `gap: 1rem` | Rien, sauf l'espace entre les cartes : une grille sans colonnes n'en a qu'une |
| 2 | `@media (min-width: 768px)` : `repeat(2, 1fr)`, puis `(min-width: 1024px)` : `repeat(3, 1fr)` | Mobile d'abord : une colonne sur téléphone, deux sur tablette, trois sur grand écran |
| 3 | `grid-template-columns: repeat(auto-fill, minmax(250px, 1fr))` | Le raccourci : une colonne à 375 px, deux à 600 px, trois à 960 px, sans media query |

- `display: grid` se met sur le **parent**, comme `display: flex` : ses **enfants directs**
  deviennent les cases.
- `1fr` est une fraction de la place libre : `repeat(3, 1fr)` vaut `1fr 1fr 1fr`.
- Mobile d'abord : la règle sans media query est celle du téléphone, `min-width` ajoute les
  colonnes sur les écrans plus larges.
- `minmax(250px, 1fr)` : la colonne fait au moins 250 px, et se partage le reste.
- `repeat(auto-fill, …)` : le navigateur place autant de colonnes que la largeur le permet.
- Le contenu est plafonné à 60rem par `max-width` : la grille ne dépasse jamais trois colonnes.

**Site en ligne** : https://fallinov.github.io/c113-demo-nav-flex/

## Les étapes, un commit chacune

Ouvre les [commits de cette branche](https://github.com/fallinov/c113-demo-nav-flex/commits/solution-etape-9/)
et clique sur un commit : GitHub montre exactement les lignes ajoutées (en vert) à chaque étape.

| Étape | Commit | Ce qui change à l'écran |
|-------|--------|-------------------------|
| 1 | HTML : quatre pages avec la même navigation | Liste à puces verticale, liens bleus soulignés |
| 2 | Retirer les puces et le retrait | Plus de puces, la liste reste verticale |
| 3 | `display: flex` sur la liste | Les liens passent sur une ligne… collés |
| 4 | `gap` | Les liens s'espacent |
| 5 | Header sombre, liens cliquables | Fond sombre, zone cliquable, survol et focus |
| 6 | Header en flex | Logo à gauche, menu à droite, centrés verticalement |
| 7 | `flex-wrap` | Sur téléphone, le menu passe à la ligne au lieu de déborder |
| 9 | `aria-current="page"` | Le lien de la page affichée reste en couleur |
| 9 | `max-width` et `margin: 0 auto` | Sur grand écran, le contenu reste centré |
| 9 | `transition` | Au survol, le fond du lien change en douceur |

## À retenir

- `display: flex` se met sur le **parent** : ce sont ses **enfants directs** qui se placent
  côte à côte. Ici, le parent est `<ul class="menu">`, les enfants sont les `<li>`.
- `justify-content` place les éléments sur l'axe principal (horizontal par défaut) :
  `flex-start`, `center`, `flex-end`, `space-between`.
- `align-items` les place sur l'axe secondaire (vertical par défaut) : `center` aligne le logo
  et les liens sur la même ligne médiane.
- `gap` espace les éléments **entre eux**, sans marge en trop au début ni à la fin.
- `flex-wrap: wrap` autorise le passage à la ligne quand la place manque.
- `aria-current="page"` dit au navigateur quel lien mène à la page affichée : il s'écrit sur
  un lien différent à chaque page, et `[aria-current="page"]` le vise en CSS.
- `max-width` plafonne la largeur sans empêcher le bloc de rétrécir. `margin: 0 auto` partage
  la place restante à gauche et à droite : sans `max-width`, il n'y a rien à partager.

## Structure

```
c113-demo-nav-flex/
├── index.html
├── projets.html
├── a-propos.html
├── contact.html
├── style.css
└── images/
    └── projet-1.svg … projet-7.svg
```

## S'entraîner

Nuxy, formation HTML & CSS, **module 10 — Flexbox** :

- [Introduction : Flexbox](https://www.nuxy.ch/exercises/css-intro-flexbox)
- [Passe en mode flex](https://www.nuxy.ch/exercises/css-display-flex)
- [Répartis sur l'axe](https://www.nuxy.ch/exercises/css-justify-content)
- [Centre sur l'autre axe](https://www.nuxy.ch/exercises/css-align-items)
- [Des espaces sans marges](https://www.nuxy.ch/exercises/css-gap)
- [Colonne ou rangée](https://www.nuxy.ch/exercises/css-flex-direction)
- [Défi : la navbar parfaite](https://www.nuxy.ch/exercises/css-barre-navigation)
- [Examen du module 10](https://www.nuxy.ch/exercises/css-quiz-flexbox)

Pour aller plus loin :

- [Tu es ici](https://www.nuxy.ch/exercises/css-page-en-cours) (module 11) — signaler la page
  en cours dans le menu
- [Le menu qui s'empile](https://www.nuxy.ch/exercises/css-menu-responsive) (module 12) — le
  menu en colonne sur téléphone, en rangée sur grand écran

Autres outils :

- [Flexbox Froggy](https://flexboxfroggy.com/#fr) — 24 niveaux pour maîtriser `justify-content`
  et `align-items`
- [Flexbox Sandbox](https://flexbox.tirtho.ch/) — règle les propriétés du conteneur et des
  éléments, observe les axes et copie le CSS généré
- Plan de la séance : https://devjs.ch/cours/113/plan#seance-9-28-octobre-2026
