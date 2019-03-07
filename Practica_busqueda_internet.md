
# Proyecto Bases de Datos en internet

## Empresa Media markt:

### 1º Creem la database
```sql
	CREATE DATABASE mediamarkt;
```
### 2º Creem les tables
```sql
	CREATE TABLE  smartphones (id_smartphone INTEGER PRIMARY KEY,
	s_operativo VARCHAR(20),
	processador VARCHAR(20),
	marca VARCHAR(20),
	cap_memoria VARVHAR(10));
```
```sql
	CREATE TABLE smartwatches(id INTEGER PRIMARY KEY,
	processador VARCHAR(20),
	cap_memoria VARCHAR(20),
	nfc BOOLEAN,
	display VARCHAR(20));
```
```sql
	CREATE TABLE sportwatches(id INTEGER PRIMARY KEY,
	pantalla_color BOOLEAN,
	bateria VARCHAR(20),
	color VARCHAR(20));
```
```sql
	CREATE TABLE auriculares(id INTEGER PRIMARY KEY,
	tipo_construccion VARCHAR(30),
	transmision VARCHAR(30),
	microfono BOOLEAN,
	color VARCHAR(30));
```
```sql
  CREATE TABLE fundas(id_funda INTEGER PRIMARY KEY,
	color VARCHAR(30),
	telefono INTEGER,
	FOREIGN KEY(telefono) REFERENCES smartphones(id_smartphone));
```
### 3º Plenem les tables
```sql
	INSERT INTO smartphones VALUES (1,Android one,optacore,Samsung,64 Gb);
	INSERT INTO smartphones VALUES (2,'Android 8','quad-core','Xiaomi','32Gb');
	INSERT INTO smartphones VALUES (3,'Android 7.5','quad-core','LG','32Gb');
	INSERT INTO smartphones VALUES (4,'Ios 4.5','dual-core','Apple','16Gb');
	INSERT INTO smartphones VALUES (5,'Ios 8','quad-core','Apple','32Gb');
```
```sql
	INSERT INTO smartwatches VALUES (1,'qualcom','2Gb',true,'1,2 pulgadas');
	INSERT INTO smartwatches VALUES (2,'qualcom','1.5Gb',false,'1,6 pulgadas');
	INSERT INTO smartwatches VALUES (3,'intel','1.7Gb',true,'1,4 pulgadas');
	INSERT INTO smartwatches VALUES (4,'intel','2Gb',true,'2 pulgadas');
	INSERT INTO smartwatches VALUES (5,'razer','4Gb',true,'2.5 pulgadas');
```
```sql
	INSERT INTO sportwatches VALUES (1,true,'1000 Ma','rosa');
	INSERT INTO sportwatches VALUES (2,false,'900 Ma','negro');
	INSERT INTO sportwatches VALUES (3,false,'900 Ma','negro');
	INSERT INTO sportwatches VALUES (4,true,'1200 Ma','magenta');
	INSERT INTO sportwatches VALUES (5,false,'900 Ma','negro');
```
```sql
	INSERT INTO auriculares VALUES (1,'intra-aurales','inhalambrica',true,'rosa');
	INSERT INTO auriculares VALUES (2,'intra-aurales','cable',false,'verde');
	INSERT INTO auriculares VALUES (3,'normal','cable',true,'rojo');
	INSERT INTO auriculares VALUES (4,'normal','cable',true,'negro');
	INSERT INTO auriculares VALUES (5,'intra-aurales','inhalambrica',true,'negro');
```
```sql
	INSERT INTO fundas VALUES (1,'blanco',1);
	INSERT INTO fundas VALUES (2,'rosa',1);
	INSERT INTO fundas VALUES (3,'lila',2);
	INSERT INTO fundas VALUES (4,'lila',4);
	INSERT INTO fundas VALUES (5,'negro',2);
	INSERT INTO fundas VALUES (6,'negro',1);
```
### 4º Selects
	
#### 1) Muestra los smartphones que pueden tener la funda rosa.
```sql
	SELECT s.*,f.color FROM smartphones s,fundas f 
	WHERE f.color='rosa' 
	AND s.id_smartphone=f.telefono;
```
#### 2) Muestra la marca de los smartphones que tienen un procesador quad-core.
```sql
	SELECT marca FROM smartphones 
	WHERE processador LIKE 'quad-core';
```
#### 3) Muestra los smartwotches con procesador marca qualcom y que tengan NFC.
```sql
	SELECT * FROM smartwatches 
	WHERE processador LIKE 'qualcom' 
	AND nfc=true;
```








#### 4) Muestra los smartphones con fundas de color negro de marca xiaomi.
```sql
	SELECT * FROM smartphones s,fundas f 
	WHERE f.color LIKE 'negro' 
	AND s.id_smartphone=f.telefono 
	AND s.marca LIKE 'xiaomi';
```
#### 5) Muestra cuantos smartwatches hay de color negro.
```sql
	SELECT COUNT(*)AS Cantidad_Sportwatches FROM sportwatches 	
  WHERE color LIKE 'negro';
```


	
