# Exercici Consultes base de dades ACB

## Exercici 01:
###  Mostrar el nom, cognom, altura dels jugadors mes alts de 2m. i que el seu nom continga la lletra 'a'.
```sql
  SELECT nombre,apellido,altura 
  FROM `jugador` 
  WHERE altura>2 
  AND nombre LIKE "%a%";
```
## Exercici 02:
### Mostrar els jugadors, que superen l'altura mitjana i que la ciutat del seu equip comence per 'V'.
```sql
  SELECT * 
  FROM jugador j,equipo e 
  WHERE e.ciudad LIKE "V%" AND j.equipo=e.id_equipo 
  AND j.altura>(SELECT AVG(altura) FROM jugador);
```
## Exercici 03:
### Mostrar el nom, cognom i nom del equip dels jugadors que el seu equip comença per la lletra 'R' i juga en la posició de pivot.
```sql
SELECT j.nombre,j.apellido, e.nombre 
FROM equipo e, jugador j 
WHERE e.nombre LIKE "R%" and j.equipo=e.id_equipo 
AND j.posicion LIKE "Pivot"; 
```
## Exercici 04:
### Mostrar el nom, cognom, equip del jugador mes alt de la posició Alero.
```sql
SELECT j.nombre,j.apellido,e.nombre 
FROM jugador j, equipo e 
WHERE posicion LIKE "Alero" 
AND j.equipo=e.id_equipo 
AND altura = (SELECT MAX(altura) FROM jugador where posicion LIKE "Alero");
```
## Exercici 05:
### Mostrar el nom i el equip del jugador que mes cobra.
```sql
SELECT j.nombre, e.nombre 
FROM jugador j, equipo e 
WHERE j.equipo=e.id_equipo 
AND j.salario=(SELECT MAX(salario) 
FROM jugador) GROUP BY j.nombre,e.nombre 
```
