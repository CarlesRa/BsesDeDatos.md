## Entrar en postgresql:
```
  sudo su postgres
  psql
```
## Crear base de datos:
```
  CREATE DATABASE [nombre_base de datos];
```
## Conectar a la base de datos:
```
  \c [nombre _base de datos];
```
## Crear tablas:
```
  CREATE TABLE {nombre_tabla]([atributo][tipo_dato][restriccion]);
```
## Modificar tablas:
```
  ALTER TABLE [nombre_tabla] [nombre_columna] [accion_a_realizar];
```
## Insertar datos:
```
  INSERT INTO [nombre_tabla] ([coma_lista_columnas]) ([coma_lista_valores]);
```
