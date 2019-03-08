# Branching

---

Por defecto cualquier repositorio de git esta en un branch llamado **master. **Es posible generar varios branches para múltiples propósitos, esto servirá para elaborar estrategias de trabajo con git.![](/assets/branch1.png)

### Operaciones sobre branches

Para crear un branch hay que tomar en cuenta el branch donde nacerá.

Para saber el branch donde estas trabajando bastará el siguiente comando:

```
$ git rev-parse --abbrev-ref HEAD

master
```

Listar los branches creados en el proyecto:

```
$ git branch 
```

Listar todos los branches incluyendo los remotos

```
$ git branch -a

* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
```

Crear un branch nuevo

```
$ git branch <nombre-del-branch>
```

Posicionarse en un branch existente:

```
$ git checkout <nombre-del-branch>
```

Crear y posicionarse en un nuevo branch

```
$ git checkout -b <nombre-del-branch-nuevo>
```

Cada branch creado podrá guardar cambios:![](/assets/branch4.png)Sin embargo existirá la necesidad de concentrar todos esos cambios guardados en cada branch en un sólo branch.

Para ello uniremos los cambios en un sólo branch con el comando** git merge**

```
$ git merge branch-a-mezclar
```

Este comando unirá los cambios del branch que se indica sobre el branch donde se esta trabajando. El tag HEAD indicará el branch donde se esta trabajando. En el siguiente ejemplo se hace merge en **master** del **branch1, **nada cambia más que la posición del indicador HEAD. ![](/assets/branch5.png)Pero al mezclar el **branch2** ocurrirá lo siguiente:![](/assets/branch6.png)

Se creará un nuevo commit como referencia de que se esta mezclando otro branch.

Si mezclamos el branch3 de nuevo obtendremos un sólo branch \(**master**\) con todos los cambios en los branches creados:![](/assets/branch7.png)



