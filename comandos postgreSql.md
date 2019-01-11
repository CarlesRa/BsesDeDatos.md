En:
psql -U username -W -h iphost basename
Parámetros:
-U es el usuario de la base
-W mostrará el prompt de solicitud de password
-h IP del servidor de la base de datos en caso nos conectemos remotamente sino bastaría con poner
localhost
Luego ya estaremos dentro de postgres y podremos hacer consultas:
basename=# SELECT * FROM tabla; (no olvidemos el ; al final de cada query)
Ahora bien a veces necesitamos saber alguna información extra de nuestra base como las tablas que
la componen, los campos de alguna tabla, etc., para eso existen los siguientes comandos:
El equivalente de SHOW TABLES es
basename=# \d
El equivalente de SHOW DATABASES es
basename=# \l
El equivalente de SHOW COLUMNS es
basename=# \d table
El equivalente de DESCRIBE TABLE es
basename=# \d+ table
Con esto ya podemos realizar consultas a nuestra base de datos y disponer de alguna información
extra, luego para salir de la consola de postgres bastaría con escribir \q mas enter y listo ya estamos
fuera.
1)El primer comando nos enseñará como iniciar el cliente de psql en nuestra consola:
psql -U user -W -h host database
Ya hemos hablado un poco de este comando en otro post, dejo el link por si quieres ver en detalle
cada parámetro: Primeros pasos en PosgreSQL
2)Nuestro segundo comando nos ayudara a saber la lista de nuestras bases de datos, el comando es:
\l
3)Seleccionar una base de datos o cambiar de base:
\c basename
4)Listar tablas de una base de datos:
\d
Si la lista es muy larga veremos que podemos movernos hacia abajo y luego para salir solo
digitamos la letra “q”
5)Para ver la información de la estructura de una tabla en especifico:
\d table
6)Vaciar una tabla en especifico o el famoso TRUNCATE que conocemos:
TRUNCATE TABLE table RESTART IDENTITY
Con este comando borramos el contenido de una tabla y reiniciamos su indice sino agregamos
RESTART IDENTITY nuestros indices no seran reiniciados y seguiran según el ultimo registro.
7)Crear una base de datos:
CREATE DATABASE basename;
8)Borrar o eliminar una base de datos:
DROP DATABASE basename;
9)Borrar o eliminar una tabla en especifico:

DROP TABLE tablename;
10)Enviar resultados de una consulta a un archivo delimitado por |
COPY (SELECT * FROM tablename) TO '/home/tablename.csv' WITH DELIMITER '|';
Cabe mencionar que el archivo necesito permisos de escritura.
11)Uso de LIMIT y OFFSET
SELECT * FROM table LIMIT limit OFFSET offset;
Donde:
limit: es nuestro limite de registros a mostrar
offset: indica desde donde comenzaran a mostrarce los registros
12)Uso de comillas:
SELECT “column” FROM “table” WHERE “column” = 'value';
Generalmente podemos utilizar comillas dobles para nuestras columnas y comillas simples para
nuestros valores, esto no es una regla pero a veces es necesario en casos especiales, tales como
cuando ocupamos nombres reservados, por ejemplo:
SELECT to FROM table;
En este caso tenemos un campo llamado “to”, esto nos dará un error de sintaxis, por lo tanto
tendremos que usar comillas dobles:
SELECT “to” FROM table;
13)Salir del cliente psql:
\q

CAMBIAR EL PASSWORD DE UN USUARIO
Con el usuario postgres desde el cliente psql ejecutamos el comando:
ALTER USER usuario WITH PASSWORD 'nueva_password'
También, desde la linea de comandos del sistema podemos ejecutar:
psql -c "ALTER USER usuario WITH PASSWORD 'nueva_password'"

IMPORTAR FICHERO .sql
psql -h hostname -d databasename -U username -f file.sql
\i 'path/to/file.sql'
o también
PRIMERO CREAR LA BD: createdb [-T template0] newdb
y después importarla
pg_restore -d newdb db.sql
EXPORTAR BD
pg_dump mibasedatos > db.sql
