<h1>Database Project for **HospitalDepartment**</h1>

The scope of this project is to use all the SQL knowledge gained throught the Software Testing course and apply them in practice.

Application under test: **HospitalDepartment**

Tools used: MySQL Workbench

Database description: **A continuous updated databases in a hospital make the work much easier for all staff. The created database, named HospitalDepartment, contains the information related to respiratory department, emplooyees, patients, patients' information, treatment, investigations and other relevant details.**

<ol>
<li> </li>
<br>
You can find below the database schema that was generated through Reverse Engineer and which contains all the tables and the relationships between them.

The tables are connected in the following way:

<ul>
  <li> **RespDepartment**  is connected with **Employee** through a **one to many** relationship which was implemented through **RespDepartment.DepID** as a primary key and **Employee.EmpID** as a foreign key</li>
  <li> **Hospitalization**  is connected with **RespDepartment** through a **one to many** relationship which was implemented through **Hospitalization.PacFileID** as a primary key and **Hospitalization.DepID** as a foreign key</li>
  <li> **PatientData**  is connected with **Hospitalization** through a **one to many** relationship which was implemented through **nPatientData.PacHospID** as a primary key and **Hospitalization.PacFileID** as a foreign key</li>
 <li> **Treatment**  is connected with **Hospitalization** through a **one to manye** relationship which was implemented through **Treatment.TreatID** as a primary key and **Hospitalization.TreatID** as a foreign key</li>
 <li> **Laboratory**  is connected with **Hospitalization** through a **one to manye** relationship which was implemented through **Laboratory.LabTestID** as a primary key and **Hospitalization.LabTestID** as a foreign key</li>
 <li> **Farmacy**  is connected with **Hospitalization** through a **one to manye** relationship which was implemented through **Farmacy.FarmID** as a primary key and **Hospitalization.TreatID*** as a foreign key</li>

</ul><br>

<li>Database Queries</li><br>

<ol type="a">
  <li>DDL (Data Definition Language)</li>

  The following instructions were written in the scope of CREATING the structure of the database (CREATE INSTRUCTIONS)

  **Inserati aici toate instructiunile de CREATE pe care le-ati scris, atat create database cat si create table**

  After the database and the tables have been created, a few ALTER instructions were written in order to update the structure of the database, as described below:

  **Inserati aici toate instructiunile de ALTER pe care le-ati scris. Incercati sa includeti instructiuni cat mai variate cum ar fi:**
 **- schimbare nume tabela**
 **- adaugare sau stergere coloana**
 **- redenumire coloana**
 **- adaugare proprietati coloana (ex: adaugare auto-increment)**
 **- modificare proprietati coloana (ex: modificare tip de data, modificare pozitie coloana etc)**
 **- adaugare cheie primara sau secundara (daca nu a fost deja adaugata la crearea tabelei)**
 
  
  <li>DML (Data Manipulation Language)</li>

  In order to be able to use the database I populated the tables with various data necessary in order to perform queries and manipulate the data. 
  In the testing process, this necessary data is identified in the Test Design phase and created in the Test Implementation phase. 

  Below you can find all the insert instructions that were created in the scope of this project:

  **Inserati aici toate instructiunile de INSERT pe care le-ati scris. Incercati sa folositi atat insert pe toate coloanele (fara sa precizati pe ce coloane se face insert) cat si insert pe cateva coloane (care necesita mentionarea explicita a coloanelor pe care se face insert). De asemenea, incercati sa acoperiti situatia in care inserati mai multe randuri in acelasi timp**

  After the insert, in order to prepare the data to be better suited for the testing process, I updated some data in the following way:

  **Inserati aici toate instructiunile de UPDATE pe care le-ati scris folosind filtrarile necesare astfel incat sa actualizati doar datele de care aveti nevoie**


  <li>DQL (Data Query Language)</li>

After the testing process, I deleted the data that was no longer relevant in order to preserve the database clean: 

**Inserati aici toate instructiunile de DELETE pe care le-ati scris folosind filtrarile necesare astfel incat sa stergeti doar datele de care aveti nevoie**

In order to simulate various scenarios that might happen in real life I created the following queries that would cover multiple potential real-life situations:

**Inserati aici toate instructiunile de SELECT pe care le-ati scris folosind filtrarile necesare astfel incat sa extrageti doar datele de care aveti nevoie**
**Incercati sa acoperiti urmatoarele:**<br>
**- where**<br>
**- AND**<br>
**- OR**<br>
**- NOT**<br>
**- like**<br>
**- inner join**<br>
**- left join**<br>
**- OPTIONAL: right join**<br>
**- OPTIONAL: cross join**<br>
**- functii agregate**<br>
**- group by**<br>
**- having**<br>
**- OPTIONAL DAR RECOMANDAT: Subqueries - nu au fost in scopul cursului. Puteti sa consultati tutorialul [asta](https://www.techonthenet.com/mysql/subqueries.php) si daca nu intelegeti ceva contactati fie trainerul, fie coordonatorul de grupa**<br>

</ol>

<li>Conclusions</li>

**Inserati aici o concluzie cu privire la ceea ce ati lucrat, gen lucrurile pe care le-ati invatat, lessons learned, un rezumat asupra a ceea ce ati facut si orice alta informatie care vi se pare relevanta pentru o concluzie finala asupra a ceea ce ati lucrat**

</ol>
