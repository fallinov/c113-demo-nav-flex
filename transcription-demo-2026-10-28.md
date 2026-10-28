# Transcription — démo Flexbox du 28 octobre 2026

Cours 113, séance 9. Démo en direct : la liste de liens brute de la branche `main` devient une
barre de navigation. Le code tapé pendant la démo est sur cette branche
(`demo-sfa-28.10.2026`), dans `css/style.css` et dans les quatre pages HTML (classe `actif`).

> Transcription automatique relue : erreurs de reconnaissance vocale corrigées, hésitations et
> apartés retirés, prénoms des élèves supprimés. Les repères de temps sont en minutes depuis le
> début de l'enregistrement.

## Cloner le dépôt et créer une branche (00:00)

Pour la démo, je clone le dépôt. Dans le menu principal, tout en haut : **New → Project from
Version Control**, un nouveau projet depuis un gestionnaire de versions comme GitHub. On colle
l'adresse du dépôt. WebStorm le range automatiquement dans le dossier `WebstormProjects` ; on
clique sur **Clone** pour copier le dépôt distant sur notre portable. Une fois le clonage
terminé, il demande s'il faut ouvrir le projet dans la fenêtre existante ou dans une nouvelle :
je prends la fenêtre existante.

On ouvre `index.html` dans Firefox pour voir le résultat actuel : un menu structuré
correctement, avec une liste à puces, mais au niveau du look, ce n'est pas très cool.
L'objectif, vous pouvez le voir en passant sur la branche `solution` (**Checkout**) : un menu
classique, comme on en trouve sur n'importe quel site. Passer de ce truc brut à quelque chose de
joli et d'utilisable, avec de gros boutons qu'on peut bien appuyer, y compris sur un smartphone.

C'est responsive, donc ça s'adapte, mais ce n'est pas le top. Aujourd'hui, exceptionnellement,
on commence par la version grand écran ; on verra la version smartphone quand on attaquera la
partie responsive. On fait donc l'inverse de ce que je vous dis d'habitude : normalement, il
faut commencer par le mobile.

Pour ne pas casser la branche principale, je crée une nouvelle branche à partir de `main`.
Vérifiez d'abord que vous êtes bien sur `main` (**Checkout**), puis **New Branch**. Le nom, vous
mettez ce que vous voulez : votre nom, `demo-flex`… Ce n'est pas obligatoire pour vous : de
toute façon, vous n'avez pas les droits pour modifier mon dépôt. Moi, par contre, si je
sauvegarde sur `main`, je casse ma branche.

## La structure du site (00:04)

Le site a plusieurs pages, et on peut naviguer de l'une à l'autre. Toutes les pages ont le même
header et le même footer. Le logo ramène à la page d'accueil. La structure : le `header`, le
contenu principal dans le `main`, et le `footer`.

Ce qui nous intéresse, c'est le header : le logo « Mon portfolio », puis la navigation. Le menu
de navigation, on le met dans une `nav`, et une `nav` est toujours structurée par une liste à
puces : ce sont les bonnes pratiques. Le problème de la liste à puces, c'est qu'elle ajoute des
décorations dont on ne veut pas : elle décale le texte vers la droite et elle met une petite
puce. Première chose à faire : supprimer les puces et le décalage.

## Inspecter la liste (00:05)

D'où vient ce décalage ? Si on ne sait pas, le plus simple, c'est l'inspecteur : clic droit
dans le navigateur, **Inspecter**. Quand je passe sur la liste, il affiche ses différentes
dimensions, en trois couleurs : le bleu, c'est la dimension de l'élément, sa hauteur et sa
largeur naturelles ; le jaune, ce sont les marges extérieures ; le violet, le padding. On
retrouve ces informations dans l'onglet de mise en page : la taille, le padding (la marge
intérieure), la margin (la marge extérieure). Quand je survole ces valeurs, le navigateur les
met en évidence dans la page.

On voit que c'est la liste à puces, le `ul`, qui crée une marge intérieure à gauche : un padding
de 40 pixels. C'est dans cette zone que s'affiche la puce. Ce padding, on va le supprimer, et
les puces aussi.

Toutes mes pages HTML sont reliées à la même feuille de style grâce au `link` vers
`css/style.css`. Pour l'instant, il n'y a que quelques règles de base que vous connaissez : les
variables de couleur ; le `body` avec `margin: 0` pour que les éléments puissent se coller au
bord de la page, une police, une hauteur de ligne, une couleur de texte, une couleur de fond ;
le `main` et le `footer` avec un padding, pour que les textes ne soient pas collés au bord.

