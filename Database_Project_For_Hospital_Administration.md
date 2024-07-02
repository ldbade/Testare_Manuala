<h1>Database Project for **Hospital**</h1>

The scope of this project is to use all the SQL knowledge gained throught the Software Testing course and apply them in practice.

**Application under test**: HospitalDepartment

**Tools used**: MySQL Workbench

**Database description**: A continuous updated databases in a hospital make the work much easier for all staff.


<h2>Database Schema</h2>

You can find below the database schema that was generated through Reverse Engineer and which contains all the tables and the relationships between them.

![DiagramSQL](https://github.com/ldbade/Testare_Manuala/assets/161169534/90fa17b0-295e-4b60-807c-c92c294e81a7)


  
The tables are connected in the following way:


  - **RespDepartment**  is connected with **Employees** through a **one to one** relationship which was implemented through **RespDepartment.DepID** as a primary key and **Employees. DepID** as a foreign key
  - **Hospitalization**  is connected with **RespDepartment** through a **one to many** relationship which was implemented through **Hospitalization.PacFileID** as a primary key and **RespDepartment.PacFileID** as a foreign key
  - **PatientData**  is connected with **Hospitalization** through a **one to many** relationship which was implemented through **PatientData.PacHospID** as a primary key and **Hospitalizatio.PacHospID** as a foreign key
 
  - **Treatment**  is connected with **Hospitalization.TreatID** through a **one to many** relationship which was implemented through **Treatment.TreatID** as a primary key and **Hospitalization.TreatID** as a foreign key
  - **Farmacy**  is connected with **Treatment.TreatID** through a **one to many** relationship which was implemented through **Farmacy.FarmID** as a primary key and **Treatment.FarmID** as a foreign key
  - **Laboratory**  is connected with **Hospitalization.LabTestID** through a **one to many** relationship which was implemented through **Laboratory.LabTestID** as a primary key and **Hospitalization.LabTestID** as a foreign key


<h2>Database Queries</h2>

  <h3>DDL (Data Definition Language)</h3>

  The following instructions were written in the scope of CREATING the structure of the database (CREATE INSTRUCTIONS):
  ```
CREATE DATABASE HospitalDepartment;
CREATE TABLE RespDepartment (
DepID int NOT NULL AUTO_INCREMENT,
DepName varchar (20) NOT NULL,
PacFileID int NOT NULL,
EmpID int NOT NULL,
PRIMARY KEY (DepID)
);
```

```
CREATE TABLE Employees (
EmpID int NOT NULL,
EmpLastName varchar (150) NOT NULL,
EmpFirstName varchar (150) NOT NULL,
EmpCNP varchar (13) NOT NULL,
Speciality varchar (50) NOT NULL,
DepID int NOT NULL,
Salary float NULL
);
```

```
CREATE TABLE Hospitalization(
PacFileID varchar (10) NOT NULL,
PacHospID varchar (10) NOT NULL,
DepID int NOT NULL,
Room varchar (10) NOT NULL,
Diagnostic varchar (255) NOT NULL,
TreatID varchar (255) NOT NULL,
Dateofadmission Datetime NOT NULL,
Dateofdischarge Datetime NULL,
LabTestID varchar (10) NOT NULL,
FarmID varchar (10) NOT NULL,
PRIMARY KEY (PacFileID)
);
```
```
CREATE TABLE PatientData (
PacHospID varchar(10) NOT NULL,
PacFileID varchar (10) NOT NULL,
PacLastName varchar (255) NOT NULL,
PacFirstName varchar (255) NOT NULL,
CNP varchar (13) NOT NULL,
City varchar (100) NOT NULL,
Address varchar (100) NULL,
PacType varchar (100) NOT NULL,
PacPhone int NOT NULL,
FamilyNo int NOT NULL
);
```
```
CREATE TABLE Treatment (
TreatID varchar(10) NOT NULL,
PacHospID varchar(10) NOT NULL,
MedName varchar(200),
MedcineDose varchar (20) NOT NULL,
MedicineTime varchar (20) NOT NULL,
MedicineWay varchar (25) NOT NULL
);
```
```
CREATE TABLE Farmacy (
FarmID varchar (10) NOT NULL,
PacFileID varchar (10) NOT NULL,
MedName1 varchar (100) NOT NULL,
MedName2 varchar (100) NULL,
MedName3 varchar (100) NULL,
MedName4 varchar (100) NULL, 
MedName5 varchar (100) NULL,
MedName6 varchar (100) NULL,
TreatID varchar(10) NOT NULL
);
```

```
CREATE TABLE Laboratory (
LabTestID varchar(10) NOT NULL,
PacFileID varchar(10) NOT NULL,
TestName varchar(255) NOT NULL,
TestDate date NOT NULL,
TestResults varchar(255) NULL
);
```
  After the database and the tables have been created, a few ALTER instructions were written in order to update the structure of the database, as described below:
- **ALTER TABLE** RespDepartment MODIFY COLUMN PacFileID varchar (10) NOT NULL;
- **ALTER TABLE** Employees ADD PRIMARY KEY (EmpID);
- **ALTER TABLE** RespDepartment ADD CONSTRAINT
FOREIGN KEY (EmpID) REFERENCES Employees(EmpID);
- **ALTER TABLE** Treatment CHANGE PacHospID PacFileID varchar (10) NOT NULL;
- **ALTER TABLE** Treatment CHANGE MedcineDose MedicineDose varchar (20) NOT NULL;
- **ALTER TABLE** InPatients RENAME OutPatients;
- **ALTER TABLE** OutPatients RENAME COLUMN InPatientID TO OutPatientID;

```
CREATE TABLE InPatients (
OutPatientID int (1) NOT NULL AUTO_INCREMENT,
PacHospID varchar(4) NOT NULL,
PacLastName varchar (255) NOT NULL,
PacFirstName varchar (255) NOT NULL,
CNP varchar (13) NOT NULL,
City varchar (100) NOT NULL,
Address varchar (100) NULL,
PacType varchar (100) NOT NULL,
PacPhone int NOT NULL,
FamilyNo int NOT NULL,
PRIMARY KEY (OutPatientID)
);
```
 
  
  <h3>DML (Data Manipulation Language)</h3>

  In order to be able to use the database I populated the tables with various data necessary in order to perform queries and manipulate the data. 
  In the testing process, this necessary data is identified in the Test Design phase and created in the Test Implementation phase. 

  Below you can find all the insert instructions that were created in the scope of this project:

```
INSERT INTO RespDepartment VALUES (1, 'RESPIRATORY', 'RESP138', 21);
INSERT INTO RespDepartment VALUES (2, 'RESPIRATORY', 'RESP139', 22);
INSERT INTO RespDepartment VALUES (3, 'RESPIRATORY', 'RESP140', 23);
INSERT INTO RespDepartment VALUES (4, 'RESPIRATORY', 'RESP141', 24);
INSERT INTO RespDepartment VALUES (5, 'RESPIRATORY', 'RESP142', 25);
INSERT INTO RespDepartment VALUES (6, 'RESPIRATORY', 'RESP143', 26);
INSERT INTO RespDepartment VALUES (7, 'RESPIRATORY', 'RESP144', 27);
INSERT INTO RespDepartment VALUES (8, 'RESPIRATORY', 'RESP145', 28);
INSERT INTO RespDepartment VALUES (9, 'RESPIRATORY', 'RESP146', 29);
INSERT INTO RespDepartment VALUES (10, 'RESPIRATORY', 'RESP147', 30);
```
```
INSERT INTO Employees VALUES (21, 'Popescu', 'Adrian', '1700218120754', 'doctor', 1, 20000);         
INSERT INTO Employees VALUES (22, 'Tomescu', 'Vasile', '1780615125740','doctor', 2, 1800);     
INSERT INTO Employees VALUES (23, 'Sabau', 'Mihaela', '2751002333120','doctor', 3, 18500);       
INSERT INTO Employees VALUES (24, 'Moldovan', 'Ana','2800305126345', 'asistenta', 4, 5000);       
INSERT INTO Employees VALUES (25, 'Felecan', 'Naomi', '2780910125320', 'asistenta', 5, 4350);        
INSERT INTO Employees VALUES (26, 'Cadis', 'Maria', '2770517120654', 'asistenta', 6, 4550);         
INSERT INTO Employees VALUES (27, 'Deac', 'Sefora', '2791205120636', 'infirmiera', 7, 2900);          
INSERT INTO Employees VALUES (28, 'Sandru', 'Delia', '2650505125455', 'infirmiera', 8, 2650);      
INSERT INTO Employees VALUES (29, 'Pop', 'Dumitru', '1720606125235', 'manager', 9, 24000);         
INSERT INTO Employees VALUES (30, 'Prodan', 'Vasile', '1701205120554', 'portar', 10, 2730);          
INSERT INTO Employees VALUES (31, 'Dumitrache', 'Camelia', '2791105120756', 'administrator', 11, 2655);     
INSERT INTO Employees VALUES (32, 'Tomescu', 'Simona', '2681113125442', 'contabil', 12, 2900);    
```
```
INSERT INTO Hospitalization VALUES ('RESP138', 'SPR2100', 1, '17A', 'Traheo-bronsita acuta', 'TR1', '2022-09-15 10:30:05', '2022-09-19 13:40:00', 'LAB301', 'RPR255');
INSERT INTO Hospitalization VALUES ('RESP139', 'SPR2101', 2, '17A', 'Pneumonie acuta', 'TR2', '2022-09-15 11:00:00', '2022-09-20 14:10:09', 'LAB302', 'RPR256');
INSERT INTO Hospitalization VALUES ('RESP140', 'SPR2102', 3, '17B', 'Angina acuta', 'TR3', '2022-09-15 20:05:05', '2022-09-20 11:10:05', 'LAB303', 'RPR257');
INSERT INTO Hospitalization VALUES ('RESP141', 'SPR2103', 4, '18A', 'Angina acuta', 'TR4', '2022-09-16 09:00:05', '2022-09-21 13:14:00', 'LAB304', 'RPR258');
INSERT INTO  Hospitalization VALUES ('RESP142', 'SPR2104', 5, '18B', 'Pneumonie bazala stg', 'TR5', '2022-09-16 10:25:00', '2022-09-22 14:50:00', 'LAB305','RPR259' );
INSERT INTO  Hospitalization VALUES ('RESP143', 'SPR2105', 6, '18B', 'Bronsita acuta', 'TR6', '2022-09-17 10:25:00', '2022-09-22 14:50:00', 'LAB306','RPR260' );
INSERT INTO Hospitalization  VALUES ('RESP144', 'SPR2106', 7, '19B', 'Pneumonie bazala dr', 'TR7', '2022-09-17 10:25:00', '2022-09-22 14:50:00', 'LAB307','RPR261' );
INSERT INTO Hospitalization VALUES ('RESP145', 'SPR2107', 8, '20A', 'Angina acuta', 'TR8', '2022-09-18 09:00:05', '2022-09-21 13:14:00', 'LAB308','RPR262');
INSERT INTO Hospitalization VALUES ('RESP146', 'SPR2108', 9, '20B', 'Pneumonie bazala dr', 'TR9', '2022-09-18 10:25:00', '2022-09-23 14:50:00', 'LAB309', 'RPR263');
INSERT INTO Hospitalization VALUES ('RESP147', 'SPR2109', 10, '20B', 'Pneumonie bazala stg', 'TR10', '2022-09-19 10:25:00', '2022-09-23 14:50:00', 'LAB310', 'RPR264');
```
```
INSERT INTO Treatment VALUES ('TR1','RESP138' , 'Augmentin', '1,2g', '08:00, 20:00', 'intravenos');
INSERT INTO Treatment VALUES ('TR2', 'RESP139', 'Claritromicina', '500mg', '08:00, 20:00', 'perfuzabil');
INSERT INTO Treatment VALUES ('TR3', 'RESP140', 'Augmentin', '1,2g', '08:00, 20:00', 'intravenos');
INSERT INTO Treatment VALUES ('TR4','RESP141' , 'Augmentin', '1,2g', '08:00, 20:00', 'intravenos');
INSERT INTO Treatment VALUES ('TR5', 'RESP142', 'Claritromicina', '500mg', '08:00, 20:00', 'perfuzabil');
INSERT INTO Treatment VALUES ('TR6', 'RESP143', 'Cefuroxim', '750mg', '08:00, 20:00', 'perfuzabil');
INSERT INTO Treatment VALUES ('TR7', 'RESP144', 'Claritromicina', '500mg', '08:00, 20:00', 'perfuzabil');
INSERT INTO Treatment VALUES ('TR8', 'RESP145' , 'Augmentin', '1,2g', '08:00, 20:00', 'intravenos');
INSERT INTO Treatment VALUES ('TR9', 'RESP146', 'Claritromicina', '500mg', '08:00, 20:00', 'perfuzabil');
INSERT INTO Treatment VALUES ('TR10','RESP147' , 'Claritromicina', '500mg', '08:00, 20:00', 'perfuzabil');
```

```
INSERT INTO Laboratory VALUES ('LAB301', 'RESP138', 'ASLO', '2022-09-15', NULL);
INSERT INTO Laboratory VALUES ('LAB302', 'RESP139', 'ExFaringian', '2022-09-15', NULL);
INSERT INTO Laboratory VALUES ('LAB303', 'RESP140' , 'CRP', '2022-09-16', NULL);
INSERT INTO Laboratory VALUES ('LAB304', 'RESP141', 'ExFaringian', '2022-09-16', NULL);
INSERT INTO Laboratory VALUES ('LAB305', 'RESP142', 'CRP', '2022-09-16', NULL);
INSERT INTO Laboratory VALUES ('LAB306', 'RESP143', 'ASLO', '2022-09-17', NULL);
INSERT INTO Laboratory VALUES ('LAB307', 'RESP144', 'ExFaringian', '2022-09-17', NULL);
INSERT INTO Laboratory VALUES ('LAB308', 'RESP145', 'ASLO', '2022-09-18', NULL);
INSERT INTO Laboratory VALUES ('LAB309', 'RESP146', 'Radiografie pulmonara', '2022-09-18', NULL);
INSERT INTO Laboratory VALUES ('LAB310', 'RESP147', 'Radiografie pulmonara', '2022-09-19', NULL);
```
```
INSERT INTO Farmacy VALUES ('RPR255', 'RESP138', 'Augmentin', 'Ser fiziologic', 'Paracetamol', NULL, NULL, NULL, 'TR1');
INSERT INTO Farmacy VALUES ('RPR256', 'RESP139', 'Claritromicina', 'Ser fiziologic', 'Paracetamol', NULL, NULL, NULL, 'TR2');
INSERT INTO Farmacy VALUES ('RPR257', 'RESP140', 'Augmentin', 'Ser fiziologic', 'Paracetamol', NULL, NULL, NULL, 'TR3');
INSERT INTO Farmacy VALUES ('RPR258', 'RESP141', 'Augmentin', 'Ser fiziologic', 'Paracetamol', NULL, NULL, NULL, 'TR4');
INSERT INTO Farmacy VALUES ('RPR259', 'RESP142', 'Claritromicina', 'Ser fiziologic', 'Paracetamol', NULL, NULL, NULL, 'TR5');
INSERT INTO Farmacy VALUES ('RPR260', 'RESP143', 'Cefuroxim', 'Ser fiziologic', 'Paracetamol', 'Nurofen', NULL, NULL, 'TR6');
INSERT INTO Farmacy VALUES ('RPR261', 'RESP144', 'Claritromicina', 'Ser fiziologic', 'Paracetamol', NULL, NULL, NULL, 'TR7');
INSERT INTO Farmacy VALUES ('RPR262', 'RESP145', 'Augmentin', 'Ser fiziologic', 'Paracetamol', NULL, NULL, NULL, 'TR8');
INSERT INTO Farmacy VALUES ('RPR263', 'RESP146', 'Claritromicina', 'Ser fiziologic', 'Paracetamol', NULL, NULL, NULL, 'TR9');
INSERT INTO Farmacy VALUES ('RPR264', 'RESP147', 'Claritromicina', 'Ser fiziologic', 'Paracetamol', NULL, NULL, NULL, 'TR10');
```


```
INSERT INTO OutPatients VALUES (358, 2451, 'Cristorean', 'Maria', '2500504124656', 'Cluj Napoca', 'Campului 72', 'respirator', '0745235562', '0755454545');
INSERT INTO OutPatients VALUES (359, 2452, 'Pop', 'Voicu', '1641212125124', 'Dej', 'Ciresilor 10', 'respirator', '0771343264', '0755455210');
INSERT INTO OutPatients VALUES (360, 2453, 'Brad',  'Adrian', '1790823120554', 'Cluj Napoca', 'Tineretului 19', 'respirator', '0757000241', '0745414545');
```
```
INSERT INTO OutPatients (OutPatientID, PacHospID, PacLastName, PacFirstName, CNP, City, Address, PacType, PacPhone, FamilyNo)
 VALUES (361, 2454, 'Brad', 'Adriana', '2790823120554', 'Cluj Napoca', 'Tineretului 19', 'respirator', '0755702241', '0745484545');
```

 
  After the insert, in order to prepare the data to be better suited for the testing process, I updated some data in the following way:

 
- **UPDATE** Laboratory SET TestResults ='negative' WHERE LabTestID='Lab304';
- **UPDATE** Laboratory SET TestResults ='positive' WHERE LabTestID='Lab304';

  <h3>DQL (Data Query Language)</h3>

After the testing process, I deleted the data that was no longer relevant in order to preserve the database clean: 


- **DELETE** FROM OutPatients WHERE City='Cluj-Napoca';
In order to simulate various scenarios that might happen in real life I created the following queries that would cover multiple potential real-life situations:
<br>

- SELECT * FROM InPatients;
SELECT * FROM PatientFile;
SELECT * FROM Treatment;
SELECT PatientData.PacFileID, PatientData.PacLastName, PatientData.PacFirstName,
Hospitalization.Diagnostic, Treatment.MedName, Treatment.MedicineDose 
FROM PatientData
INNER JOIN Hospitalization ON PatientData.PacFileID=Hospitalization.PacFileID
INNER JOIN Treatment ON PatientData.PacFileID=Treatment.PacFileID;

- SELECT * FROM PatientData
CROSS JOIN Laboratory ON PatientData.PacFileID=Laboratory.PacFileID;

- SELECT Hospitalization.PacFileID, Treatment.TreatID FROM Hospitalization LEFT JOIN Treatment ON Hospitalization.TreatID=Treatment.TreatID;
--The statement returns all records from Hospitalization and the matches records from Treatment;


- SELECT EmpCNP  AS CNP FROM Employees 
UNION ALL
SELECT CNP FROM PatientData
ORDER BY CNP;

- SELECT * FROM Employees;
SELECT EmpLastName, EmpFirstName FROM Employees WHERE EXISTS (
SELECT Salary FROM Employees WHERE EmpLastName>'Sabau');

- SELECT * FROM PatientData;
SELECT COUNT (PacFileID), City FROM PatientData GROUP BY City ORDER BY COUNT (PacFileID) ASC; 


- SELECT * FROM PatientData;
SELECT COUNT(PacFileID) FROM PatientData;


- SELECT * FROM Employees;
SELECT MAX(EmpID) AS Maxim FROM Employees;

- SELECT AVG(Salary) AS Media FROM Employees;
SELECT * FROM Employees;


- SELECT CONCAT(City, Address) AS FullAddress FROM PatientData;
SELECT CONCAT_WS('*', PacLastName, PacFirstName) AS FullName FROM PatientData;

- SELECT LEFT ('Tomescu', 4) AS String;
- SELECT Dateofadmission, Diagnostic FROM Hospitalization WHERE Dateofadmission='2022-09-17' AND Diagnostic='Bronsita acuta';
- SELECT Dateofadmission, Diagnostic FROM Hospitalization WHERE Dateofadmission='2022-09-17' OR Diagnostic='Pneumonie bazala';
SELECT * FROM PatientData WHERE City LIKE 'Nap%';

- SELECT EmpCNP SUM(Salary)
FROM Employees
GROUP BY EmpCNP
HAVING SUM(Salary)>4000;






<h2>Conclusions</h2>

A useful database for the respiratory department in a hospital has been created. The admin user gave the access to all staff needed. All the records should be updated daily for the patients' files, treatment, blood tests and other investigations, medication.


