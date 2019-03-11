# Reestructuración de un branch: Git Rebase

Contenido:

* Rebase de branches
* Rebase por commits
* Cherry-pick
* Revert
* Reflog

[Visualizing](http://git-school.github.io/visualizing-git/#free)

### Merge vs Rebase branches

Merge![](/assets/rebase1.png)Rebase ![](/assets/rebase2.png)El uso del rebase puede ocasionar conflictos que necesitarán ser ajustados manualmente

```
$ git rebase master
En primer lugar, rebobinando HEAD para después reproducir tus cambios encima de ésta...
Aplicando: coding FS-456  adding binnacle and auth in all routes
Aplicando: coding FS-462  addin sending to broker
Aplicando: FS-464 Adding function for set dates per division

Resolve all conflicts manually, mark them as resolved with
"git add/rm <conflicted_files>", then run "git rebase --continue".
You can instead skip this commit: run "git rebase --skip".
To abort and get back to the state before "git rebase", run "git rebase --abort".
```

Opciones de git rebase cuando ocurren conflictos:

* Si se soluciona el conflicto, la delta se deberá agregar a stage, y continuar con el rebase **git  rebase --continue**
* Para cancelar el rebase: **git rebase --abort**
* Para ignorar el conflicto: **git rebase --skip**

### Rebase Interactive: rebasando commits

Para esto se necesitará ubicar la referencia de un commit pasado:

```
$ git rebase -i <hash-del-commit>

pick dd24824 commit 3
pick 573db4e commit 4
pick d12a348 commit 5

# Rebase 49a3b55..d12a348 en 49a3b55 (3 comandos)
#
# Comandos:
# p, pick <commit> = usar commit
# r, reword <commit> = usar commit, pero editar el mensaje de commit
# e, edit <commit> = usar commit, pero parar para un amend
# s, squash <commit> = usar commit, pero fusionarlo en el commit previo
# f, fixup <commit> = como "squash", pero descarta el mensaje del log de este commit
# x, exec <commit> = ejecuta comando ( el resto de la línea) usando un shell
# b, break = parar aquí (continuar rebase luego con 'git rebase --continue')
# d, drop <commit> = eliminar commit
# l, label <label> = poner label al HEAD actual con un nombre
# t, reset <label> = reiniciar HEAD a el label
# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
```

Al usar esta opción entraremos al editor por defecto \(VIM\) y desde ahí tendremos que modificar la referencia a cada commit en función de lo que necesitemos realizar.

* Reescribir las referencias de un commit
* Squash de un grupo de commits

* Eliminar commits

### Copiar un commit de un branch a otro: cherry-pick

```
$ git cherry-pick <commit>
```

![](/assets/cherry1.png)![](/assets/cherry2.png)

### Revirtiendo cambios

```
$ git revert <commit>
```

### ![](/assets/revert.png)

### Git reflog

Es la herramienta que guarda el histórico de operaciones efectuadas sobre los branches del proyecto

```
$ git reflog 

26a53e4 (HEAD -> feature/3, feature/recover) HEAD@{0}: rebase finished: refs/heads/feature/3 onto 26a53e40a204a94ff6bfeada22c57d786b23ce39
d12a348 (recover-branch, master) HEAD@{1}: rebase:
26a53e4 (HEAD -> feature/3, feature/recover) HEAD@{2}: rebase: checkout feature/recover
d12a348 (recover-branch, master) HEAD@{3}: checkout: moving from feature/recover to feature/3
26a53e4 (HEAD -> feature/3, feature/recover) HEAD@{4}: checkout: moving from 26a53e40a204a94ff6bfeada22c57d786b23ce39 to feature/recover
26a53e4 (HEAD -> feature/3, feature/recover) HEAD@{5}: checkout: moving from feature/3 to 26a53e4
d12a348 (recover-branch, master) HEAD@{6}: checkout: moving from d12a3482af7be4e1c2740abe600ffd586014c543 to feature/3
d12a348 (recover-branch, master) HEAD@{7}: checkout: moving from feature/3 to HEAD@{0}
d12a348 (recover-branch, master) HEAD@{8}: reset: moving to HEAD@{0}
d12a348 (recover-branch, master) HEAD@{9}: reset: moving to d12a348
ce61f73 (feature/2) HEAD@{10}: checkout: moving from feature/2 to feature/3
ce61f73 (feature/2) HEAD@{11}: revert: Revert "Commit 7"
26a53e4 (HEAD -> feature/3, feature/recover) HEAD@{12}: commit: Commit 7
01fa5cd HEAD@{13}: commit: Commit 6
```