Ce padding a deux valeurs, `1rem 1.5rem` : la première pour l'axe vertical, en haut et en bas ;
la seconde pour l'axe horizontal, à gauche et à droite. On vérifie dans l'inspecteur : 16 pixels
en haut et en bas — 1 rem, c'est 16 pixels —, 24 pixels à gauche et à droite, soit 1,5 rem.

C'est pour ça qu'on ne travaille pas avec des pixels. Les pixels servent plutôt à donner des
tailles maximum ou minimum. Tout le reste doit être fluide et s'adapter à la configuration du
navigateur de la personne : si elle veut lire en 23 pixels, ça doit suivre, et ça doit
s'adapter à la taille de son écran. Une hauteur en pixels, ça passe ; une largeur en pixels, on
essaie d'éviter. On travaille avec des pourcentages, des `rem`, ou des `max-width` et
`min-width` en pixels.

## Enlever les puces et le retrait (00:10)

On sélectionne le menu grâce à sa classe : dans le CSS, j'écris `.menu`, WebStorm me le propose
directement, et j'ouvre les accolades.

D'abord, supprimer les puces avec `list-style-type`. Par défaut, ce sont des petits ronds ;
vous pouvez mettre des carrés si vous voulez, il suffit de recharger la page pour voir le
changement. Nous, on n'en veut pas : `none`.

Ensuite, les marges. On a vu le padding : on le met à 0, et le texte vient se coller au bord. On
met aussi la `margin` à 0, comme ça on supprime toutes les marges.

## `display: flex` (00:12)

On arrive au point du jour. Accueil, Projets, À propos et Contact s'affichent les uns en dessous
des autres. Nous, on aimerait les afficher côte à côte. Pour ça, on change ce qu'on appelle le
`display`. Il existe plein d'options. Le mode actuel du menu, c'est `display: block`.

Ce que je veux changer, ce n'est pas l'affichage du menu, mais celui de son contenu. Le contenu
du menu, ce sont les `li`. Je passe le menu en `display: flex`, et regardez : ce n'est pas le
menu qui change, c'est son contenu. Les `li` s'affichent côte à côte. En une seule ligne de CSS,
j'ai changé l'ordre naturel, les uns en dessous des autres, en côte à côte.

## `gap`, le conteneur et les éléments (00:14)

Deuxième chose : les éléments sont collés. On ajoute une distance entre eux avec `gap`. Avec
`1rem`, on a 16 pixels d'espace entre chaque élément ; c'est un peu beaucoup, on met la moitié,
`0.5rem` : 8 pixels.

Le menu, c'est ce qu'on appelle le **conteneur** ; ce qui est à l'intérieur, ce sont les
**éléments**. En activant `flex`, on transforme le menu en conteneur, et ses enfants directs
réagissent aux instructions du parent.

## Le tour des propriétés dans Flexbox Sandbox (00:15)

Si on reprend la page de démonstration (Flexbox Sandbox) : on a le conteneur, notre menu, et
les éléments, ses enfants. On a mis un `gap` de 8 pixels, on peut l'agrandir : c'est l'écart
entre les éléments. Tout le reste est aux valeurs par défaut.

- `flex-direction` : par défaut, les éléments s'affichent côte à côte (`row`), mais une ligne de
  CSS suffit pour les passer en colonne (`column`). Avec `row-reverse`, ils s'affichent en ordre
  inversé, de droite à gauche ; pareil avec `column-reverse`, de bas en haut. On ne trouve pas
  toujours d'exemples où on s'en sert, mais c'est possible.
- `justify-content` : l'alignement. Je peux mettre les éléments au centre, à la fin, etc. Je
  peux répartir l'espace entre les éléments pour qu'ils remplissent toute la zone
  (`space-between`), ou avec `space-around`, qui ajoute aussi de l'espace avant le premier et
  après le dernier.
- `flex-wrap` : si mes éléments sont trop grands ou trop nombreux, par défaut, ils débordent et
  ça casse tout. Ils sortent de l'écran et ça crée un défilement horizontal, ce qu'on ne veut
  pas. Avec `flex-wrap: wrap`, ceux qui n'ont plus de place passent à la ligne suivante. C'est
  hyper pratique : des photos ou des cartes, sur un smartphone, il n'y a pas la place ; on en
  aura deux côte à côte ou une seule, et les autres passent en dessous automatiquement en
  fonction de la place. Si je change la largeur de la zone, les éléments s'adaptent tout seuls.

