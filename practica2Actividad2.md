# Actividad 2

## Creamos la tabla paises:
```
CREATE TABLE paises(pai_codsuc INTEGER
, pai_identi INTEGER
, PRIMARY KEY(pai_codsuc, pai _identi)
, pai_codigo VARCHAR(4)
, pai_nombre VARCHAR(20) );
```
## Creamos la tabla productos:
```
CREATE TABLE productos(pro_codsuc INTEGER
, pro_identi INTEGER PRIMARY KEY
, pro_codbar VARCHAR(20)
, pro_nombre VARCHAR(20)
, pro_desc VARCHAR(20)
, pro_marca VARCHAR(20)
, pro_precio DOUBLE
, pro_idepais INTEGER);
```
### Creamos las restricciones foreign key:
```
ALTER TABLE productos ADD FOREIGN KEY pro_codsuc REFERENCES paises(pai_codsuc);
ALTER TABLE productos ADD FOREIGN KEY pro_identi REFERENCES paises(pro_identi);
ON UPDATE cascade;
ON DELETE null;
```
### Cambiamos el tipo pro_marca a INTEGER:
```
ALTER TABLE productos ALTER COLUMN pro_marca TYPE INTEGER;
```
### Crear restricción de precio en valor positivo:
```
ALTER TABLE productos ADD CONSTRAINT pro_precio CHECK (pro_precio>0);
```

