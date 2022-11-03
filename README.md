1.-update: (actualizar algún dato especìfico en una tabla)
 
 
	sqlite> update users set lastname = ‘Starktion’ where userid =1;
	sqlite> select * from users where userid =1;
 

2.-estructura de la base de datos .schema
 
sqlite>.schema users
“CREATE TABLE users (userid int, firstname text, lastname text, email text );”
 
 
3.-date and time functions (definiciòn de la fecha y hora respectivamente)
 
sqlite>CREATE TABLE dates (fecha1 text, fechacomp);
 
sqlite>INSERT INTO dates(fecha1, fechacomp) values(datetime(‘now’), datetime(‘now’,’localtime’));
 
sqlite>select * from dates;
 
 
4.-primary key constraint
 
sqlite>CREATE TABLE primary4(zone1 INTEGER PRIMARY KEY, zone2 TEXT NOT NULL);
 
sqlite>insert into primary4(zone1, zone2)values("11", "Chapinero");
 
sqlite> select * from primary4;
 
 
 
 
5.-not null constraint (restricciòn bàsica que impide la contenciòn de valores nulos)
 
	sqlite> CREATE TABLE dptos5 (
   ...>  id_dpto INTEGER PRIMARY KEY AUTOINCREMENT,
   ...>  denom TEXT NOT NULL UNIQUE
   ...> );
 
sqlite>insert into dptos5 (id_dpto, denom)values(1, "Penthouse");
 
sqlite>select * from dptos5;
 
 
6.-unique constraint(restricciòn bàsica que impide que un unico dato se encuentre en diferentes filas o registros)
 
sqlite>create unique index ind20 ON users (userid);
 
sqlite>select * from users where userid ="ind20";
 

7.-default constraint (proporciona un valor determinado para una columna)
 
sqlite>create table def7 (space1 INTEGER DEFAULT 15, space2 INTEGER DEFAULT 20);
 
sqlite>insert into def7 DEFAULT VALUES;
 
sqlite> select * from def7;
 
.
.
.
 
“Ahora insertando datos a otra tabla con un select aplicando el concepto de DEFAULT”
 
sqlite> create table def7II(sp1 INTEGER, sp2 INTEGER);
 
sqlite> INSERT INTO def7II SELECT space1, space2 FROM def7;
 
sqlite> select * from def7II;
 
 
 

8.-check constraint (Limìta el rango de valores que se puede colocar en una columna)
 
sqlite> CREATE TABLE PEOPLE8 (Id INT NOT NULL, Lastname varchar(255), Firstname varchar(255), Age INT CHECK (AGE=22));
 
sqlite> SELECT * FROM PEOPLE;
Parse error: no such table: PEOPLE
sqlite> INSERT INTO PEOPLE8(Id, Lastname, Firstname, Age)values(1, "Lightion", "Leinad", 20);
Runtime error: CHECK constraint failed: AGE=22 (19)
 
sqlite> INSERT INTO PEOPLE8(Id, Lastname, Firstname, Age)values(1, "Lightion", "Leinad", 19);
Runtime error: CHECK constraint failed: AGE=22 (19)
 
sqlite> INSERT INTO PEOPLE8(Id, Lastname, Firstname, Age)values(1, "Lightion", "Leinad", 21);
Runtime error: CHECK constraint failed: AGE=22 (19)
 
sqlite> INSERT INTO PEOPLE8(Id, Lastname, Firstname, Age)values(1, "Lightion", "Leinad", 18);
Runtime error: CHECK constraint failed: AGE=22 (19)
sqlite> INSERT INTO PEOPLE8(Id, Lastname, Firstname, Age)values(1, "Lightion", "Leinad", 22);
sqlite>
 
 
9.-alter table
 
sqlite> ALTER TABLE PEOPLE8 ADD COLUMN SPORT TEXT;
 
sqlite> SELECT * FROM PEOPLE8;
 
sqlite> .schema PEOPLE8
 
>>CREATE TABLE PEOPLE8 (Id INT NOT NULL, Lastname varchar(255), Firstname varchar(255), Age INT CHECK (AGE=22), SPORT TEXT);
 
 
10.-delete(Borrar registros de las tablas de una base de datos), drop(Borra por completo la estructura de una tabla)
 
sqlite> UPDATE PEOPLE8 SET Id =2 where SPORT ='BASKT';
 
sqlite> SELECT * FROM PEOPLE8;
 
sqlite> DELETE FROM PEOPLE8 WHERE Id =1;
 
sqlite> SELECT * FROM PEOPLE8;
 
sqlite> .tables
 
sqlite> create table subjs(cebo1 INT PRIMARY KEY, cebo2 VARCHAR(255), cebo3 INT, cebo4 TEXT);
 
sqlite> .tables
 
sqlite> DROP TABLE subjs;
 
sqlite> .tables
 
PEOPLE8   dates     def7      def7II    dptos5    primary4  users
 
 
11.-backup (Hacer una copia de seguridad de la base de datos), restore(restaura la base de datos)
 
sqlite>
sqlite>
