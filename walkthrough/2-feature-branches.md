# 2. Branches de Feature 

| Date | Phase |
| --- | --- |
| 1<sup>er</sup> Février | Development |

La version 1.0 a été mise en production hier sans problème. Tout le code de cette version a été fusionné dans les branches `master` et `develop` du projet. Les nouvelles recettes pour février ont été envoyées à l'équipe :

| Rédacteur  | Recette  |
| --- | --- |
| Cuba Pudding Jr. | http://allrecipes.com/recipe/228654/quick-oatmeal-pancakes/ |
| Eggs Benny | http://allrecipes.com/recipe/174361/asparagus-with-cranberries-and-pine-nuts/ |
| John Lemon | http://allrecipes.com/recipe/18241/candied-carrots/ |
| Madame Croque | http://www.realsimple.com/food-recipes/browse-all-recipes/roast-pork-sandwich/ |

## :running: Activités

Suivez les activités ci-dessous pour parcourir le processus de création d'une branche de fonctionnalité et de création d'une demande d'extraction pour fusionner vos changements dans le référentiel source.

### 1 - Créer une branche de fonctionnalité

__Tous les membres de l'équipe__

Choisissez un rédacteur &mdash ; vous ajouterez sa recette au projet dans une nouvelle branche de fonctionnalité. S'il y a plus de rédacteurs que de personnes, ce n'est pas grave, une seule branche de fonctionnalité sera finalement fusionnée.

Créez une branche de fonctionnalité à partir de la branche `develop` qui contient le nom de l'auteur et le mois de la recette :
```sh
$ git checkout develop

$ git checkout -b cuba-pudding-jr-feb

$ git branch
* cuba-pudding-jr-feb
  develop
  master
```

:bulb : Les branches des fonctionnalités seront nommées de telle sorte que quelqu'un d'autre puisse regarder les branches en cours et avoir une idée approximative du travail effectué sur chaque branche.

:bulb: Vous pouvez créer une branche sans l'extraire immédiatement via la commande `git branch` :
```sh
$ git branch cuba-pudding-jr-feb
```

### 2 - Apporter des modifications au projet

__Tous les membres de l'équipe__

Dans votre éditeur de texte, effectuez les modifications suivantes :

1. Ajoutez la nouvelle recette dans le répertoire [`/app/recipe/feb/`](/app/recipe/feb/).
2. Mettez à jour la page de l'écrivain dans le répertoire [`/app/writer/`](/app/writer/).
3. Mettre à jour le fichier principal [`/app/index.md`](/app/index.md).

Puisque d'autres personnes vont faire des changements en même temps, faites attention à ne pas modifier les lignes de code qui ne sont pas pertinentes pour votre changement.

### 3 - Examen des modifications

__Tous les membres de l'équipe__

Si vous regardez l'état actuel de git, vous verrez 2 fichiers avec des changements non-stagés et un nouveau dossier qui n'a pas été suivi par git :
```sh
$ git status
On branch cuba-pudding-jr-feb
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   app/index.md
        modified:   app/writer/cuba-pudding-jr.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        app/recipe/feb/

no changes added to commit (use "git add" and/or "git commit -a")
```

Si vous lancez un diff, vous devriez voir les modifications qui ont été apportées aux fichiers qui sont suivis par git :
```sh
$ git diff
diff --git a/app/index.md b/app/index.md
index ac3abad..9777cd5 100644
--- a/app/index.md
+++ b/app/index.md
@@ -8,7 +8,7 @@ Welcome to _Flavor_, the only place on the planet where your taste buds won't be

 ### [Cuba Pudding Jr.](writer/cuba-pudding-jr.md) | cubapud@flavor.magazine

-[Grilled Peach Salad](recipe/jan/grilled-peach-salad.md)
+[Quick Oatmeal Pancakes](recipe/feb/quick-oatmeal-pancakes.md)

 ### [Eggs Benny](writer/eggs-benny.md) | englishmuffin@flavor.magazine

diff --git a/app/writer/cuba-pudding-jr.md b/app/writer/cuba-pudding-jr.md
index 250faea..7315699 100644
--- a/app/writer/cuba-pudding-jr.md
+++ b/app/writer/cuba-pudding-jr.md
@@ -4,4 +4,5 @@

 Recipe Picks:

+- February: [Quick Oatmeal Pancakes](../recipe/feb/quick-oatmeal-pancakes.md)
 - January: [Grilled Peach Salad](../recipe/jan/grilled-peach-salad.md)
(END)
```

