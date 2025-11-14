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

# Réponces à la question 6 :
## Partie 1 :
il faut faire :
`git log` _(pour trouver le commit concerner)_
`git reset <commit-hash>` _(pour le suprimé)_

## Partie 2 :
La différance entre `git reset` et `git revert` est que `git reset` vas suprimer le commit concerné et ne l'aissera aucune trace de son existance ce qui peut posser problème pour les commits envoyés après.
Le `git revert`, quand à lui, va créé un commit d'annulation ce qui aurras pour effet que les commits envoyés avant la supression ne seront pas impactés et que l'historique conserveras sont intégrité.
Le choie entre `git reset` et `git revert` dépend donc de la trace que nous shouaitons concerver dans l'historique.















Si besoin, voici les commandes effectuer :

pacaud@FeuilleDePapier:~/évaluationgit$ git clone https://github.com/Emerick2/git-exam
Cloning into 'git-exam'...
remote: Enumerating objects: 10, done.
remote: Counting objects: 100% (10/10), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 10 (delta 1), reused 9 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (10/10), done.
Resolving deltas: 100% (1/1), done.
pacaud@FeuilleDePapier:~/évaluationgit$ git branch
fatal: not a git repository (or any of the parent directories): .git
pacaud@FeuilleDePapier:~/évaluationgit$ git status
fatal: not a git repository (or any of the parent directories): .git
pacaud@FeuilleDePapier:~/évaluationgit$ git status
fatal: not a git repository (or any of the parent directories): .git
pacaud@FeuilleDePapier:~/évaluationgit$ ls
git-exam
pacaud@FeuilleDePapier:~/évaluationgit$ cd git-exam/
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
go.mod  main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git log
commit 4bebcbc9c0f94016432d08c234bb5ea0893661fd (HEAD -> main, origin/main, origin/HEAD)
Author: baremy <remy.bamas@ynov.com>
Date:   Thu Oct 30 13:58:50 2025 +0100

    add branch main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
* main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add gitignore
fatal: pathspec 'gitignore' did not match any files
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git create .gitignore
git: 'create' is not a git command. See 'git --help'.

The most similar command is
        reset
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git create gitignore
git: 'create' is not a git command. See 'git --help'.

The most similar command is
        reset
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ code gitignore.git
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
gitignore.git  go.mod  main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add gitignore.git 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"ajout du gitignore exercice 1"
[main 0bc812e] ajout du gitignore exercice 1
 1 file changed, 2 insertions(+)
 create mode 100644 gitignore.git
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 16 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 332 bytes | 332.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/Emerick2/git-exam
   4bebcbc..0bc812e  main -> main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
* main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ code README.md
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add README.md 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"ajout du README avec erreur"
[main dd0c81c] ajout du README avec erreur
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 16 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 390 bytes | 390.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/Emerick2/git-exam
   0bc812e..dd0c81c  main -> main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch hotfix
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch hotfix
Switched to branch 'hotfix'
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
README.md  gitignore.git  go.mod  main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add README.md 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"correction du README"
[hotfix 1d201d4] correction du README
 1 file changed, 1 insertion(+), 1 deletion(-)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
fatal: The current branch hotfix has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin hotfix

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.

pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push --set-upstream origin hotfix
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 16 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 371 bytes | 371.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: 
remote: Create a pull request for 'hotfix' on GitHub by visiting:
remote:      https://github.com/Emerick2/git-exam/pull/new/hotfix
remote: 
To https://github.com/Emerick2/git-exam
 * [new branch]      hotfix -> hotfix
branch 'hotfix' set up to track 'origin/hotfix'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch hotfix
Your branch is up to date with 'origin/hotfix'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git merge hotfix 
Updating dd0c81c..1d201d4
Fast-forward
 README.md | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch feature-url
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-url
Switched to branch 'feature-url'
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ code PremièreFonctionnalité.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add première fonctionnalité
fatal: pathspec 'première' did not match any files
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add PremièreFonctionnalité.go 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"première fonctionnalité pour exercice 3 de la branche feature-url"
[feature-url 89b2655] première fonctionnalité pour exercice 3 de la branche feature-url
 1 file changed, 5 insertions(+)
 create mode 100644 "Premi\303\250reFonctionnalit\303\251.go"
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
fatal: The current branch feature-url has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin feature-url

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.

pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push --set-upstream origin feature-url
To https://github.com/Emerick2/git-exam
 ! [rejected]        feature-url -> feature-url (non-fast-forward)
error: failed to push some refs to 'https://github.com/Emerick2/git-exam'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
fatal: The current branch feature-url has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin feature-url

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.

pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch feature-url
nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
PremièreFonctionnalité.go  README.md  gitignore.git  go.mod  main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
* feature-url
  hotfix
  main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch dev 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev
Switched to branch 'dev'
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push --set-upstream origin dev
To https://github.com/Emerick2/git-exam
 ! [rejected]        dev -> dev (non-fast-forward)
error: failed to push some refs to 'https://github.com/Emerick2/git-exam'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch dev
nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git rebase feature-url 
Current branch dev is up to date.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
PremièreFonctionnalité.go  README.md  gitignore.git  go.mod  main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch dev
nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
fatal: The current branch dev has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin dev

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.

pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push --set-upstream origin dev
To https://github.com/Emerick2/git-exam
 ! [rejected]        dev -> dev (non-fast-forward)
error: failed to push some refs to 'https://github.com/Emerick2/git-exam'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
PremièreFonctionnalité.go  README.md  gitignore.git  go.mod  main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
* dev
  feature-url
  hotfix
  main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch develop 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch develop 
Switched to branch 'develop'
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push --set-upstream origin develop 

Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 16 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 384 bytes | 384.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'develop' on GitHub by visiting:
remote:      https://github.com/Emerick2/git-exam/pull/new/develop
remote: 
To https://github.com/Emerick2/git-exam
 * [new branch]      develop -> develop
branch 'develop' set up to track 'origin/develop'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
  dev
* develop
  feature-url
  hotfix
  main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch feature-color
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push --set-upstream origin feature-color 

Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
remote: 
remote: Create a pull request for 'feature-color' on GitHub by visiting:
remote:      https://github.com/Emerick2/git-exam/pull/new/feature-color
remote: 
To https://github.com/Emerick2/git-exam
 * [new branch]      feature-color -> feature-color
branch 'feature-color' set up to track 'origin/feature-color'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ code color.html
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ code main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch develop
Your branch is up to date with 'origin/develop'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   main.go

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        color.html

no changes added to commit (use "git add" and/or "git commit -a")
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add main.go color.html 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"ajout du changementd de couleur"
[develop f8f1432] ajout du changementd de couleur
 2 files changed, 10 insertions(+), 2 deletions(-)
 create mode 100644 color.html
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 16 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 516 bytes | 516.00 KiB/s, done.
Total 4 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/Emerick2/git-exam
   89b2655..f8f1432  develop -> develop
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch develop
Your branch is up to date with 'origin/develop'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ chmod +x ./script  
./fake-colleague.sh https://github.com/remybms/git-exam.git
chmod: cannot access './script': No such file or directory
bash: ./fake-colleague.sh: No such file or directory
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ chmod +x ./script  
./fake-colleague.sh https://github.com/remybms/git-exam.git
chmod: cannot access './script': No such file or directory
bash: ./fake-colleague.sh: No such file or directory
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$  chmod +x ./script  
./fake-colleague.sh https://github.com/Emerick2/git-exam.git
chmod: cannot access './script': No such file or directory
bash: ./fake-colleague.sh: No such file or directory
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git fetch
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git merge
Already up to date.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch develop
Your branch is up to date with 'origin/develop'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   main.go

no changes added to commit (use "git add" and/or "git commit -a")
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add main.go 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"la ligne pour l'exercice 4 à renvoyer une erreur donc le git fetch puis git merge n'ont pas eu d'erreur..."
[develop 39f05f5] la ligne pour l'exercice 4 à renvoyer une erreur donc le git fetch puis git merge n'ont pas eu d'erreur...
 1 file changed, 8 insertions(+)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 16 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 466 bytes | 466.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/Emerick2/git-exam
   f8f1432..39f05f5  develop -> develop
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev
Switched to branch 'dev'
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git merge feature-color
Already up to date.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch dev
nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
fatal: The current branch dev has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin dev

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.

pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
* dev
  develop
  feature-color
  feature-url
  hotfix
  main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git merge feature-color
Already up to date.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
PremièreFonctionnalité.go  README.md  gitignore.git  go.mod  main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-color 
Switched to branch 'feature-color'
Your branch is up to date with 'origin/feature-color'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
PremièreFonctionnalité.go  README.md  gitignore.git  go.mod  main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git log
commit 89b26557b44ffbbd6ec1d226cda91d5fce0a7e1c (HEAD -> feature-color, origin/feature-color, feature-url, dev)
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:16:58 2025 +0100

    première fonctionnalité pour exercice 3 de la branche feature-url

commit 1d201d41c80ba30b79c5d5f9f6dae223e355da6a (origin/hotfix, main, hotfix)
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:13:58 2025 +0100

    correction du README

commit dd0c81c6225322189e75c846baf619375b6129b9 (origin/main, origin/HEAD)
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:12:23 2025 +0100

    ajout du README avec erreur

commit 0bc812e27ca16d31a069ca860f4ae09c83cc2dfe
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:10:51 2025 +0100

    ajout du gitignore exercice 1

commit 4bebcbc9c0f94016432d08c234bb5ea0893661fd
Author: baremy <remy.bamas@ynov.com>
Date:   Thu Oct 30 13:58:50 2025 +0100

    add branch main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-color 
Already on 'feature-color'
Your branch is up to date with 'origin/feature-color'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch
fatal: missing branch or commit argument
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch feature-color
Your branch is up to date with 'origin/feature-color'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ code color.html
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch feature-color
Your branch is up to date with 'origin/feature-color'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   main.go

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        color.html

no changes added to commit (use "git add" and/or "git commit -a")
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add main.go color.html 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"je m'étais tromper de branche, désolé..."
[feature-color db210d6] je m'étais tromper de branche, désolé...
 2 files changed, 12 insertions(+), 2 deletions(-)
 create mode 100644 color.html
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"de nouveau pour l'exercice 4, je m'étais tromper de branche, désolé..."
On branch feature-color
Your branch is ahead of 'origin/feature-color' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 16 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 596 bytes | 596.00 KiB/s, done.
Total 4 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/Emerick2/git-exam
   89b2655..db210d6  feature-color -> feature-color
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
  dev
  develop
* feature-color
  feature-url
  hotfix
  main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch develop 
Switched to branch 'develop'
Your branch is up to date with 'origin/develop'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-color 
Switched to branch 'feature-color'
Your branch is up to date with 'origin/feature-color'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ chmod +x ./script
./fake-colleague.sh https://github.com/remybms/git-exam.git
chmod: cannot access './script': No such file or directory
bash: ./fake-colleague.sh: No such file or directory
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git fetch 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git merge
Already up to date.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev
Switched to branch 'dev'
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git merge feature-color 
Updating 89b2655..db210d6
Fast-forward
 color.html | 6 ++++++
 main.go    | 8 ++++++--
 2 files changed, 12 insertions(+), 2 deletions(-)
 create mode 100644 color.html
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
fatal: The current branch dev has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin dev

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.

pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch dev
nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git merge feature-url 
Already up to date.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git merge feature-color 
Already up to date.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch main 
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git fetch dev
fatal: 'dev' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git merge dev
Updating 1d201d4..db210d6
Fast-forward
 "Premi\303\250reFonctionnalit\303\251.go" | 5 +++++
 color.html                                | 6 ++++++
 main.go                                   | 8 ++++++--
 3 files changed, 17 insertions(+), 2 deletions(-)
 create mode 100644 "Premi\303\250reFonctionnalit\303\251.go"
 create mode 100644 color.html
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch main
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/Emerick2/git-exam
   dd0c81c..db210d6  main -> main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
  dev
  develop
  feature-color
  feature-url
  hotfix
