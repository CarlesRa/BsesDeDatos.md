# Base de datos Oficina

## Creación de la base de datos:

  ```
  sudo -i -u postgres
  psql
  CREATE DATABASE oficina;
  
  ```
## Conectar a la base de datos:
  ```
  
  \c oficinas
  ```
  
## Creación de las tablas y atributos:

  ### Tabla Empleados:
```
  CREATE TABLE Empleados(num_empleado INTEGER PRIMARY KEY
  , nombre VARCHAR(20)
  , edad INTEGER
  , oficina INTEGER
  , FOREIGN KEY(oficina) REFERENCES Oficina(oficina)
  , título VARCHAR(15)
  , contrato INTEGER
  , jefe INTEGER
  , FOREING KEY(jefe) REFERENCES empleados(num_empleado)
  , cuota INTEGER
  ,ventas INTEGER);
  ```
  ### Tabla Oficinas:
    
    
    ```
    
   CREATE TABLE Oficinas(oficina INTEGER PRIMARY KEY
   , ciudad VARCHAR(15)
   , región VARCHAR(15)
   , director INTEGER
   , FOREIGN KEY(director) REFERENCES empleados(num_empleado)
   , objetivo INTEGER
   , ventas INTEGER);
   
   ```
  
