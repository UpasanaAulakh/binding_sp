# binding_sp
create database DROP_DOWN_ADO
use DROP_DOWN_ADO
create table Country
(ID INT PRIMARY KEY IDENTITY,NAME VARCHAR(50));

CREATE TABLE STATE(ID INT PRIMARY KEY IDENTITY,NAME VARCHAR(80),
COUNTRYID INT  FOREIGN KEY REFERENCES COUNTRY (ID));

CREATE TABLE CITY
(ID INT PRIMARY KEY IDENTITY,NAME VARCHAR(80),
STATEID  INT FOREIGN KEY REFERENCES STATE (ID));

SELECT*FROM CITY
INSERT INTO COUNTRY VALUES('INDIA'),('PAKISTAN'),('JAPAN'),('RUSSIA'),('NEPAL');
INSERT INTO STATE VALUES('DELHI',1),('GUJARAT',1),('UP',1),
('KARACHI',2),('ISLAMABAAD',2),
('HIROSHIMA',3),('TOKYO',3),
('KIROV',4),
('BHAGMATI PRADESH',5),
('KARNALI PRADESH',5);
INSERT INTO CITY VALUES('MODINAGAR',2),('AMROHA',3),('GUBAERG TOWN',4),('RAPTI',9);
-------------------------------------------------------------------------------------------------
CREATE PROC SP_GET_COUNTRY
AS
BEGIN
SELECT ID id ,NAME name FROM COUNRTY
END
CREATE PROC SP_GET_STATE @ID INT
AS
BEGIN
SELECT ID id ,NAME name FROM STATE WHERE COUNTRYID=@ID
END

CREATE PROC SP_GET_CITY @ID INT
AS
BEGIN
SELECT ID id ,NAME name FROM CITY WHERE STATEID=@ID
END