* main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev
Switched to branch 'dev'
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch dev
nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch develop 
Switched to branch 'develop'
Your branch is up to date with 'origin/develop'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status 
On branch develop
Your branch is up to date with 'origin/develop'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-color 
Switched to branch 'feature-color'
Your branch is up to date with 'origin/feature-color'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status 
On branch feature-color
Your branch is up to date with 'origin/feature-color'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-url 
Switched to branch 'feature-url'
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status 
On branch feature-url
nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
fatal: The current branch feature-url has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin feature-url

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.

pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push --set-upstream origin feature-url

To https://github.com/Emerick2/git-exam
 ! [rejected]        feature-url -> feature-url (non-fast-forward)
error: failed to push some refs to 'https://github.com/Emerick2/git-exam'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch hotfix 
Switched to branch 'hotfix'
Your branch is up to date with 'origin/hotfix'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status 
On branch hotfix
Your branch is up to date with 'origin/hotfix'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status 
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add README.md 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-color 
M       README.md
Switched to branch 'feature-color'
Your branch is up to date with 'origin/feature-color'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch feature-color
Your branch is up to date with 'origin/feature-color'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md

pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch main
M       README.md
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md

pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
Everything up-to-date
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ^C
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"modification alléatoire du fichier READMI pour l'exercice 6"
[main cd26866] modification alléatoire du fichier READMI pour l'exercice 6
 1 file changed, 3 insertions(+), 1 deletion(-)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 16 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 404 bytes | 404.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/Emerick2/git-exam
   db210d6..cd26866  main -> main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-color 
Switched to branch 'feature-color'
Your branch is up to date with 'origin/feature-color'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
PremièreFonctionnalité.go  color.html     go.mod
README.md                  gitignore.git  main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ chmod +x ./main.go  
./fake-colleague.sh https://github.com/remybms/git-exam.git
bash: ./fake-colleague.sh: No such file or directory
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ chmod +x ./main  
./fake-colleague.sh https://github.com/remybms/git-exam.git
chmod: cannot access './main': No such file or directory
bash: ./fake-colleague.sh: No such file or directory
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ chmod +x ./main  
chmod: cannot access './main': No such file or directory
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ chmod +x ./main  chmod +x ./main
./fake-colleague.sh https://github.com/remybms/git-exam
chmod: cannot access './main': No such file or directory
chmod: cannot access 'chmod': No such file or directory
chmod: cannot access '+x': No such file or directory
chmod: cannot access './main': No such file or directory
bash: ./fake-colleague.sh: No such file or directory
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ chmod +x ./main.go
./fake-colleague.sh https://github.com/remybms/git-exam
bash: ./fake-colleague.sh: No such file or directory
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ chmod +x ./main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ./fake-colleague.sh https://github.com/remybms/git-exam
bash: ./fake-colleague.sh: No such file or directory
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ./fake-colleague.sh https://github.com/remybms/git-exam.git
bash: ./fake-colleague.sh: No such file or directory
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ./fake-colleague.sh https://github.com/Emerick2/git-exam
bash: ./fake-colleague.sh: No such file or directory
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ./fake-colleague.sh https://github.com/Emerick2/git-exam.git
bash: ./fake-colleague.sh: No such file or directory
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ code ake-colleague.sh
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ./fake-colleague.sh https://github.com/remybms/git-exam
bash: ./fake-colleague.sh: No such file or directory
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ./fake-colleague.sh https://github.com/Emerick2/git-exam.git
bash: ./fake-colleague.sh: No such file or directory
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git merge
Already up to date.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ./fake-colleague.sh https://github.com/remybms/git-exam
bash: ./fake-colleague.sh: Permission denied
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ./fake-colleague.sh https://github.com/Emerick2/git-exam.git
bash: ./fake-colleague.sh: Permission denied
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add fake-colleague.sh 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"tentative de création du fake-colleagues mais j'ai un 'Permission denied'"
[feature-color 8772784] tentative de création du fake-colleagues mais j'ai un 'Permission denied'
 1 file changed, 1 insertion(+)
 create mode 100644 fake-colleague.sh
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 16 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 378 bytes | 378.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/Emerick2/git-exam
   db210d6..8772784  feature-color -> feature-color
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch main
M       main.go
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   main.go

