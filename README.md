# IMPLEMENT-THE-DATABASE-USING-SQL-DATA-DEFINITION-WITH-CONSTRAINTS-VIEWS-
# AIM: 
To create and modifying a table using DDL commands, create Constraints and Views for 
Tables in the Database. 
# DESCRIPTION: 
# DATA DEFINITION LANGUAGE (DDL): The Data Definition Language (DDL) is used to create 
and destroy databases and database objects. These commands will primarily be used by database 
administrators during the setup and removal phases of a database project. 
Let's take a look at the structure and usage of four basic DDL commands: 
1. CREATE 
2. DESC 
3. ALTER 
4. DROP 
5. RENAME 
 
 
## 1. CREATE 
### (a) CREATE TABLE: This is used to create a new relation (table) 
Syntax: CREATE TABLE <relation_name/table_name > 
(field_1 data_type(size),field_2 data_type(size), .. . ); 
Example: 
```
SQL> CREATE TABLE Student (sno NUMBER (3), sname CHAR (10), class CHAR (5));
```
 
 
## 2. DESC – Command used to view the table structure. 
Syntax : desc <table name>; 
Example : 
```
desc Student;
```
 
 
## 3. ALTER: 
### (a) ALTER TABLE ...ADD...: This is used to add some extra fields into existing relation. 
Syntax: ALTER TABLE relation_name ADD (new field_1 data_type(size), new field_2 
data_type(size),..); 
Example:
```
SQL>ALTER TABLE std ADD (Address CHAR(10));
```
 
  
 
 
### (b) ALTER TABLE...MODIFY...: This is used to change the width as well as data 
type of fields of existing relations. 
Syntax: ALTER TABLE relation_name MODIFY (field_1 newdata_type(Size), field_2 
newdata_type(Size), ... field_newdata_type(Size)); 
Example:
```
SQL>ALTER TABLE student MODIFY(sname VARCHAR(10), class VARCHAR(5)); 
```
 
 
### c) ALTER TABLE..DROP ...... This is used to remove any field of existing relations. 
Syntax: ALTER TABLE relation_name DROP COLUMN (field_name); 
Example:
```
SQL>ALTER TABLE student DROP column (sname);
```
 
### d) ALTER TABLE..RENAME ..... This is used to change the name of fields in existing relations. 
Syntax: ALTER TABLE relation_name RENAME COLUMN (OLD field_name) to 
(NEW field_name); 
Example: 
```
SQL>ALTER TABLE student RENAME COLUMN sname to stu_name;
```
 
 
## 4. DROP TABLE: This is used to delete the structure of a relation. It permanently deletes 
the records in the table. 
Syntax: DROP TABLE relation_name; 
Example:
```
SQL>DROP TABLE std;
```
 
## 5. RENAME: It is used to modify the name of the existing database object. 
Syntax: RENAME TABLE old_relation_name TO new_relation_name; 
Example: SQL>RENAME TABLE std TO std1; 
 
# SQL CONSTRAINTS: 
➢ SQL constraints are used to specify rules for the data in a table. Constraints are used to limit the 
type of data that can go into a table. 
➢ This ensures the accuracy and reliability of the data in the table. If there is any violation between 
the constraint and the data action, the action is aborted. 
➢ Constraints can be column level or table level. Column level constraints apply to a column, and 
table level constraints apply to the whole table. 
➢ It can be specified when the table is created (using CREATE TABLE statement) or after the 
table is created (using ALTER TABLE statement). 
The following constraints are commonly used in SQL: 
NOT NULL - Ensures that a column cannot have a NULL value 
 
  
 
 
### UNIQUE - Ensures that all values in a column are different 
### PRIMARY KEY - A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in 
a table 
### FOREIGN KEY - Prevents actions that would destroy links between tables 
### CHECK - Ensures that the values in a column satisfies a specific condition 
### DEFAULT - Sets a default value for a column if no value is specified 
### CREATE INDEX - Used to create and retrieve data from the database very quickly 
 
 
## 1. NOT NULL: When a column is defined as NOTNULL, then that column becomes a 
mandatory column. It implies that a value must be entered into the column if the record is to 
be accepted for storage in the table. 
Syntax: 
CREATE TABLE Table_Name (column_name data_type (size) NOT NULL, ); 
Example: 
```
CREATE TABLE student (sno NUMBER(3)NOT NULL, name CHAR(10));
```
 
 
## 2. UNIQUE: The purpose of a unique key is to ensure that information in the column(s) is 
unique i.e. a value entered in column(s) defined in the unique constraint must not be repeated 
across the column(s). A table may have many unique keys. 
Syntax: 
CREATE TABLE Table_Name(column_name data_type(size) UNIQUE, ….); 
Example: 
```
CREATE TABLE student (sno NUMBER(3) UNIQUE, name CHAR(10));
```
 
 
## 3. CHECK: Specifies a condition that each row in the table must satisfy. To satisfy the 
constraint, each row in the table must make the condition either TRUE or unknown (due to a 
null). 
Syntax: 
CREATE TABLE Table_Name(column_name data_type(size) CHECK(logical expression), ….); 
Example: 
```
CREATE TABLE student (sno NUMBER (3), name CHAR(10), class CHAR(5),CHECK(class 
IN(‘CSE’,’CAD’,’VLSI’));
```
 
