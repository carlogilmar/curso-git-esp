# Branching

Contenido:

* Crear un branch
* Operaciones sobre un branch
* git merge
* Abortar operaciones

---

Por defecto cualquier repositorio de git esta en un branch llamado **master. **Es posible generar varios branches para múltiples propósitos, esto servirá para elaborar estrategias de trabajo con git.![](/assets/branch1.png)

### Creación de branches

Para crear un branch hay que tomar en cuenta el branch donde nacerá. 

Para saber el branch donde estas trabajando bastará el siguiente comando:

```
$ git rev-parse --abbrev-ref HEAD

master
```