no changes added to commit (use "git add" and/or "git commit -a")
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git log
commit cd26866a1f0ed098685dff9b51d5916c75f11d6d (HEAD -> main, origin/main, origin/HEAD)
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:56:48 2025 +0100

    modification alléatoire du fichier READMI pour l'exercice 6

commit db210d6debd7a309a5d492d72f81acecb75bf7c2 (dev)
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:41:49 2025 +0100

    je m'étais tromper de branche, désolé...

commit 89b26557b44ffbbd6ec1d226cda91d5fce0a7e1c (feature-url)
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:16:58 2025 +0100

    première fonctionnalité pour exercice 3 de la branche feature-url

commit 1d201d41c80ba30b79c5d5f9f6dae223e355da6a (origin/hotfix, hotfix)
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:13:58 2025 +0100

    correction du README

commit dd0c81c6225322189e75c846baf619375b6129b9
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:12:23 2025 +0100

    ajout du README avec erreur

commit 0bc812e27ca16d31a069ca860f4ae09c83cc2dfe
Author: pemerick <emerick.pacaud@ynov.com>
:
commit cd26866a1f0ed098685dff9b51d5916c75f11d6d (HEAD -> main, origin/main, origin/HEAD)
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:56:48 2025 +0100

    modification alléatoire du fichier READMI pour l'exercice 6

commit db210d6debd7a309a5d492d72f81acecb75bf7c2 (dev)
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:41:49 2025 +0100

    je m'étais tromper de branche, désolé...

commit 89b26557b44ffbbd6ec1d226cda91d5fce0a7e1c (feature-url)
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:16:58 2025 +0100

    première fonctionnalité pour exercice 3 de la branche feature-url

commit 1d201d41c80ba30b79c5d5f9f6dae223e355da6a (origin/hotfix, hotfix)
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:13:58 2025 +0100

    correction du README

commit dd0c81c6225322189e75c846baf619375b6129b9
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:12:23 2025 +0100

    ajout du README avec erreur

commit 0bc812e27ca16d31a069ca860f4ae09c83cc2dfe
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:10:51 2025 +0100

    ajout du gitignore exercice 1

commit 4bebcbc9c0f94016432d08c234bb5ea0893661fd
Author: baremy <remy.bamas@ynov.com>
Date:   Thu Oct 30 13:58:50 2025 +0100

    add branch main
(END)
Date:   Fri Nov 14 10:41:49 2025 +0100

    je m'étais tromper de branche, désolé...

commit 89b26557b44ffbbd6ec1d226cda91d5fce0a7e1c (feature-url)
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:16:58 2025 +0100

    première fonctionnalité pour exercice 3 de la branche feature-url

commit 1d201d41c80ba30b79c5d5f9f6dae223e355da6a (origin/hotfix, hotfix)
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:13:58 2025 +0100

    correction du README

commit dd0c81c6225322189e75c846baf619375b6129b9
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:12:23 2025 +0100

    ajout du README avec erreur

commit 0bc812e27ca16d31a069ca860f4ae09c83cc2dfe
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:10:51 2025 +0100

    ajout du gitignore exercice 1

commit 4bebcbc9c0f94016432d08c234bb5ea0893661fd
Author: baremy <remy.bamas@ynov.com>
Date:   Thu Oct 30 13:58:50 2025 +0100

    add branch main
...skipping...

    je m'étais tromper de branche, désolé...

commit 89b26557b44ffbbd6ec1d226cda91d5fce0a7e1c (feature-url)
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:16:58 2025 +0100

    première fonctionnalité pour exercice 3 de la branche feature-url

commit 1d201d41c80ba30b79c5d5f9f6dae223e355da6a (origin/hotfix, hotfix)
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:13:58 2025 +0100

    correction du README

