# Comandos MySQL

## Comandos Mysql USB portable
Comando para inicializar o levantar el servidor de mysql o mariadb en usb portable.
```
bin\mysqld --console
```

Comando para entrar al servidor. `-u` (En lugar de root pondras tu usuario en caso de tener, si no ingresar como root) `-p` (A lado de esto pondras la contraseña en caso de tener, en caso de no tener dejar vacio).
```
bin\mysql -u root -p 
```

Para salir usar de la base de datos mysql `exit;`. Para dejar de correr el servidor de mysql o mariadb usar la combinacion de Presiona `Ctrl + C` para copiar.

## Comandos para MySQL Localmente Windows

Esto mostrara la informacion del servidor, en caso de tener otra version o otra base de datos esto podria cambiar.
```
sc query MySQL80
```

Inicializas el servidor mysql.
```
net start MySQL80
```

Apagas el servidor mysql.
```
net stop MySQL80 
```
