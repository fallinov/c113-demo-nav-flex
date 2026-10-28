# C113 — Démo Flexbox : la barre de navigation

Démo du cours 113 (séance 9) : une liste de liens brute devient une barre de navigation
grâce à Flexbox.

Tu es sur la branche **`solution-etape-8`** : la solution de la séance 9, plus l'étape 8
(mobile d'abord, séance 11). La solution de la séance 9 seule est sur la branche
[`solution`](https://github.com/fallinov/c113-demo-nav-flex/tree/solution), le code de départ
sur [`main`](https://github.com/fallinov/c113-demo-nav-flex).

**Site en ligne** : https://fallinov.github.io/c113-demo-nav-flex/

## Les étapes, un commit chacune

Ouvre les [commits de cette branche](https://github.com/fallinov/c113-demo-nav-flex/commits/solution-etape-8/)
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
| 8 | Mobile d'abord (séance 11) | Sur téléphone, un lien par ligne ; dès 768 px, la barre en ligne |

## À retenir

- `display: flex` se met sur le **parent** : ce sont ses **enfants directs** qui se placent
  côte à côte. Ici, le parent est `<ul class="menu">`, les enfants sont les `<li>`.
- `justify-content` place les éléments sur l'axe principal (horizontal par défaut) :
  `flex-start`, `center`, `flex-end`, `space-between`.
- `align-items` les place sur l'axe secondaire (vertical par défaut) : `center` aligne le logo
  et les liens sur la même ligne médiane.
- `gap` espace les éléments **entre eux**, sans marge en trop au début ni à la fin.
- `flex-wrap: wrap` autorise le passage à la ligne quand la place manque.
- Mobile d'abord : le CSS de base vise le téléphone (`flex-direction: column`), la media query
  `@media (min-width: 768px)` ajoute la mise en page des grands écrans (`flex-direction: row`).

## Structure

```
c113-demo-nav-flex/
├── index.html
├── projets.html
├── a-propos.html
├── contact.html
└── css/
    └── style.css
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