commit dd0c81c6225322189e75c846baf619375b6129b9
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:12:23 2025 +0100

    ajout du README avec erreur

commit 0bc812e27ca16d31a069ca860f4ae09c83cc2dfe
Author: pemerick <emerick.pacaud@ynov.com>
Date:   Fri Nov 14 10:10:51 2025 +0100

    ajout du gitignore exercice 1

commit 4bebcbc9c0f94016432d08c234bb5ea0893661fd
Author: baremy <remy.bamas@ynov.com>
Date:   Thu Oct 30 13:58:50 2025 +0100

    add branch main



--- La j'ai du tué le terminal et le relancer





pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
        modified:   main.go

no changes added to commit (use "git add" and/or "git commit -a")
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
        modified:   main.go

no changes added to commit (use "git add" and/or "git commit -a")
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
        modified:   main.go

no changes added to commit (use "git add" and/or "git commit -a")
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
        modified:   main.go

no changes added to commit (use "git add" and/or "git commit -a")
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add README.md 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"ajout de la réponce à la partie 2 de la question 6"
[main 5c65b48] ajout de la réponce à la partie 2 de la question 6
 1 file changed, 875 insertions(+), 1 deletion(-)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 16 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 4.49 KiB | 4.49 MiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/Emerick2/git-exam
   cd26866..5c65b48  main -> main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git reset dd0c81c6225322189e75c846baf619375b6129b9
Unstaged changes after reset:
M       README.md
M       main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
To https://github.com/Emerick2/git-exam
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'https://github.com/Emerick2/git-exam'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git reset cd26866a1f0ed098685dff9b51d5916c75f11d6d
Unstaged changes after reset:
M       README.md
M       color.html
M       main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch main
Your branch is behind 'origin/main' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
        modified:   main.go

no changes added to commit (use "git add" and/or "git commit -a")
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add README.md main.go 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"suppression de la modification alléatoire avec l'utilisation de git reset  cd26866a1f0ed098685dff9b51d5916c75f11d6d"
[main a7b9b06] suppression de la modification alléatoire avec l'utilisation de git reset  cd26866a1f0ed098685dff9b51d5916c75f11d6d
 2 files changed, 878 insertions(+), 1 deletion(-)
 mode change 100644 => 100755 main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
To https://github.com/Emerick2/git-exam
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'https://github.com/Emerick2/git-exam'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch main
Your branch and 'origin/main' have diverged,
and have 1 and 1 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ^C
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git tag v0.3
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push v0.3
fatal: 'v0.3' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch main
Your branch and 'origin/main' have diverged,
and have 1 and 1 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
To https://github.com/Emerick2/git-exam
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'https://github.com/Emerick2/git-exam'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
  dev
  develop
  feature-color
  feature-url
  hotfix
* main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev
Switched to branch 'dev'
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch dev
nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch dev
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   color.html

no changes added to commit (use "git add" and/or "git commit -a")
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add color.html 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"Modification pour m'assurer que la branche est bien sur le commit distant"
[dev 931918d] Modification pour m'assurer que la branche est bien sur le commit distant
 1 file changed, 2 insertions(+), 2 deletions(-)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
fatal: The current branch dev has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin dev

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.

pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push --set-upstream origin dev
To https://github.com/Emerick2/git-exam
 ! [rejected]        dev -> dev (non-fast-forward)
error: failed to push some refs to 'https://github.com/Emerick2/git-exam'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push --set-upstream origin dev


To https://github.com/Emerick2/git-exam
 ! [rejected]        dev -> dev (non-fast-forward)
error: failed to push some refs to 'https://github.com/Emerick2/git-exam'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch branche
fatal: invalid reference: branche
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev
Already on 'dev'
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch -M dev2
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev
branch 'dev' set up to track 'origin/dev'.
Switched to a new branch 'dev'
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch dev
Your branch is up to date with 'origin/dev'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
color.html  go.mod  main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch -M dev3
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev2
error: The following untracked working tree files would be overwritten by checkout:
        color.html
