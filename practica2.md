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
  , repcli INTEGER
  , limiteCredito INTEGER);
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
  , PRIMARY KEY (codigo,num_pedido,fecha_pedido)
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
   
