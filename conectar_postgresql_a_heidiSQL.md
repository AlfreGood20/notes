
# Conectar una base de datos render postgreSQL a heidiSQL

## Pasos a seguir

- Crea nueva nueva session.

### Configura la session

- Tipo de red: `PostgreSQL (TCP/IP)`
- Libreria: `libpq-17.dll`
- Nombre del host/IP: `${HOSTNAME}.oregon-postgres.render.com`
- [ ] Pedir credenciales
- Usuario: `${USERNAME}`
- Contraseña: `${PASSWORD}`
- Puerto. 5432

> Nota importante: Debes ir a SSL deberas de activar el `[x] Usar SSL` y en la parte `Certificate verification:` deberas de elegir `Sin verificación (no seguro)` Es importante hacer esto para poder acceder al host de la base de datos.