## 4. PRIMARY KEY: A field which is used to identify a record uniquely. A column or 
combination of columns can be created as primary key, which can be used as a reference 
 from other tables. A table contains primary key is known as Master Table. 
✓ It must uniquely identify each record in a table. 
✓ It must contain unique values. 
✓ It cannot be a null field. 
✓ It cannot be multi port field. 
✓ It should contain a minimum no. of fields necessary to be called unique. 
Syntax: 
CREATE TABLE Table_Name(column_name data_type(size) PRIMARY KEY, ….); 
Example: 
```
CREATE TABLE faculty (fcode NUMBER(3) PRIMARY KEY, fname CHAR(10));
```
 
 
## 5. FOREIGN KEY: It is a table level constraint. We cannot add this at column level. To 
reference any primary key column from other table this constraint can be used. The table in 
which the foreign key is defined is called a detail table. The table that defines the primary 
key and is referenced by the foreign key is called the master table. 
Syntax: CREATE TABLE Table_Name(column_name data_type(size) 
FOREIGN KEY(column_name) REFERENCES table_name); 
Example: 
```
CREATE TABLE subject (scode NUMBER (3) PRIMARY KEY, subname 
CHAR(10),fcode NUMBER(3), FOREIGN KEY(fcode) REFERENCE faculty );
```
 
## 6. DEFAULT: The DEFAULT constraint is used to insert a default value into a column. The 
default value will be added to all new records, if no other value is specified. 
Syntax: 
CREATE TABLE Table_Name(col_name1,col_name2,col_name3 DEFAULT ‘<value>’); 
Example: 
```
CREATE TABLE student (sno NUMBER(3) UNIQUE, name CHAR(10),address VARCHAR(20) 
DEFAULT ‘Aurangabad’);
```
 
 
### VIEW: In SQL, a view is a virtual table based on the RESULT-set of an SQL statement. 
✓ A view contains rows and columns, just like a real table. The fields in a view are fields from one 
or more real tables in the database. 
✓ You can add SQL functions, WHERE, and JOIN statements to a view and present the data as 
✓ if the data were coming from one single table. 
✓ A view is a virtual table, which consists of a set of columns from one or more tables. It is 
✓ similar to a table but it does not store in the database. View is a query stored as an object. 
 
Syntax: CREATE VIEW <view_name> AS SELECT <set of fields> 
FROM relation_name WHERE (Condition) 
Example: 
```
SQL> CREATE VIEW employee AS SELECT empno,ename,job FROM EMP WHERE job = 
‘clerk’; 
SQL> View created.
```
Example: 
```
CREATE VIEW [Current Product List] AS 
SELECT ProductID, ProductName 
FROM Products 
WHERE Discontinued=No; 
UPDATING A VIEW : A view can updated by using the following syntax : 
Syntax : CREATE OR REPLACE VIEW view_name AS 
SELECT column_name(s) 
FROM table_name 
WHERE condition 
DROPPING A VIEW: A view can deleted with the DROP VIEW command. 
Syntax: DROP VIEW <view_name> ;
```
 
 
 # RESULT: 
Thus, creating and modifying a table using DDL commands, create Constraints and Views for 
Tables in the Database has been completed successfully.
