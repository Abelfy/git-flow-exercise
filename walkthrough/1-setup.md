# 1. Setup

Afin de contribuer à un projet GitHub, vous aurez besoin de deux choses : un Fork GitHub et un clone local de ce projet.

## :running: Activités

Suivez les activités ci-dessous pour vous préparer à la suite de l'exercice.


### 1 - Fork un dépôt de sources

__Tous les membres de l'équipe__

Fork le dépôt de sources :
   1. Visitez https://github.com/Abelfy/git-flow-exercise/.
   2. Cliquez sur le bouton "fork", et choisissez votre compte GitHub personnel si vous y êtes invité.

---

:cop: :raised_hand: - Please wait until everyone has caught up.

:construction: :construction: :construction: :construction: :construction: :construction: :construction: :construction: :construction: :construction: :construction: :construction: :construction: :construction: :construction:

---

### 2 - Cloner votre Fork

__Tous les membres de l'équipe__

Clone this project to your local machine:
```sh
$ cd ~/my/parent/directory
$ git clone https://github.com/source-username/repository-name.git
# clone the fork repository from GitHub

$ cd repository-name
# change working directory to the cloned repository
```

Voir les remotes existants :
```sh
$ git remote
origin

$ git remote -v
origin https://github.com/source-username/repository-name.git (fetch)
origin https://github.com/source-username/repository-name.git (push)
```

Vous devriez voir un remote `origin` qui pointe vers le projet GitHub source :
```sh
$ git remote show origin
* remote origin
  Fetch URL: https://github.com/source-username/repository-name.git
  Push  URL: https://github.com/source-username/repository-name.git
  HEAD branch: master
  Remote branches:
    develop tracked
    master  tracked
  Local branch configured for 'git pull':
    master  merges with remote master
  Local ref configured for 'git push':
    master  pushes to master (up to date)
```

Voir les branches existantes :
```sh
$ git branch
# show local branches
* master

$ git branch -r
# show remote branches
origin/HEAD -> origin/master
origin/develop
origin/master

$ git branch -a
# show all branches
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/develop
  remotes/origin/master
```

### 3 - Add Remote for your GitHub Fork

__Tous les membres de l'équipe__

Ajoutez un remote `me` :
```sh
$ git remote add me https://github.com/your-username/repository-name.git
# add the me remote

$ git remote -v
origin https://github.com/source-username/repository-name.git (fetch)
origin https://github.com/source-username/repository-name.git (push)
me https://github.com/your-username/repository-name.git (fetch)
me https://github.com/your-username/repository-name.git (push)
```

Vous devriez voir un remote `me` qui pointe vers votre dépôt GitHub Fork :
```sh
$ git remote show me
* remote me
  Fetch URL: https://github.com/your-username/repository-name.git
  Push  URL: https://github.com/your-username/repository-name.git
  HEAD branch: master
  Remote branches:
    develop new (next fetch will store in remotes/me)
    master  new (next fetch will store in remotes/me)
  Local ref configured for 'git push':
    master  pushes to master (up to date)
```

Les mainteneurs devront créer des branches et pousser directement vers le dépôt des sources.

Tous les membres de l'équipe devront extraire les changements du référentiel source afin de créer des branches pour les fonctionnalités.

Récupérez les données de la branche depuis le dépôt distant `origin` :
```sh
$ git fetch origin
From https://github.com/source-username/repository-name
* [new branch]      develop    -> origin/develop
* [new branch]      master     -> origin/master

$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/develop
  remotes/origin/master
  remotes/me/develop
  remotes/me/master
```

### 4 - Configurer les branches locales

__Tous les membres de l'équipe__

A ce stade, vous devriez avoir remarqué que vous n'avez pas de branche locale `develop`.
```sh
$ git branch
* master
```

Créez une branche `develop` qui suit la branche `develop` de `origin` :
```sh
$ git checkout -b develop --track origin/develop
Branch develop set up to track remote branch develop from origin
```

Remarquez que l'affichage des détails pour la branche distante `origin` indique que les branches locales `develop` et `master` sont configurées pour pousser vers et tirer depuis les branches du dépôt GitHub source :
```sh
$ git remote show origin
...
   Local branches configured for 'git pull':
     develop merges with remote develop
     master  merges with remote master
   Local branches configured for 'git push':
     develop pushes to develop (up to date)
     master  pushes to master (up to date)
```

:bulb: Le drapeau `-vv` pour la commande `git branch` montrera aussi les branches distantes qui sont suivies par vos branches locales (entre cochets) :
```sh
$ git branch -vv
* develop 3e03a92 [origin/develop] Create example app
  master  3e03a92 [origin/master] Create example app
```

Vous devriez maintenant être prêt à passer à la suite du guide. Si vous souhaitez voir le dépôt que vous avez créé sur votre machine locale dans le bureau GitHub, vous pouvez ajouter un dépôt en choisissant un chemin local.

## Next

Ensuite, nous allons suivre le processus de création de branches de fonctionnalités, de publication des modifications sur GitHub et de demande de fusion des modifications dans le référentiel source à l'aide d'une demande de reprise.

[Go](2-feature-branches.md)

## Quick Links

- [Readme](../readme.md)
- [2. Feature Branches](2-feature-branches.md)
- [3. Code Review](3-code-review.md)
- [4. Fetching Latest](4-fetching-latest.md)
- [5. Hotfix](5-hotfix.md)
- [6. Release Branch](6-release-branch.md)
- [7. Release Bugs](7-release-bugs.md)
- [8. Completed Release](8-completed-release.md)
