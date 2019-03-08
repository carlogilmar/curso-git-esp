# Comandos prácticos

Contenido:

* git status
* git diff
* git checkout
* git stash
* git reset
* Reescribir último commit
* Ignorar archivos

---

### git status

```bash
$ git status

En la rama master
Tu rama está actualizada con 'origin/master'.

nada para hacer commit, el árbol de trabajo está limpio
```

* Sólo responde en un repositorio de git
* Indica branch/rama del repositorio
* Estado en relación al historial del repositorio remoto \(si hay\)
* Archivos en el working directory

### git diff

Un commit conserva el estado de un archivo o grupo de archivos. Cuando este es modificado entonces cambia de estado, esta diferencia entre el estado inicial y el modificado puede ser detectada por git.

```
$ git status
En la rama master
Cambios no rastreados para el commit:
  (usa "git add 
<
archivo
>
..." para actualizar lo que será confirmado)
  (usa "git checkout --<archivo>
..." para descartar los cambios en el directorio de trabajo)

        modificado:     readme.md

sin cambios agregados al commit (usa "git add" y/o "git commit -a")

$ git diff readme.md

diff --git a/readme.md b/readme.md
index e69de29..0700af8 100644
--- a/readme.md
+++ b/readme.md
@@ -0,0 +1,6 @@
+Este es un ejemplo:
+- Lorem ipsum dolor sit amet, consectetur adipiscing elit.
+- Vivamus eget massa eu leo scelerisque facilisis eget nec felis.
+- Quisque sit amet enim ut diam molestie eleifend vitae at massa.
+- Suspendisse ut magna eget urna placerat feugiat.
+- Vivamus sed lacus dapibus, consectetur nibh at, sagittis est.
```

### git checkout

Con`git checkout -- archivo_modificado`es posible descartar las modificaciones en un archivo previamente versionado mediante un commit. No es posible rescatar esas modificaciones una vez descartadas.

```
$ git status

En la rama master
Cambios no rastreados para el commit:
  (usa "git add 
<
archivo
>
..." para actualizar lo que será confirmado)
  (usa "git checkout -- 
<
archivo
>
..." para descartar los cambios en el directorio de trabajo)

        modificado:     readme.md

sin cambios agregados al commit (usa "git add" y/o "git commit -a")

$ git checkout -- readme.md

$ git status

En la rama master
nada para hacer commit, el árbol de trabajo está limpio
```

### git stash

Git cuenta con una pila para guardar temporalmente modificaciones del working directory sin enviarlos necesariamente a stage. Estos cambios se pueden recuperar.

Guardar una modificación en working directory

```
$ git status

        modificado:     readme.md

$ git stash
Saved working directory and index state WIP on master: 7178862 Agregando archivo readme.md

$ git status
En la rama master
nada para hacer commit, el árbol de trabajo está limpio
```

Rescatando las modificaciones guardadas en el stash

```
$ git stash pop

En la rama master
Cambios no rastreados para el commit:
  (usa "git add <archivo> ..." para actualizar lo que será confirmado)
  (usa "git checkout -- <archivo> ..." para descartar los cambios en el directorio de trabajo)

        modificado:     readme.md

sin cambios agregados al commit (usa "git add" y/o "git commit -a")
Dropped refs/stash@{0} (2d2ee07c302d428406dd10a5a922ddae078cc559)
```

### git reset

Con este comando será posible deshacer commits previamente hechos.

```
$ git reset HEAD~1
```

* HEAD-1 es la referencia al último commit realizado \(HEAD-n, n=número de commits\)

Con la opción`--hard`se descartaran los cambios realizados

```
$ git reset --hard HEAD~1
```

### Reescribir último commit

```
$ git commit --amend -m "descripción a reescribir en el último commit realizado"
```

### Ignorar archivos

Se debe crear el archivo`.gitignore`para listar los archivos y carpetas que no serán necesarios bajo el control de versiones, este archivo **sí debe estar versionado.**

