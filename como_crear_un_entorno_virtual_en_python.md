# Como crear un entorno virtual en python

## Paso a paso
Ejecutar en la terminal el siguente comando, ya sea en powershell o en bash:

```powershell
py -m venv venv
```
> **Nota:** En algunos casos el `py` puede cambiar por `python`. Consulte la documentacion de python.
>

### Entrar al entrono virtual

En powershell y en terminal bash:
```powershel
./venv/Scripts/activate
```

En MacOs:
```
source venv/bin/activate
```

Para salir del entorno virtual
```
deactivate
```