:bulb: Appuyez sur <kbd>Enter</kbd> pour afficher d'avantages de lignes de diff (si nécessaire) et <kbd>Ctrl</kbd>+<kbd>C</kbd> pour fermer le diff.

Si vous trouvez des changements qui n'aurait pas du avoir lieu corriger les maintenant.

### 4 - Mise en attente et validation des changements

Mettez en attente toutes les modifications que vous avez faites jusqu'à présent :
```sh
$ git add app/*
# Attention, l'utilisation d'un joker ajoute tous les fichiers modifiés qui correspondent au motif.

$ git status
On branch cuba-pudding-jr-feb
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   app/index.md
        new file:   app/recipe/feb/quick-oatmeal-pancakes.md
        modified:   app/writer/cuba-pudding-jr.md
```

:bulb: Si vous faites un diff maintenant vous ne verrez aucun changement, c'est parce que `git diff` compare tous les changements staged aux changements unstaged.

:bulb : Vous pouvez trouver que le processus d'affichage des différences, de mise à disposition des fichiers et de validation est plus facile dans GitHub Desktop.

Maintenant que toutes vos modifications ont été mises à disposition, livrez-les avec un message approprié :
```sh
$ git commit -m "Adding Cuba Pudding Jr.'s Feb Recipe"
```

### 5 -  Pousser les changements vers le Fork

Maintenant que vos changements ont été validés, publions-les dans votre Fork sur GitHub :
```sh
$ git push -u me HEAD
```

:bulb : Spécifier la référence HEAD indique à git de pousser sur la même branche que le HEAD de votre projet local, qui est actuellement votre branche de fonctionnalité.

:bulb : Le drapeau `-u` indique à git de lier votre branche locale avec la branche distante de sorte que les futures commandes de push & pull ne nécessitent pas que vous
de spécifier d'où vous voulez pousser ou tirer du code.

Naviguez vers votre Fork sur Github, vous devriez maintenant voir votre nouvelle branche dans l'interface.


### 6 - Ouvrir une Pull Request

Sur votre fork GitHub, vous devriez voir un bloc en haut indiquant que vous avez récemment poussé une branche. Si ce bloc est visible, cliquez sur le bouton "Compare & Pull Request" à droite de votre branche de fonctionnalité. S'il n'est pas disponible, choisissez votre branche dans la liste déroulante juste au-dessus de la liste du répertoire de code, puis cliquez sur le bouton "New Pull Request" à droite de la liste déroulante.

Dans l'interface de la demande de mise à jour, assurez-vous que la fourche de base est `source-username\repository-name` et que la branche de base est `develop`. Cela signifie que vous demandez à fusionner vos modifications dans la branche `develop` du dépôt source. À ce moment-là, assurez-vous également que les branches head fork et compare correspondent à votre branche GitHub Fork et feature branch, respectivement.

Veuillez rédiger un message documentant les changements que vous avez effectués, puis cliquez sur le bouton vert "Create pull request".

## Suivant

Ensuite, nous allons parcourir le processus de révision d'une demande de retrait, de visualisation locale du code d'une autre personne et de fusion d'une pull request.

[3. Code Review](3-code-review.md)

## Quick Links

- [Readme](../readme.md)
- [1. Setup](1-setup.md)
- [3. Code Review](3-code-review.md)
- [4. Fetching Latest](4-fetching-latest.md)
- [5. Hotfix](5-hotfix.md)
- [6. Release Branch](6-release-branch.md)
- [7. Release Bugs](7-release-bugs.md)
- [8. Completed Release](8-completed-release.md)