Quand vous avez une grille d'informations à fabriquer, que ce soit des cartes, des photos ou des
textes, vous utilisez `display: flex`, vous choisissez comment aligner vos éléments, et tout
est fluide. Il n'y a pas grand-chose à faire : activer `flex`, puis paramétrer les quelques
propriétés que vous voyez là. Avec cet outil, vous pouvez même tester ce qui irait le mieux pour
votre site, puis copier le code.

Celle qu'il ne faut surtout pas oublier, c'est celle qui fait passer à la ligne quand il n'y a
plus de place. Si mon menu n'a plus assez de place, ça ne va pas du tout : il faut que les
éléments passent en dessous. On ajoute `flex-wrap: wrap` : quand il n'y a plus assez de place,
Contact passe à la deuxième ligne. Je le mets plutôt en deuxième position, après `display`, et
le `gap` en troisième. Ça ne change rien, ce sont des conventions d'écriture.

Le code du conteneur est terminé : il est passé en `flex`, ses éléments sont côte à côte, et
fluides grâce au `wrap`. Vous connaissez tous le wrap au McDo : la galette qui enroule les
aliments. Si les aliments sortent du wrap, c'est perdu. `flex-wrap`, c'est l'idée : on garde les
éléments enroulés dans le conteneur.

## Retour sur `gap` et les unités `rem` et `em` (00:20)

*Question d'un élève sur le `gap`.* Si on met 0, il n'y a pas d'espace entre les éléments. C'est
plus parlant sur la démo, avec `flex-start` plutôt que `space-between`, qui ajoute lui-même de
l'espace entre les éléments : `gap: 0`, pas d'espace ; `gap: 10px`, 10 pixels d'espace entre
chaque élément, en haut, en bas, à gauche et à droite. Ça crée de l'aération autour des
éléments.

À la fin, tout devient des pixels, mais donner l'aération en pixels, ce n'est pas une bonne
chose. Il vaut mieux une taille proportionnelle à la taille du texte : si le site est écrit en
16 pixels, l'espace doit être un multiple de 16 pixels. `1rem`, c'est une fois la taille du
texte ; `2rem`, deux fois. Cette taille dépend de la configuration du navigateur : par défaut,
16 pixels sur un ordinateur, mais certaines personnes trouvent ça trop petit et mettent 20
pixels. Sur un bon site, si j'augmente la taille du texte, les écarts augmentent aussi : tout
est proportionnel, le site garde le même aspect en 16 ou en 20 pixels.

`rem`, c'est « root em » : la taille racine, celle que l'utilisateur a réglée dans son
navigateur. Je travaille par multiples de 0,25 : `0.25rem`, `0.5rem`, `0.75rem`, `1rem`, etc.

`em`, c'est la même chose, sauf que ce n'est pas la taille du texte par défaut du navigateur,
mais celle de l'élément dans lequel je me trouve. Par exemple, sous le titre « Bienvenue », qui
est très grand, `1em` ne fera pas 16 pixels mais la taille du titre. Dans le menu, `0.5em`
donne un tout petit écart ; `0.5rem`, la moitié de 16 pixels, soit 8 pixels, l'écart
s'agrandit.

On travaille beaucoup avec ces deux unités. Mon réflexe, pour tout ce qui est aération, c'est
le `rem`, pas le pixel : de toute façon, il faut éviter le pixel au maximum. Vous retrouverez
aussi ces unités dans les codes que vous trouvez sur Internet.

## Header sombre et liens blancs (00:27)

`display: flex` et `gap`, c'est fait. Maintenant, un peu de style pour le header : on le met en
sombre. Il n'y a pas encore de règle pour le header ; je l'ajoute avant celle du `main`. Je
change le `background-color` avec la couleur sombre, `--color-dark`. On ajoute un peu de marge
intérieure, parce que tous les éléments sont collés : un `padding` de `1rem` en haut et en bas,
`1.5rem` à gauche et à droite.

Ce qui ne va plus : on ne voit plus la couleur des liens. On revient au menu : je veux traiter
les liens du menu, pas tous les liens du site. J'écris `.menu a` et je leur mets une couleur
blanche, tout simplement : la variable de la couleur de fond, `--color-bg`, qui est quasiment
blanche. Pour le contraste, pas besoin de calculer ici. Le violet du logo ne va pas non plus :
le logo est aussi un lien, il faut le changer.

`.menu a`, ça veut dire les balises `a` qui se trouvent dans le menu. L'espace entre `.menu` et
`a` veut dire : les liens à l'intérieur du menu, à n'importe quel niveau — enfants,
petits-enfants, arrière-petits-enfants.

