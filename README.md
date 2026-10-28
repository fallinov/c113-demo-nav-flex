# C113 — Démo Flexbox : la barre de navigation

Démo du cours 113 (séance 9) : une liste de liens brute devient une barre de navigation
grâce à Flexbox.

**Site en ligne** : https://fallinov.github.io/c113-demo-nav-flex/

## Les étapes, un commit chacune

Ouvre l'onglet **Commits** du dépôt et clique sur un commit : GitHub montre exactement les
lignes ajoutées (en vert) à chaque étape.

| Étape | Commit | Ce qui change à l'écran |
|-------|--------|-------------------------|
| 1 | HTML : quatre pages avec la même navigation | Liste à puces verticale, liens bleus soulignés |
| 2 | Retirer les puces et le retrait | Plus de puces, la liste reste verticale |
| 3 | `display: flex` sur la liste | Les liens passent sur une ligne… collés |
| 4 | `gap` | Les liens s'espacent |
| 5 | Header sombre, liens cliquables | Fond sombre, zone cliquable, survol et focus |
| 6 | Header en flex | Logo à gauche, menu à droite, centrés verticalement |
| 7 | `flex-wrap` | Sur téléphone, le menu passe à la ligne au lieu de déborder |

## À retenir

- `display: flex` se met sur le **parent** : ce sont ses **enfants directs** qui se placent
  côte à côte. Ici, le parent est `<ul class="menu">`, les enfants sont les `<li>`.
- `justify-content` place les éléments sur l'axe principal (horizontal par défaut) :
  `flex-start`, `center`, `flex-end`, `space-between`.
- `align-items` les place sur l'axe secondaire (vertical par défaut) : `center` aligne le logo
  et les liens sur la même ligne médiane.
- `gap` espace les éléments **entre eux**, sans marge en trop au début ni à la fin.
- `flex-wrap: wrap` autorise le passage à la ligne quand la place manque.

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

- [Flexbox Froggy](https://flexboxfroggy.com/#fr) — 24 niveaux pour maîtriser `justify-content`
  et `align-items`
- Plan de la séance : https://devjs.ch/cours/113/plan#seance-9-28-octobre-2026