Please move or remove them before you switch branches.
Aborting
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev
branch 'dev' set up to track 'origin/dev'.
Switched to a new branch 'dev'
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
color.html  go.mod  main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch dev
Your branch is up to date with 'origin/dev'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   main.go

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        color.html

no changes added to commit (use "git add" and/or "git commit -a")
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
* dev
  dev2
  dev3
  develop
  feature-color
  feature-url
  hotfix
  main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch develop 
error: The following untracked working tree files would be overwritten by checkout:
        color.html
Please move or remove them before you switch branches.
Aborting
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch dev
Your branch is up to date with 'origin/dev'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        color.html

nothing added to commit but untracked files present (use "git add" to track)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-color 
error: The following untracked working tree files would be overwritten by checkout:
        color.html
Please move or remove them before you switch branches.
Aborting
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-color 
error: The following untracked working tree files would be overwritten by checkout:
        color.html
Please move or remove them before you switch branches.
Aborting
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch dev
Your branch is up to date with 'origin/dev'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        color.html

nothing added to commit but untracked files present (use "git add" to track)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-color 
error: The following untracked working tree files would be overwritten by checkout:
        color.html
Please move or remove them before you switch branches.
Aborting
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
* dev
  dev2
  dev3
  develop
  feature-color
  feature-url
  hotfix
  main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-url 
Switched to branch 'feature-url'
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch feature-url
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        color.html

nothing added to commit but untracked files present (use "git add" to track)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch hotfix 
Switched to branch 'hotfix'
Your branch is up to date with 'origin/hotfix'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch hotfix
Your branch is up to date with 'origin/hotfix'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        color.html

nothing added to commit but untracked files present (use "git add" to track)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-url
Switched to branch 'feature-url'
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch -M feature-color2
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
  dev
  dev2
  dev3
  develop
  feature-color
* feature-color2
  hotfix
  main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-color
error: The following untracked working tree files would be overwritten by checkout:
        color.html
Please move or remove them before you switch branches.
Aborting
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch -M feature-
url2
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
  dev
  dev2
  dev3
  develop
  feature-color
* feature-url2
  hotfix
  main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add README.md 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"J'ai créé une branche alors qu'elle existais déjà, donc la vrais branche, ces la 2..."
[feature-url2 13063fe] J'ai créé une branche alors qu'elle existais déjà, donc la vrais branche, ces la 2...
 1 file changed, 13 insertions(+), 1 deletion(-)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
fatal: The current branch feature-url2 has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin feature-url2

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.

pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push --set-upstream origin feature-url2
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 16 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 412 bytes | 412.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'feature-url2' on GitHub by visiting:
remote:      https://github.com/Emerick2/git-exam/pull/new/feature-url2
remote: 
To https://github.com/Emerick2/git-exam
 * [new branch]      feature-url2 -> feature-url2
branch 'feature-url2' set up to track 'origin/feature-url2'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev
Switched to branch 'dev'
Your branch is up to date with 'origin/dev'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
color.html  go.mod  main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status 
On branch dev
Your branch is up to date with 'origin/dev'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        color.html

nothing added to commit but untracked files present (use "git add" to track)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev2
error: The following untracked working tree files would be overwritten by checkout:
        color.html
Please move or remove them before you switch branches.
Aborting
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev3
Switched to branch 'dev3'
Your branch is up to date with 'origin/dev'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch dev3
Your branch is up to date with 'origin/dev'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        color.html

nothing added to commit but untracked files present (use "git add" to track)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
color.html  go.mod  main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev
Switched to branch 'dev'
Your branch is up to date with 'origin/dev'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
color.html  go.mod  main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev2
error: The following untracked working tree files would be overwritten by checkout:
        color.html
Please move or remove them before you switch branches.
Aborting
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev2
error: The following untracked working tree files would be overwritten by checkout:
        color.html
Please move or remove them before you switch branches.
Aborting
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git stsh
git: 'stsh' is not a git command. See 'git --help'.

The most similar command is
        stash
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git stash
No local changes to save
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev2
error: The following untracked working tree files would be overwritten by checkout:
        color.html
