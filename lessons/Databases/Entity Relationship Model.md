## **Creating a New Database**

Steps to create a new database application  
1. Requirements definition and analysis
2. **`Conceptual design (use Entity-Relationship model)`**
3. Logical design (use Relational Data model)
4. Physical Design (index, application program, etc.)
5. Implementation
6. Maintenance

![[Pasted image 20250211213741.png]]

In this chapter, we follow the traditional approach of concentrating on the database structures and constraints during **`conceptual database design`**. 

We present high-level conceptual data model concepts using the **Entity-Relationship** (**ER**) **model**. This model and its variations are frequently used for the conceptual database design.

We also present the diagrammatic notation associated with the ER model, known as **ER diagrams**.   
## **Conceptual Design**

During **conceptual design** we form a **`schema`**. 
A schema is a concise description of the data requirements and includes:
1. entity types
2. entity constraints
3. relationships between entities
  
We use **ER diagrams** to model entities and the relationships between them. 

During or after the **conceptual schema design**, the basic data model operations can be used to specify the **high-level user queries and operations** identified during functional analysis. 

## **Logical Design**

- The next step in database design is the actual implementation of the database, using a commercial DBMS.

- Most current commercial DBMSs use an implementation data model—such as the relational or the object-relational database model—so the conceptual schema is transformed from the high-level data model into the implementation data model. 

- This step is called **logical design** or **data model mapping**; its result is a database schema in the implementation data model of the DBMS. Data model mapping is often automated or semiautomated within the database design tools. 

## **Physical Design**

- The last step is the **physical design** phase, during which the internal storage structures, file organizations, indexes, access paths, and physical design parameters for the database files are specified. 

- In parallel with these activities, application programs are designed and implemented as database transactions corresponding to the high-level transaction specifications. 

- We present only the basic ER model concepts for conceptual schema design in this chapter.