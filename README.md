1.-update: (actualizar algún dato especìfico en una tabla)


![1 UPDATE](https://user-images.githubusercontent.com/107563009/200398825-ede64d3d-0a87-420b-8b13-5b21a0edf42f.PNG)
 
 
	sqlite> update users set lastname = ‘Starktion’ where userid =1;
	sqlite> select * from users where userid =1;
 

2.-estructura de la base de datos .schema

![2 SCHEMA](https://user-images.githubusercontent.com/107563009/200427188-f983620b-9f22-4d7a-bbe6-d19827d68948.PNG)
 
sqlite>.schema users
“CREATE TABLE users (userid int, firstname text, lastname text, email text );”
 
 
3.-date and time functions (definiciòn de la fecha y hora respectivamente)

![3 datetime](https://user-images.githubusercontent.com/107563009/200427213-b434c8da-16f6-49f8-a4ef-17cf716252bc.PNG)
 
sqlite>CREATE TABLE dates (fecha1 text, fechacomp);
 
sqlite>INSERT INTO dates(fecha1, fechacomp) values(datetime(‘now’), datetime(‘now’,’localtime’));
 
sqlite>select * from dates;
 
 
4.-primary key constraint

![4 PRIMARY KEY](https://user-images.githubusercontent.com/107563009/200427235-dcafb0e2-8ecd-4b41-96e1-75d2f1b4b999.PNG)
 
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

![5 NOT NULL](https://user-images.githubusercontent.com/107563009/200427245-b323d64f-535a-411c-8d81-ffe0ef1171b7.PNG)
 
 
6.-unique constraint(restricciòn bàsica que impide que un unico dato se encuentre en diferentes filas o registros)

![6 UNIQUE CONSTRAINT](https://user-images.githubusercontent.com/107563009/200427265-78d9c9f7-654c-462d-a586-12964e9250a8.PNG)
 
sqlite>create unique index ind20 ON users (userid);
 
sqlite>select * from users where userid ="ind20";
 

7.-default constraint (proporciona un valor determinado para una columna)

![7 DEFAULT CONSTRAINT II](https://user-images.githubusercontent.com/107563009/200427293-bfc8ecbb-16e6-41f2-911d-d2e209c3b233.PNG)

 
sqlite>create table def7 (space1 INTEGER DEFAULT 15, space2 INTEGER DEFAULT 20);
 
sqlite>insert into def7 DEFAULT VALUES;
 
sqlite> select * from def7;
 
.
.
.

![7 DEFAULT CONSTRAINT](https://user-images.githubusercontent.com/107563009/200427318-52946e91-1413-43a5-abea-416465a4cd80.PNG)

“Ahora insertando datos a otra tabla con un select aplicando el concepto de DEFAULT”
 
sqlite> create table def7II(sp1 INTEGER, sp2 INTEGER);
 
sqlite> INSERT INTO def7II SELECT space1, space2 FROM def7;
 
sqlite> select * from def7II;
 
 
 

8.-check constraint (Limìta el rango de valores que se puede colocar en una columna)

![8 CHECK CONSTRAINT](https://user-images.githubusercontent.com/107563009/200427350-d7bffad2-3117-4627-9e8f-653d4c6d90a6.PNG)
 
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

![9 ALTER TABLE](https://user-images.githubusercontent.com/107563009/200427367-60cb5705-db9d-40ab-95ed-bb46dfbc6810.PNG)
 
sqlite> ALTER TABLE PEOPLE8 ADD COLUMN SPORT TEXT;
 
sqlite> SELECT * FROM PEOPLE8;
 
sqlite> .schema PEOPLE8
 
>>CREATE TABLE PEOPLE8 (Id INT NOT NULL, Lastname varchar(255), Firstname varchar(255), Age INT CHECK (AGE=22), SPORT TEXT);
 
 
10.-delete(Borrar registros de las tablas de una base de datos), drop(Borra por completo la estructura de una tabla)

![10 DELETE AND DROP](https://user-images.githubusercontent.com/107563009/200427388-8e28ae55-b0d7-4a85-9836-2d3a036d9946.PNG)
 
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
 
 
11.-backup (Hacer una copia de seguridad de la base de datos), 
 
![image](https://user-images.githubusercontent.com/107563009/200433505-8c41b4ab-fa2d-4af9-ae90-01ac8c253670.png)

![image](https://user-images.githubusercontent.com/107563009/200435174-7e687f1b-2839-42a8-8b42-2ed6effda305.png)





restore(restaura la base de datos)


![image](https://user-images.githubusercontent.com/107563009/200436043-1dfbfda1-7d74-497f-b7e5-132b37a9cd2c.png)