Please move or remove them before you switch branches.
Aborting
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch dev
Your branch is up to date with 'origin/dev'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        color.html

nothing added to commit but untracked files present (use "git add" to track)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add color.html 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"J'essaye toujours de résoudre le problèmes des branches créé en trop..."
[dev 51d31a1] J'essaye toujours de résoudre le problèmes des branches créé en trop...
 1 file changed, 6 insertions(+)
 create mode 100644 color.html
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 16 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 452 bytes | 452.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/Emerick2/git-exam
   84ced84..51d31a1  dev -> dev
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev2
Switched to branch 'dev2'
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
PremièreFonctionnalité.go  color.html     go.mod
README.md                  gitignore.git  main.go
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch dev2
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   main.go

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fake-colleague.sh

no changes added to commit (use "git add" and/or "git commit -a")
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add main.go fake-colleague.sh 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"La branche dev utilisé était la branche dev2"
[dev2 636698d] La branche dev utilisé était la branche dev2
 2 files changed, 11 insertions(+)
 create mode 100644 fake-colleague.sh
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
fatal: The current branch dev2 has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin dev2

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.

pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push --set-upstream origin dev2
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 16 threads
Compressing objects: 100% (7/7), done.
Writing objects: 100% (7/7), 808 bytes | 404.00 KiB/s, done.
Total 7 (delta 4), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (4/4), completed with 3 local objects.
remote: 
remote: Create a pull request for 'dev2' on GitHub by visiting:
remote:      https://github.com/Emerick2/git-exam/pull/new/dev2
remote: 
To https://github.com/Emerick2/git-exam
 * [new branch]      dev2 -> dev2
branch 'dev2' set up to track 'origin/dev2'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
  dev
* dev2
  dev3
  develop
  feature-color
  feature-url2
  hotfix
  main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-color 
Switched to branch 'feature-color'
Your branch is up to date with 'origin/feature-color'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ ls
PremièreFonctionnalité.go  color.html         gitignore.git  main.go
README.md                  fake-colleague.sh  go.mod
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch feature-color
Your branch is up to date with 'origin/feature-color'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git add main.go 
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git commit -m"Je vérigie que toutes les branches soit bien envoyées"
[feature-color e376ae9] Je vérigie que toutes les branches soit bien envoyées
 1 file changed, 10 insertions(+)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 16 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 387 bytes | 387.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/Emerick2/git-exam
   8772784..e376ae9  feature-color -> feature-color
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch dev2
Switched to branch 'dev2'
Your branch is up to date with 'origin/dev2'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch dev2
Your branch is up to date with 'origin/dev2'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch develop 
Switched to branch 'develop'
Your branch is up to date with 'origin/develop'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch develop
Your branch is up to date with 'origin/develop'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
  dev
  dev2
  dev3
* develop
  feature-color
  feature-url2
  hotfix
  main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-color 
Switched to branch 'feature-color'
Your branch is up to date with 'origin/feature-color'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch feature-color
Your branch is up to date with 'origin/feature-color'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-url2
Switched to branch 'feature-url2'
Your branch is up to date with 'origin/feature-url2'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch feature-url2
Your branch is up to date with 'origin/feature-url2'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch hotfix 
Switched to branch 'hotfix'
Your branch is up to date with 'origin/hotfix'.
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch hotfix
Your branch is up to date with 'origin/hotfix'.

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch main
Switched to branch 'main'
Your branch and 'origin/main' have diverged,
and have 1 and 1 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch main
Your branch and 'origin/main' have diverged,
and have 1 and 1 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

nothing to commit, working tree clean
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git branch
  dev
  dev2
  dev3
  develop
  feature-color
  feature-url2
  hotfix
* main
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git switch feature-url
error: Your local changes to the following files would be overwritten by checkout:
        README.md
Please commit your changes or stash them before you switch branches.
Aborting
pacaud@FeuilleDePapier:~/évaluationgit/git-exam$ git status
On branch main
Your branch and 'origin/main' have diverged,
and have 1 and 1 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")