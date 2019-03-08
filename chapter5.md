# Repositorios Remotos: GitHub

![](/assets/github2.png)Contenido:

* Sobre GitHub
* Áreas de git
* Sincronizar un repositorio local en un repositorio remoto
* Git para repositorios remotos
* Submódulos

---

### ![](/assets/github1.png)Servicios de GitHub

* Plataforma de control de versiones
* Ecosistema Open Source
* Administración de tableros
* Proyectos públicos
  * Código y edición manual
  * Sintaxis markdown 
  * Inspección de elementos de git: commits, branches, releases y contributors. 
  * Issues
  * Pull requests
  * **Actions**
  * Proyectos/Tableros
  * Wiki
  * Insights 
  * GitHub Pages

[GitHub Enterprise](https://github.com/enterprise)

[GitHub Learning Lab](https://lab.github.com/)

[GitHub Cheat Sheet about git](https://services.github.com/on-demand/downloads/github-git-cheat-sheet.pdf)

[Markdown syntax ](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

[GitHub Education](https://education.github.com/)

[Git Large File Storage](https://git-lfs.github.com/)

[Git Secret](https://git-secret.io/)

### Áreas de git![](/assets/github3.png)

### Sincronizar un repositorio local en un repositorio remoto

Crear un nuevo repositorio en GitHub![](/assets/github4.png)Al crearlo nos dará las siguientes opciones:![](/assets/github5.png) 

GitHub nos ofrece las opciones siguientes:

* or create a new repository on the command line
* or push an existing repository from the command line
* or import code from another repository

Por ahora solo necesitamos incluir la URL del repositorio remoto creado anteriormente en nuestro proyecto local 

* **URL por SSH**: necesitaremos generar y dar de alta nuestra llave SSH en GitHub para poder usar esta opción
* **URL por HTTPS**: nos pedirá una confirmación de usuario y contraseña de GitHub cada vez que efectuemos alguna operación.

#### SSH

[Guía para dar de alta llave ssh ](https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) 

Crear la llave si no existe, y dar de alta en **Settings / New SSH Key**![](/assets/github6.png)

#### Agregar la URL del repositorio remoto

1. Copiar la URL por SSH o HTTPS \(se recomienda SSH\)![](/assets/github7.png)
2. En el proyecto local se necesita dar de alta 

```
$ git remote add origin <url-del-repositorio-remoto>
```

Este comando consta de 2 directivas: **origin** y la **url del repositorio remoto. **

**Origin** será el tag con el que identificaremos la url, y es un parámetro obligatorio. Esto quiere decir que es posible agregar múltiples urls de diferentes repositorios remotos en diferentes plataformas. 

3. Comprobar la url

```
$ git remote -v

origin	git@github.com:carlogilmar/prueba.git (fetch)
origin	git@github.com:carlogilmar/prueba.git (push)

```

### Git para repositorios remotos![](/assets/github9.png)

#### git push 

Para enviar los cambios realizados en el repositorio local al repositorio remoto bastará con realizar un PUSH

```
$ git push origin master
```

Los dos parámetros necesarios son:

* tag de la url del repositorio remoto \(normalmente se identifica como **origin**\)
* nombre del branch que se enviará \(en este ejemplo es **master**\)

#### git pull

En el caso de que el repositorio remoto sea actualizado entonces existirá la necesidad de actualizar nuestro repositorio local con los nuevos cambios, para ellos usaremos el siguiente comando:

```
$ git pull origin master
```

Ambos comandos, tanto **push** como **pull** actualizan el repositorio remoto o local **por branch. **

#### git fetch

El repositorio remoto tendrá noción de que pueden existir algunos tags o branches en el repositorio remoto, sin embargo puede existir el caso de que estos existan ahí y el repositorio local no tenga noción de ellos, para ello es necesario actualizar la información del repositorio remoto en el repositorio local, para ello usamos este comando:

```
$ git fetch

remote: Counting objects: 637, done.
remote: Compressing objects: 100% (251/251), done.
remote: Total 637 (delta 241), reused 503 (delta 186)
Recibiendo objetos: 100% (637/637), 59.61 KiB | 504.00 KiB/s, listo.
Resolviendo deltas: 100% (241/241), completado con 29 objetos locales.
Desde bitbucket.org:ebcdesarrollo/broker-oracle
 + 70d6211...a5cdc5a QA             -> origin/QA  (actualización forzada)
 + 7d1ebe5...296ca70 PROD           -> origin/PROD  (actualización forzada)
 * [nueva rama]      feature/BO-133 -> origin/feature/BO-133
 * [nueva rama]      feature/BO-134 -> origin/feature/BO-134
   ea37041..7e4e3c1  master         -> origin/master
```



