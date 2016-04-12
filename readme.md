Al finalizar el punto **10)**, la situación es:

27754bc HEAD@{0}: reset: moving to HEAD~1

deb6186 HEAD@{1}: commit: #2 Subida git-nuestro.md al repositorio, rama styled

27754bc HEAD@{2}: checkout: moving from master to styled

27754bc HEAD@{3}: commit (initial): #1 Subida git-nuestro.md al repositorio

**11)** **git reset --hard HEAD~1**
porque he utilizado la directiva --hard para descartar los cambios realizados en el fichero *git-nuestro.md*

**12)** **git reflog + git reset deb6186**
porque reset mueve la rama `styled` al puntero del último commit que nos interesa

**13)** **No, el merge no generó ningún conflicto**, *Already up-to-date*. La rama `styled` ya contiene todos los cambios de la `master` y está en la misma línea. Además, al haber hecho --hard al mover la rama, produce que la working copy quede como antes del commit y por eso el mensaje de *Already up-to-date*. 
Al intentar hacer un *git checkout master*, te avisa de que hay cambios que puedes perder y aparece el mensaje ***Please, commit your changes or stash them before you can switch branches.
Aborting***. Por eso, otra opción hubiera sido rehacer el commit con git stash + git checkout

**19)** **Sí, el merge generó conflictos**, porque *git-nuestro.md* ha sido cambiado en dos ramas diferentes, y en esos casos hay que tomar una decisión

**21)** **No, el merge no generó ningún conflicto**, 

git merge styled

Updating 27754bc..e8dc8d4

Fast-forward
 git-nuestro.md | 19 +++++++++----------
 1 file changed, 9 insertions(+), 10 deletions(-)

Porque es un merge fast-forward de dos ramas en la misma línea, se mueve el puntero HEAD -> `master`, se ve claramente en sourcetree

**25)** **git log --graph**

**26)** **Sí, podria ser fast-forward**, ya que están en la misma línea y bastaría colocar HEAD de `master` apuntando a la rama `title` absorbiendo el cambio del título de la rama `title`

**27)** **git reset HEAD@{1}**

Unstaged changes after reset:

M	git-nuestro.md

No es --hard y selecciona HEAD@{1}. Entiendo que se podría haber hecho también **git reset [puntero del checkout title->master]**

**28)** **git stash**, el mensaje devuelto es:

*Saved working directory and index state WIP on master: e8dc8d4 Merge branch 'htmlify' into styled
HEAD is now at e8dc8d4 Merge branch 'htmlify' into styled*

**29)** **git branch -D title**

Deleted branch title (was bfae145).

**30)** **git reset HEAD@{3}**

Unstaged changes after reset:
M	git-nuestro.md

**32)** **git checkout 27754bc**
Note: checking out '27754bc'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at 27754bc... #1 Subida git-nuestro.md al repositorio

También con **git checkout 27754bcc3bf78be7b7a343ad5f1fdfd0004dc9e3**
siendo:

commit 27754bcc3bf78be7b7a343ad5f1fdfd0004dc9e3

Author: jacobo enriquez gabeiras <michi_two@yahoo.com>

Date:   Mon Apr 11 20:01:16 2016 +0200

    #1 Subida git-nuestro.md al repositorio

**33)** **git checkout master**