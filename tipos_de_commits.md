
# Tipos de commits para git 🖊️

Los tipos de commits en git es la forma se organizan habitualmente mediante la especificacion de `Conventional Commits` para mantener un historial claro, legible y automatizable.

## ¿Qué es un commit?
Es una forma de guardar el punto de partida o una captura instantanea de los cambios preparados en ese momento del proyecto.

### Comando
```bash
git commit -m "type: description"
```
Antes de ejecutar `git commit`, se utiliza el comando `git add` para pasar o "preparar" los cambios en el proyecto que se almacenarán en una confirmación. Estos dos comandos, git commit y git add, son dos de los que se utilizan más frecuentemente.

##  Tipos 🧩

El tipo hace referencia a grandes rasgos sobre los cambios que se están guardando en ese commit. Por ejemplo, si las modificaciones que hicimos fueron relacionadas a agregar una nueva característica o función, usaríamos el tipo feat.

### Tabla

|    Tipo            |                      Uso                            |
|--------------------|-----------------------------------------------------|
|    tada            |     Comenzar un proyecto                            | 
|    release         |     Deploy de cosas                                 |
|    new version     |     Etiqueta / version de lanzamiento               |
|    feat            |     Nueva caracteristica                            |
|    refactor        |     Refactorizar codigo                             |
|    fix             |     Arreglo de un bug                               |
|    patch           |     Solucion simple para un problema no critico     |
|    perf            |     Mejorar el rendimiento                          |
|    style           |     Mejorar la estructura / formato del codigo      |
|    ui              |     Agregar o actulizar la interfaz de usuario      |
|    ux              |     Mejorar la experiencia de usuario               |
|    remove          |     Eliminar codigo o archivos                      |
|    construction    |     Trabajo en progreso                             |
|    add             |     Agregar una dependencia                         |
|    upgrade         |     Actulizar dependencia                           |
|    downgrade       |     Degradar dependencia                            |
|    revert          |     Revertir cambios                                |
|    accessibility   |     Mejorar la accesibilidad                        |
|    merge           |     Fusionar ramas                                  |
|    test            |     Agregar o actulizar pruebas                     |
|    config          |     Agregar o actulizar archivos de configuracion   |
|    script          |     Agregar o actulizar scripts de desarrollo       |
|    typos           |     Corregir errores tipograficos                   |
|    assets          |     Agregar o actualizar assets (Imagenes)          |
|    responsive      |     Trabajo en diseño responsive                    |
|    docs            |     Agregar o actualizar documentacion              |
|    security        |     Solucionar problemas de seguridad               |
|    businness       |     Agregar o actulizar logica de negocios          |