# Exercici Consultes base de dades ACB

## Exercici 01:
###  Mostrar el nom, cognom, altura dels jugadors mes alts de 2m. i que el seu nom continga la lletra 'a'.
```
  SELECT nombre,apellido,altura FROM `jugador` WHERE altura>2 AND nombre LIKE "%a%";
```
## Exercici 02:
### Mostrar els jugadors, que superen l'altura mitjana i que la ciutat del seu equip comence per 'V'.
```
  SELECT * FROM jugador j,equipo e WHERE e.ciudad LIKE "V%" AND j.equipo=e.id_equipo AND j.altura>(SELECT AVG(altura) FROM jugador);
```
```
SELECT  e.nombre,count(*) FROM equipo e, jugador j where e.id_equipo=j.equipo GROUP BY e.id_equipo HAVING COUNT(*)= ALL (SELECT COUNT(*) FROM
jugador group BY e.id_equipo);
```
