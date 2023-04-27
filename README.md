# DS
object types in oracle.

CREATE TYPE BarType AS OBJECT ( 
	name CHAR(20), 
	addr CHAR(20) ) 

insert value

INSERT INTO Bars VALUES( 
	BarType('Joe''s Bar', 'Maple St.') ); 

