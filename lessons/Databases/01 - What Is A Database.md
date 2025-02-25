## **What is a Database?**

A **database** is a collection of **related data**. 
By **data**, we mean known **facts** that can be recorded and that have **implicit meaning**. 

A database is a container of tables. One database can contain one or more tables.
For example, an inventory tracking system that uses three tables is not three databases, but one database that contains three tables. 

The end users of a database may perform **business transactions** or **events may happen** that cause the **information in the database to change**.

---
## **Database Management System (DBMS)**

A **database management system (DBMS)** is a **collection of programs** that enables users to create and maintain a database. 

The DBMS is a _general-purpose software system_ that facilitates the lifecycle of a database.
We can define the lifecycle of a database through the same acronym:
1. **_Defining_**
	1. data types (int, char, string, etc.), 
	2. structures (relationships between data), 
	3. constraints (saved as metadata – descriptive information of a database)
2. **_Building_**
	1. creating tables and data to store in the database
3. **_Manipulating_**
	1. querying data
	2. inserting data
	3. updating data
4. **_Sharing_**
	1. allows multiple users and programs to access the database simultaneously (concurrent access). 

---
## **Application-Database Interaction**

An **application program** accesses a database by sending **queries** (**requests for data**) to the DBMS.
- A **query** typically causes some data to be **retrieved**
- A **transaction** may cause some data to be **read** and some data to be **written** into the database. 

We call the following components a **Database System**:
- **Applications** that query a database …
- **DBMS software** that processes application queries
- **Database** where data is physically stored. 

![[Pasted image 20250211195337.png]]

---
## Example
**University** Database 
- students
- courses
- sections
- grades
- prerequisites

![[Pasted image 20250211211553.png]]

![[Pasted image 20250211211716.png]]

##### **Step 1: Defining**

To **_define_** this database, we must specify the following for the records of each file.
1. **structure**
2. **types**
3. **constraints**

**STUDENT**
```sql
Name string not null
Number int unique
Class string in ('Freshman', 'Sophomore', 'Junior', 'Senior')
Major string
```
 
**COURSE**
```sql
Name string not null
Number int unique
Credits int in (1,2,3,4,5)
Department string
```

... and so on

##### **Step 2: Build**

To **_build_** the UNIVERSITY database, **we insert data** in each table.

Note how certain tables can be related.
For example, the record for Smith in the STUDENT file is related to two records in the GRADE_REPORT file that specify Smith’s grades in two sections.   

Most medium-size and large databases include many types of records and have **_many relationships_** among the records. 

This means we must be wary of the `order we insert items`. 
If we insert a new GRADE_REPORT for a student, but that student is had not yet been inserted as a record, then we have a problem. 
##### **Step 3: Manipulation**

Database **_manipulation_** involves **querying and updating** a database. 

Examples of **queries** are as follows: 
- Retrieve the transcript—a list of all courses and grades—of ‘Smith’
- List the names of students who took the section of the ‘Database’ course offered in fall 2008 and their grades in that section 
- List the prerequisites of the ‘Database’ course 

Examples of **updates** include the following: 
- Change the class of ‘Smith’ to sophomore
- Create a new section for the ‘Database’ course for this semester
- Enter a grade of ‘A’ for ‘Smith’ in the ‘Database’ section of last semester 

These informal queries and updates must be specified precisely in the **query language** of the DBMS before they can be processed. 

---
## **ANSI-SPARC Three-level Architecture**


When designing a new application that uses a database, there are phases we go through.

`Step 1:` **Requirements specification and analysis**
- What kind of data do we need to store?
- Who is using the database?
- etc.…

`Step 2:` **Conceptual Design**
- How does the data look in terms of **relationships** with other data?
- Chapter 7 introduces a model called the **Entity-Relationship Model** that allows us to model relationships among tables.

`Step 3:` **Logical Design**
- Conceptual design tables/diagrams are **translated** into logical design that can be expressed as a data model implemented in a commercial DBMS.
- A popular data model is the **Relational Model** that we use from Chapter 3 onward.

`Step 4:` **Physical Design**
- Logical design is translated into physical design, which is how data is physically stored on disk. 
- This is the low level – ‘store at this block’ or ‘store at this address’ type of design.

![[Pasted image 20250211212247.png]]

---
## **Databases vs Files for Storing Data**  

**File Processing Approach**
Before Database Management Systems, most ‘database’ work was done by programming directly with storage files.

In such **traditional** **file processing**, each user must define and implement the file logic for each table (group of records) for a specific software application.   

For example, we may have a single application where:

- One user, the _grade reporting office,_ may keep files on students and their grades. 
	They will need to implement programs to print a student’s transcript and to enter new grades are implemented as part of the application. 

- A second user, the _accounting office_, may keep track of students’ fees and their payments. 

Although both users are interested in data about students, each user maintains separate files— and programs to manipulate these files—because each requires some data not available from the other user’s files. 

This **redundancy** in defining and storing data results in **wasted storage space** and in redundant efforts to maintain common up-to-date data. 
#### **Database Approach**
In the database approach, **a single repository maintains data that is defined once and then accessed by various users**. 

In file systems, each application is **free to name data elements independently**. 
In contrast, in a database, the **names or labels of data are defined once**, and used repeatedly by queries, transactions, and applications. 

The main characteristics of the database approach versus the file-processing approach are the following: 
- Self-describing nature of a database system
- Insulation between programs and data, and data abstraction s Support of multiple views of the data
- Sharing of data and multiuser transaction processing 