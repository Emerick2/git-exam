deux fonctionnalités

# À lire au début :
Je me suis tromper durant la réalisation de l'évaluation, puisque je ne voyais pas les branches existantes en fesant git branch j'ai créé des copies de branche alors que je n'aurais pas du...
Pour rendre la lecture un peut plus facile j'ai renomer les branche pour rendre le parcours un peut plus facile à suivre, voici donc les branches utiliser :
- dev2
- develop
- feature-color
- feature-url2
- hotfix
- main

  ;
# Réponces à la question 6 :
## Partie 1 :
il faut faire :
`git log` _(pour trouver le commit concerner)_
`git reset <commit-hash>` _(pour le suprimé)_

## Partie 2 :
La différance entre `git reset` et `git revert` est que `git reset` vas suprimer le commit concerné et ne l'aissera aucune trace de son existance ce qui peut posser problème pour les commits envoyés après.
Le `git revert`, quand à lui, va créé un commit d'annulation ce qui aurras pour effet que les commits envoyés avant la supression ne seront pas impactés et que l'historique conserveras sont intégrité.
Le choie entre `git reset` et `git revert` dépend donc de la trace que nous shouaitons concerver dans l'historique.
