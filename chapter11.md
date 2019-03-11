# Automatización

Contenido:

* Git Bisect
* Hooks

### Git Bisect

Esta es un herramienta que nos permite inspeccionar cada commit de nuestro repositorio. 

```
* ab28285  (HEAD -> feature/3) hace 2 segundos carlogilmar Commit 15 <--- commmit inestable
* 85d5a89  hace 3 segundos carlogilmar Commit 14
* f2d454e  hace 4 segundos carlogilmar Commit 13
* ea5ccbf  hace 5 segundos carlogilmar Commit 12
* 1de1f55  hace 7 segundos carlogilmar Commit 11
* ef11712  hace 16 segundos carlogilmar commit 10
* 9cb1dcd  hace 17 segundos carlogilmar Commit 9
* 9a0438f  hace 52 segundos carlogilmar commit 8 Adding bug in this commit <--
* 26a53e4  hace 2 horas carlogilmar Commit 7
* 01fa5cd  hace 2 horas carlogilmar Commit 6
* d12a348  hace 3 horas carlogilmar commit 5
* 573db4e  hace 3 horas carlogilmar commit 4
* dd24824  hace 3 horas carlogilmar commit 3
* 49a3b55  hace 3 horas carlogilmar commit 2 <--- commit estable
* 52fabcf  hace 3 horas carlogilmar First commit
```

Para usar esta herramienta habrá que identificar un commit estable y uno inestable, de tal forma que git recorrerá el rango de commits marcado por estos. 

```
$ git bisect start
$ git bisect good 49a3b55
$ git bisect bad ab28285
Biseccionando: faltan 6 revisiones por probar después de esto (aproximadamente 3 pasos)
[9a0438f6c0cee2244ba3ca66ca1d99266ce3d3c3] commit 8 Adding bug in this commit

$ (9a0438f)> grep bug readme.md
```

Al realizar este paso git se posicionará en algún commit del rango, no necesariamente en algún orden. Aquí podemos realizar la ejecución de algún comando o ejecutar alguna prueba. Si el estado del commit es inestable se marcará como "**bad"**, de lo contrario se marcara como **"good"**. A continuación git se volverá a posicionar en otro commit.

```
$ 9a0438f> git bisect bad
Biseccionando: faltan 2 revisiones por probar después de esto (aproximadamente 2 pasos)
[d12a3482af7be4e1c2740abe600ffd586014c543] commit 5
$ d12a348>  
```

Bajo esta ejecución será posible que git encuentre exactamente el primer commit inestable:

```
$ 9a0438f> git bisect bad
Biseccionando: faltan 2 revisiones por probar después de esto (aproximadamente 2 pasos)
[d12a3482af7be4e1c2740abe600ffd586014c543] commit 5
$ d12a348> grep bug readme.md
$ d12a348> git bisect good
Biseccionando: faltan 0 revisiones por probar después de esto (aproximadamente 1 paso)
[26a53e40a204a94ff6bfeada22c57d786b23ce39] Commit 7

$ 26a53e4> grep bug readme.md
$ 26a53e4> git bisect good

9a0438f6c0cee2244ba3ca66ca1d99266ce3d3c3 is the first bad commit
commit 9a0438f6c0cee2244ba3ca66ca1d99266ce3d3c3
Author: carlogilmar <carlogilmar12@gmail.com>
Date:   Sun Mar 10 19:32:16 2019 -0600

    commit 8 Adding bug in this commit

:100644 100644 ea4433c4fe263fc2715904ecea0862202722c51c f1fd125c9d48f152655d89328a4d1106cafa728d M      readme.md
```

```
$ git bisect log

git bisect start
# good: [49a3b55e1679c7130ef477b074150f723f44ae29] commit 2
git bisect good 49a3b55e1679c7130ef477b074150f723f44ae29
# bad: [ab28285c77cfdaf8152b08619c5bb8f5fff18af0] Commit 15
git bisect bad ab28285c77cfdaf8152b08619c5bb8f5fff18af0
# bad: [9a0438f6c0cee2244ba3ca66ca1d99266ce3d3c3] commit 8 Adding bug in this commit
git bisect bad 9a0438f6c0cee2244ba3ca66ca1d99266ce3d3c3
# good: [d12a3482af7be4e1c2740abe600ffd586014c543] commit 5
git bisect good d12a3482af7be4e1c2740abe600ffd586014c543
# good: [26a53e40a204a94ff6bfeada22c57d786b23ce39] Commit 7
git bisect good 26a53e40a204a94ff6bfeada22c57d786b23ce39
# first bad commit: [9a0438f6c0cee2244ba3ca66ca1d99266ce3d3c3] commit 8 Adding bug in this commit
```

```
$ git bisect reset
```

### Hooks

* Apply patch
* Commit msg
* pre-applypatch
* pre-commit
* pre-push
* pre-rebase
* pre-receive

```
#!/bin/sh

BRANCH="$( git rev-parse --abbrev-ref HEAD )"
GIT_USER="$(git config user.name)"
MSG="*${GIT_USER}* esta actualizando el branch *${BRANCH}*"
DATA="{\"text\":\"${MSG}\"}"
echo $MSG
echo "[running] Avisando a todos en el slack que estás subiendo cambios..."
curl -X POST -H 'Content-type: application/json' --data "${DATA}" slack-token

echo "[running] Aviso enviado al canal prenomina-phx en ebc-makingdevs.slack.com"
echo ""

exit 0
```





