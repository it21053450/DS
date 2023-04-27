# DS
object types in oracle.

CREATE TYPE BarType AS OBJECT ( 
	name CHAR(20), 
	addr CHAR(20) ) 

insert value

INSERT INTO Bars VALUES( 
	BarType('Joe''s Bar', 'Maple St.') ); 

#Column Objects
CREATE TYPE BeerType AS OBJECT ( 
	name CHAR(20), 
	manf CHAR(20) ) 
	/
CREATE TABLE menu
	(bar bartype,
	 beer beertype,
	 price real);
	 
#Alternative: Object table 
CREATE TYPE MenuType AS OBJECT ( 
	bar BarType,
	beer BeerType,
	price real) 
/
CREATE TABLE Menu2 OF MenuType;

#ref
CREATE TYPE MenuType2 AS OBJECT (
	bar		REF BarType,
	beer		REF BeerType,
	price	FLOAT)

#Obtaining REFs

CREATE TABLE Sells OF MenuType2;
INSERT INTO sells VALUES(
	(SELECT REF(b) FROM bars b WHERE name='Jim''s'),
	(SELECT REF(e) FROM beers e WHERE name='Swan'),
	2.40);

#Retrieving with REF Datatype
SELECT s.bar.name, s.beer.name, price 
	FROM sells s;

#Dereferencing
SELECT s.beer.name 
	FROM Sells s 
	WHERE s.bar.name = 'Joe''s Bar'; 

#Constraints on Object Tables

CREATE TYPE person AS OBJECT (
	pid NUMBER, 
	name VARCHAR(25), 
	address VARCHAR(50));
/
CREATE TABLE person_table OF person 
	( pid PRIMARY KEY,
      name NOT NULL
    );










