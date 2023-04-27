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