Du coup, le poids de cette règle est plus fort que celui d'une règle pour tous les liens. Pour
ceux qui se rappellent : `.menu` est une classe, ça vaut 10 points, et `a` vaut 1 point, donc
cette règle vaut 11 points. J'aurais pu mettre tous les liens en blanc, mais alors les liens
dans le contenu de mes pages l'auraient été aussi : pas une bonne pratique. Là, je ne touche que
les liens du menu.

## Agrandir la zone cliquable (00:31)

Ces liens sont riquiqui et proches les uns des autres : il faut les rendre plus grands pour
qu'ils soient bien cliquables. Si j'inspecte un lien, la zone cliquable, c'est la zone en bleu.
Avec une souris, c'est assez grand ; sur un smartphone, non. On dit qu'il faut normalement un
carré de 39 pixels au minimum, disons 40 sur 40. Là, je suis à 21,5 pixels de haut pour 64 de
large : pas assez gros.

Pour agrandir la zone, une technique toute simple : le padding. On met une marge intérieure pour
gonfler artificiellement la zone. Avec du padding, la zone violette devient cliquable : si ma
souris est dans la zone violette, je peux cliquer. On travaille de nouveau en `rem` : `0.5rem`
en haut et en bas, `1rem` à gauche et à droite. On mesure : 37,5 pixels. Avec `0.75rem`, 45 :
un peu grand. Avec `0.6rem`, 40 : parfait. Avec un doigt sur un smartphone, j'ai bien la place
de cliquer.

Je mets une couleur d'arrière-plan jaune aux liens, juste pour bien voir la place qu'ils
prennent : c'est bien gros et bien cliquable. On laisse toujours un petit espace entre eux, pour
ceux qui ont de gros doigts : sinon, on a l'impression de cliquer sur un bouton et on clique en
fait sur l'autre, parce qu'ils sont collés. C'est le rôle du `gap`. Si j'enlève le fond jaune,
on a un bon espace entre les éléments : c'est très lisible.

## Survol, focus et coins arrondis (00:35)

Maintenant, quand je passe sur un lien, j'aimerais qu'il change de couleur pour montrer que je
suis dessus. On copie la règle `.menu a`, on la colle en dessous pour les liens survolés,
`:hover`, et pour les liens du menu qui ont le focus, `:focus`. On leur donne une couleur
d'arrière-plan, la variable `--color-primary`. Quand je passe dessus, je vois clairement sur quoi
je vais cliquer. C'est important.

Sur smartphone, le survol ne sert à rien, il n'existe pas. Mais quand vous cliquez, le focus vous
conforte : j'ai bien cliqué sur le bon élément. `:focus`, c'est quand je clique ; `:hover`,
quand je survole avec la souris.

Je n'aime pas trop ce rectangle un peu carré : on ajoute un petit arrondi, un `border-radius`,
à tous les liens du menu : `0.25rem`. Cette fois, il y a un petit bord arrondi quand je survole.

## Signaler la page active (00:37)

Ce n'était pas prévu dans la démo, mais quand je clique sur Projets, je ne sais plus sur quelle
page je suis. Dans un menu, on garde en général ce qu'on appelle un lien actif : il reste en vert,
lui aussi. On ajoute la classe `actif` au sélecteur : `.menu a.actif`.

Autre chose de pas très joli que j'avais oublié : le soulignement des liens. Dans un menu, ce
n'est pas beau, on l'enlève. Je le mets dans une règle `header a` avec `text-decoration: none` :
ça vise tous les liens du header, y compris ceux du menu, puisque le menu fait partie du header.

*Question : pourquoi le lien actif ne change pas ?* On a écrit une règle, mais dans le code HTML,
la classe n'existe pas encore. Quand je suis sur Accueil, je veux que Accueil reste en vert :
il faut ajouter la classe `actif` à ce lien. Dans l'inspecteur, on voit que le lien vers
`index.html` n'a pas la classe ; j'ajoute `class="actif"`.

On doit mettre `actif` sur le bon lien dans chacune des pages : dans `index.html`, sur le lien
Accueil ; dans `contact.html`, sur Contact ; dans `projets.html`, sur Projets ; dans
`a-propos.html`, sur À propos. Le code du header est identique dans chaque page, avec cette
petite différence : l'élément actif change pour représenter la page en cours.

WebStorm m'a proposé `active`, en anglais ; moi, j'ai mis `actif`, en français. Vous pouvez
appeler votre classe comme vous voulez, en anglais, en espagnol… Il faut simplement utiliser le
même nom dans le CSS et dans le HTML. Et la classe doit être dans le HTML, sinon le CSS ne sert
à rien.

