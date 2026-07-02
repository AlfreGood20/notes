# Comandos git

Ubicar la carpeta donde se trabajara
```
$ cd
```

Inicializar esa carpeta como repositorio local
```
$ git init
```

Para crear una carpeta en git
```
$ mkdir 
```

Muestra el estado del repositorio local
```
$ git status 
```

Agregar el link del repositorio remoto
```
$ git remote add origin
```
 
Muestra como se llama la rama el cual a subir
```
$ git branch 
```

Subir los archivos al repositorio remoto, indicarle el nombre de la rama
```
$ git push origin [rama]
```

Poder poner un comentario del archivo subido
```
$ git commit -m "#Comentario"
```

Esto agrega al repositorio local los archivos modificados o nuevos.
```
$ git add example.py
```

Para verificar si se hiso vinculo el repositorio remoto con el local
```
$ git remote -v
```

Trae los cambio de remoto al local
```
$ git pull origin [rama]
```

Trae los cambio del remoto al local encima de local ideal antes de un git push
```
$ git pull --rebase origin master
```

Esto crea una nueva rama para poder trabajar
```
$ git branch [Nombre de la nueva rama] 
```

Saltar a la rama la cual quiero estar
```
$ git checkout [Nombre de la rama]
```

Para poder ver los últimos commit de cada rama
```
$ git branch -v 
```

Para poder ver las ramas la cuales no están fucionada con el master
```
$ git brach --no-merged 
```

Esto crea y salta a la rama cual a trabajar en lugar de hacer y saltar
```
$ git checkout -b [Nombre de la rama]
```

Este comando lo que hace es fucionar la rama con la de master.
```
$ git merge [nombre de la rama]
```
>**Nota:** cambiar a la rama master antes de usar el comando


Con este comando hace es eliminar una rama la cual ya no vas  a usar y que ya este fucionada con la master
```
$ git branch -d [Nombre de la rama]
```

Con este comando lo que hace es quitar el ultimo comit e enviado
```
$ git reset --hard HEAD~1 
```

Con este comando puedes volver al commit donde llames
```
$ git reset --hard [Commit] 
```

Con este comando se puede ver el total de commit enviados
```
$ git log
```

## Paso a paso para borar un commit y regresar a un commit especifico

Ver todos los commit hechos en forma de lista igual de las ramas
```
$ git log --oneline 
```

Esto lo que hace es volver a ese commit y borrar los que estaban después
```
$ git reset --hard [numeración del commit] 
```

Lo que hace es forzar el empuje y poder subir al remoto
```
$ git push origin master --force
```