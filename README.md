# C113 — Démo Flexbox : la barre de navigation

Exercice du cours 113 (séance 9) : transformer une liste de liens brute en barre de navigation
grâce à Flexbox.

Ce dépôt contient le **code de départ** : quatre pages HTML avec la même navigation, affichée
comme une simple liste à puces.

## Démarrer

1. Dans WebStorm : **File → New → Project from Version Control**, colle l'URL de ce dépôt.
2. Ouvre `index.html` dans Brave ou Firefox.
3. Écris ton CSS dans `css/style.css`, une étape après l'autre, et recharge la page à chaque fois.

## Les étapes

| Étape | À faire | Propriétés |
|-------|---------|------------|
| 1 | Enlever les puces et le retrait de la liste `.menu` | `list-style`, `margin`, `padding` |
| 2 | Mettre les liens sur une ligne | `display: flex` |
| 3 | Espacer les liens | `gap` |
| 4 | Header sombre, liens blancs, zone cliquable plus grande, survol | `background-color`, `display: block`, `padding`, `:hover`, `:focus` |
| 5 | Logo à gauche, menu à droite, centrés verticalement | `display: flex` sur `.header`, `justify-content`, `align-items` |
| 6 | Sur téléphone, le menu passe sous le logo au lieu de déborder | `flex-wrap` |

Teste l'étape 6 avec la vue mobile des DevTools (320 px de large).

## La solution

Elle est sur la branche [`solution`](https://github.com/fallinov/c113-demo-nav-flex/tree/solution),
une étape par commit : [voir les commits](https://github.com/fallinov/c113-demo-nav-flex/commits/solution/).

Résultat en ligne : https://fallinov.github.io/c113-demo-nav-flex/

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