Maintenant, quand je change de page, le lien reste en vert. On aurait aussi pu souligner le lien
actif plutôt que de le mettre en vert. Le menu est fluide : même sur un tout petit téléphone,
les liens passent les uns en dessous des autres, ça ne déborde jamais.

## Le header en flex (00:43)

Le menu est bien, mais l'en-tête n'est pas terrible : le titre n'est pas bien placé par rapport
au menu. Je voudrais le titre à gauche et le menu à droite. Pour ça, on passe aussi le header en
`display: flex`. Résultat : le logo et le menu sont sur la même ligne.

Pour l'alignement vertical, je centre tout avec `align-items: center`. Puis je mets le maximum
d'espace entre le logo et le menu avec `justify-content: space-between` : plus j'agrandis la
fenêtre, plus l'espace entre les éléments augmente. Quand il n'y a plus de place, ça donne ce
genre de chose, pas terrible : on ajoute `flex-wrap: wrap`. Et on a un menu classique avec un
logo.

Le logo, je ne l'avais pas stylé : on ajoute une règle `.logo` avec `font-weight: bold` et
`font-size: 1.25rem`. Le logo est un peu plus gros, plus visible.

Un dernier détail : quand ça passe à la ligne, le logo et le menu sont collés. Grâce à Flexbox,
comment augmenter l'espace entre les éléments, vous vous souvenez ? À Londres, dans le métro, on
dit de faire attention au trou entre la rame et le quai : *Please mind the gap*. C'est le `gap` :
`0.5rem`, puis je préfère `0.75rem` pour un petit espace sympa. Même s'il est tout petit, il évite
que le menu soit collé au logo.

Ce n'est pas parfait, mais on a presque un menu qui fonctionne sur smartphone. On a réussi à
faire un vrai menu avec un logo tout simple. Si vous faites ça dans votre projet, ça me suffit.
Il faudrait juste encore l'améliorer pour smartphone ; pour le reste, ce sont de grandes zones
bien cliquables, bien visibles, avec un bon contraste. Pour la page active, je ne garderais
peut-être pas ce format-là, vous pouvez faire quelque chose de sympa.

## Commit et push sur la branche (00:49)

*Question sur la branche créée au début.* Le code que je fais sur cette branche reste sur cette
branche. Pour sauvegarder, je fais un commit et un push : message « démo du 28.10.2026 »,
**Commit and Push**. Il le pousse sur mon dépôt. Vous, si vous faites commit et push, vous ne
pourrez pas, parce que vous n'avez pas les droits sur mon dépôt.

Comme ça, je n'ai pas touché à mon code de départ : l'année prochaine, avec une nouvelle classe,
je pourrai reprendre le même code. Si j'avais modifié `main`, j'aurais tout effacé. Je fais une
branche, je travaille dessus, et plus tard je pourrai la supprimer.

Pour nos cours, on travaille tout le temps sur `main`, mais dans la pratique, on ne travaille
jamais sur `main`. On crée une branche et on travaille dessus ; si on est content, on la
fusionne avec `main` ; sinon, on l'abandonne et on la supprime. On verra ça en deuxième année,
ou peut-être en JavaScript.

## Questions : conteneur et éléments (00:50)

*Question : comment savoir faire tout ça ?* Moi, je connais les codes presque par cœur, mais
pas tous. Si vous ne savez pas comment faire une page, testez dans l'outil : vous dites « je
vais mettre 12 photos » et vous essayez les différentes propriétés pour choisir comment afficher
vos éléments.

Avec Flexbox, pensez toujours qu'il y a deux sortes d'éléments. Le **conteneur** : c'est lui qui
reçoit `display: flex` — chez nous, le menu. Et tout ce qu'il y a dedans, ce sont les
**éléments** (les *items*). Au conteneur, on donne des ordres : tout ce que vous voyez ici, ce
sont des éléments qui bougent en fonction de la configuration choisie.

On peut aussi modifier chaque élément individuellement : par exemple, dire que l'élément 1 prend
la dernière place, et donc changer sa position dans la liste en CSS. Un élément peut aussi
grandir ou rétrécir selon la place.

Grâce à Flexbox, vous pouvez facilement passer vos éléments de ligne en colonne, ou inversement,
et gérer leur positionnement. C'est très simple : vous avez vu, ce sont quelques règles. Il
existe aussi CSS Grid pour les grilles, mais c'est un peu plus complexe.
