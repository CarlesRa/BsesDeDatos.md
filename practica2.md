# Base de datos Oficina (Actividad 1)

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
  , título VARCHAR(15)
  , contrato INTEGER
  , jefe INTEGER
  , cuota INTEGER
  , ventas INTEGER);
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
  ### Tabla Clientes:
  
  ```
  CREATE TABLE Clientes(num_cliente INTEGER PRIMARY KEY
  , nombre VARCHAR(20)
  , repcli INTEGER);
  ```
  ### Tabla Productos:
  
  ```
  CREATE TABLE Productos(id_fab INTEGER
  , id_producto INTEGER
  , PRIMARY KEY (id_fab,id_producto)
  , descripcion VARCHAR(50)
  , precio INTEGER
  , existencias INTEGER);
  ```
  ### Tabla Pedidos:
  
  ```
  CREATE TABLE Pedidos(codigo INTEGER
  , num_pedido INTEGER
  , fecha_pedido TIMESTAMP
  , clie INTEGER
  , FOREIGN KEY(clie) REFERENCES clientes(num_cliente)
  , rep INTEGER
  , FOREIGN KEY(rep) REFERENCES empleados(num_empleados)
  , fab VARCHAR(50)
  , producto INTEGER
  , FOREIGN KEY(producto) REFERENCES Productos(id_producto)
  , cantidad INTEGER
  , importe INTEGER);
  ```
  ### Añadimos a Clientes la columna "limiteCredito":
  ```
  ALTER TABLE Clientes ADD COLUMN limiteCredito INTEGER;
  ```
  ### Añadimos a empleados las claves foraneas que le faltan:
  ```
  ALTER TABLE Empleados ADD FOREIGN KEY (oficina) REFERENCES Oficinas(oficina);
  ALTER TABLE Empleados ADD FOREIGN KEY (jefe) REFERENCES Empleados(num_empleado);
  ```
  ### Creamos restricción en la tabla empleados:
 ```
  ALTER TABLE Empleados ADD CONSTRAINT nombre UNIQUE(nombre);
 ```
  ### Añadir a pedidos la clave principal:
  ```
  ALTER TABLE Pedidos ADD PRIMARY KEY (num_pedido, fecha_pedido);
  ```
  ### Definimos un indice sobre la columna region de la tabla oficinas:
  ```
  CREATE INDEX regiones ON oficinas(region);
  ```
  ### Borramos el indice:
  ```
  DROP INDEX regiones ON oficinas(region);
  ```
  
