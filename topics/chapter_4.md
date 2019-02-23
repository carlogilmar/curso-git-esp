# Manipulación de un repositorio

### Situarse en un commit previo

Ver el log de commits
```
$ git log --pretty=oneline
165075cded502e1c120005f87aed07cd9335b846 (HEAD -> master) update chapter 3
d08d6829701f41f023401e440576928ba5abc93a (origin/master, origin/HEAD) update chapter 3
0fc1d128dd48b240a013a4063f88c9bedc7c46c4 update readme
4ed6f00fd729a74bce2747ac7dad21bdf699e47b update readme
0d65465b99d960115f95ed4a4de33fb2f007babc Update chapter 2
8e04b9f05f50e09bfd6872f077917ab5c1acbbef Update chapter 2
fb01c7e8a8f5910ac04795d06ca327ecd14d8afc Update chapter 2
a6bb26cbb1088f8c9f933a47efa74e41d3f08c7a Adding img
220626a557023f5a59797285257b1d5d9b8d7f6b Update chapter 2
2898a40ce72fd2ab4e7dcdb167ad68ea83b928c4 Update chapter 2
```

Regresar a un commit específico (ir al pasado)
```
$ git checkout 220626a557023f5a59797285257b1d5d9b8
```

Regresar al último commit realizado (presente)
```
$ git checkout master
```

### Búsquedas sobre el log

```
$ git log --grep="palabras-a-buscar-en-log"
```

Ver log y contenido de cada commit
```
$ git log -p
```

### git show

Ver el contenido de un commit
```
$ git show hash-del-commit
```

### git blame

Ver los commits hechos en un archivo
```
$ git blame archivo
```

