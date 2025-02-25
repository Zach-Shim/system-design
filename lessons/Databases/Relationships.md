SQLite and PostgreSQL are relational database management systems (RDMBS).
## **Relationship**

When an attribute of one entity type refers to another entity type, those two entities are said to have a **relationship**.

A relationship is where you have multiple entities (tables) that contain related data (attributes), and the data is linked by a common value that is stored in both tables.

![Diagram of a database relationship.](https://www.quackit.com/pix/sqlite/tutorial/sqlite_relationship_example.png)
## **Relationship Type**

- A **relationship type R** defines an association between **_n_** participating **entity types** E1, E2, ..., E<sub>n</sub> defined in a **relationship set**—among entities from these entity types.
- A **relationship type** can have more than two entities participating in the relationship.
## **Relationship Instance**

- A **relationship instance** **ri** of type **R** is an association of **_individual_** entity types.
- Each entity instance *e<sub>j</sub>* in *r<sub>i</sub>* is a member of entity set *E<sub>j</sub>*
- The collection of all relationships instances in *r<sub>i</sub>* of type **R** is called a **relationship set**.

As is the same case for entity types & sets `E`, a relationship type & set are referred to by the same name, `R`. 
## **Entity Relationship (ER) Diagram Notation**

In ER diagrams, relationship types are displayed as **diamond-shaped boxes** connected by **straight lines** to the **rectangular boxes** representing the participating **entity types**. 

![[Pasted image 20250224183203.png]]
## **Relationship Examples**

Consider a relationship type **WORKS_FOR**.

WORKS_FOR defines a relationship between the two entity types 
1. **EMPLOYEE**
2. **DEPARTMENT**

WORKS_FOR associates one employee to one department, and each DEPARTMENT entity can have one or more EMPLOYEE entities.

Figure 7.9 illustrates this example, where each relationship instance *r<sub>i</sub>* is shown to connect the EMPLOYEEs with DEPARTMENTs. 
- employees e1, e3, and e6 work for department d1; 
- employees e2 and e4 work for department d2; 
- employees e5 and e7 work for department d3. 

  
![[Pasted image 20250224231924.png]]

---
## **Degree of Relationship Type**

The **degree of a relationship type** is the **number of participating entity types**. 

1. **Binary Relationship Type:** 
   A relationship type of degree two (two participating entity types) is called **binary**
   
   WORKS_FOR is a binary relationship with a degree two.
   
   Relationships can generally be of any degree, but the ones most common are binary relationships. 

2. **Ternary Relationship Type:** A relationship type of degree three (three participating entity types) is called **ternary**
   
   SUPPLY, shown in Figure 7.10, is ternary where each relationship instance _ri_ associates three entities—a supplier _s_, a part _p_, and a project _j_—whenever _s_ supplies part _p_ to project _j_. 

  ![[Pasted image 20250224232336.png]]

---
## **Relationships as Attributes**

It is sometimes convenient to think of a binary relationship type in terms of attributes.

Consider the WORKS_FOR relationship type in Figure 7.9. 
One can think of an attribute called Department of the EMPLOYEE entity type, where the value of Department for each EMPLOYEE entity is (a reference to) the DEPARTMENT entity for which that employee works. 

Hence, the value set for this Department attribute is the set of all DEPARTMENT entities, which is the DEPARTMENT entity set. 

This is what we did in Figure 7.8 when we specified the initial design of the entity type EMPLOYEE for the COMPANY database. However, when we think of a binary relationship as an attribute, we always have two options. 

In this example, the alternative is to think of a multivalued attribute Employee of the entity type DEPARTMENT whose values for each DEPARTMENT entity is the set of EMPLOYEE entities who work for that department. 

The value set of this Employee attribute is the power set of the EMPLOYEE entity set. Either of these two attributes—Department of EMPLOYEE or Employee of DEPARTMENT—can represent the WORKS_FOR relationship type. If both are represented, they are constrained to be inverses of each other.

## **Role Names and Recursive Relationships**

- Each entity type that participates in a relationship type plays a particular role in the relationship. 
- The **role name** signifies the role that a participating entity from the entity type plays in each relationship instance and helps to explain what the relationship means. 

  

- For example, in the WORKS_FOR relationship type, EMPLOYEE plays the role of _employee_ or _worker_ and DEPARTMENT plays the role of _department_ or _employer_. 

  

- Role names are not technically necessary in relationship types where all the participating entity types are distinct, since each participating entity type name can be used as the role name. 

  

- However, in some cases the **_same_** entity type participates more than once in a relationship type in **_different roles_**. 

  

- In such cases the role name becomes essential for distinguishing the meaning of the role that each participating entity plays. Such relationship types are called **recursive relationships**. 

  

- In recursive relationships, role names are required (specify role that each instance plays).

- This way, we are able to tell which instance is which in the entity type

  

- Figure 7.11 shows an example. The SUPERVISION relationship type relates an employee to a supervisor, where both employee and supervisor entities are members of the same EMPLOYEE entity set. 
- Hence, the EMPLOYEE entity type **_participates twice_** in SUPERVISION: 

  

1. once in the role of _supervisor_ (or _boss_), 

and 

1. once in the role of _supervisee_ (or _subordinate_). 

  

- Each relationship instance _ri_ in SUPERVISION associates two employee entities _ej_ and _ek_, one of which plays the role of supervisor and the other the role of supervisee. 

  

- In Figure 7.11, the lines marked ‘1’ represent the supervisor role, and those marked ‘2’ represent the supervisee role; hence, _e_1 supervises _e_2 and _e_3, _e_4 supervises _e_6 and _e_7, and _e_5 supervises _e_1 and _e_4. In this example, each relationship instance must be connected with two lines, one marked with ‘1’ (supervisor) and the other with ‘2’ (supervisee).