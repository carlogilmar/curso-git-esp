# Nociones básicas de git

Contenido:

* Sobre git
* Creación de un repositorio
* DAG y Git Objects
* Áreas de Git
* Working Directory
* Stage Area \( add \)
* Local repository \( commit \)
* Log de git

---

Sobre git:

* Creado por Linus Torvalds en 2005
* Es un sistema de archivos
* Internamente implementa un **Grafo Acíclico Dirigido** DAG
* Es un sistema de control de versiones distribuido

Animaciones de git:

* [Git](https://www.youtube.com/watch?v=jHzbLNVhv-c )
* [Linux](https://www.youtube.com/watch?v=5iFnzr73XXk&t=4686s)

### Creación de un repositorio

```
$ mkdir my_project

$ git init
Inicializado repositorio Git vacío en /Users/carlogilmar/Desktop/prueba/.git/
```

Para eliminar el repositorio de git de un directorio sólo basta con borrar la carpeta _.git_

### DAG y Git Objects

```
$ tree -L 3 .git
.git
├── HEAD
├── config
├── description
├── hooks
│   ├── applypatch-msg.sample
│   ├── commit-msg.sample
│   ├── fsmonitor-watchman.sample
│   ├── post-update.sample
│   ├── pre-applypatch.sample
│   ├── pre-commit.sample
│   ├── pre-push.sample
│   ├── pre-rebase.sample
│   ├── pre-receive.sample
│   ├── prepare-commit-msg.sample
│   └── update.sample
├── info
│   └── exclude
├── objects
│   ├── info
│   └── pack
└── refs
    ├── heads
    └── tags

8 directories, 15 files
```

### Áreas de Git

1. Working Directory
2. Stage Area
3. Local Repository
4. Remote Repository

![](/assets/chapter2_1.png)

```
$ git status
```

### Working Directory

![](/assets/chapter2_2.png)

Cualquier archivo creado dentro del repositorio estará en el _working directory_

```
$ touch readme.md
$ git status
En la rama master

No hay commits todavía

Archivos sin seguimiento:
  (usa "git add <archivo>..." para incluirlo a lo que se será confirmado)

        readme.md

no hay nada agregado al commit pero hay archivos sin seguimiento presentes (usa "git add" para hacerles seguimiento)
```

El branch/rama _master_ es el nombre de la línea temporal por defecto de cualquier repositorio de git.

### Stage Area \( add \)

![](/assets/chapter2_3.png)

```
$ git add readme.md
En la rama master

No hay commits todavía

Cambios a ser confirmados:
  (usa "git rm --cached <archivo>..." para sacar del área de stage)

        nuevo archivo:  readme.md
```

### Local repository \( commit \)

![](/assets/chapter2_4.png)

```
$ git commit -m "Agregando archivo readme.md"
[master (commit-raíz) 7178862] Agregando archivo readme.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 readme.md

$ git status
En la rama master
nada para hacer commit, el árbol de trabajo está limpio
```

### Log de git

![](/assets/chapter2_5.png)

```
$ git log
commit 71788626f945c88a1c9ad00b28bc95d936bee63e (HEAD -> master)
Author: carlogilmar <carlogilmar12@gmail.com>
Date:   Fri Feb 22 23:12:26 2019 -0600

    Agregando archivo readme.md
```

## Resumen de comandos básicos

#### Inicializar repositorio de git

```
$ git init
```

#### Ver el status del repositorio

```
$ git status
```

#### Agregar uno o varios archivos del working directory a stage

```
$ git add nombre_del_archivo

$ git add archivo1 archivo2 archivo3 archivo4
```

#### Regresar un archivo de stage al working directory

```
$ git checkout -- archivo_en_stage
```

#### Agregar un archivo de stage a local repository

```
$ git commit -m "descripción breve"
```

* `-m` esta opción habilita la descripción breve, sin ella se abrirá el editor por defecto

#### Ver el log del local repository

```
$ git log
```



