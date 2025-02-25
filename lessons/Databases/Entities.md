## **Entity Definition**

An **`entity`** may be defined as a thing that is capable of an independent existence that can be uniquely identified.

An **`entity`** is a thing that exists either:
- **Physically** (i.e. person, car, employee, etc.)
- **Conceptually** (i.e., company, job, course, etc.)

Entities can be thought of as **`nouns`**.

----
## **Entity Attributes**

Every entity has attributes.
**`Attributes`** are the **properties that describe** an entity. 

For Example: 
An Employee entity may be described by the employee’s name, age, address, salary, and job.

- Several **types of attributes** occur in the ER model: 
1. **Simple**
2. **Derived**
3. **Composite**
4. **Multi-Valued**
5. **Complex**

#### **1. Simple Attributes**
Attributes that are **not divisible** are called **simple** or **atomic attributes**. 

**Composite Attributes**
**Composite Attributes** are attributes that logically have multiple parts to them.
Composite attributes can be **divided** into smaller subparts, which represent more basic attributes with independent meaning.

Figure 7.3 shows two entities and the values of their attributes. 

![[Pasted image 20250221002702.png]]

The **_Address_** attribute of the **EMPLOYEE** entity can be subdivided into 
- Street_address = ‘2311 Kirby’,
- City = ‘Houston’,  
- State = ‘Texas’,
- Zip = ‘77001’

#### **2. Derived Attributes**
In some cases, two (or more) attribute values are related. One attribute can be derived (inferred) from another.

For Example: Age and Birth_Date attributes of a Person.
- For a particular person entity, the value of Age **can be determined** from the current (today’s) date and the value of that person’s Birth_date. 
- The **Age attribute** is hence called a **derived attribute** and is said to be **derivable** from the **Birth_date attribute**, which is called a **stored attribute**. 

Some attribute values can be **derived from related entities**

For Example: Attribute Number_of_employees of a DEPARTMENT entity.
- We can be derive Number_of_employees by counting the number of employees related to (working for) that department.

#### **3. Composite Attributes**
Composite attributes can be broken down into multiple components that are: 
1. Composite Attributes (sub-composite attribute)
	or 
2. Simple Attributes

The value of a composite attribute is the concatenation of its sub-attributes. 
This allows composite attributes to form a hierarchy.

For example: In Figure 7.4, _Street_Address_ can be further divided into 
- Number 
- Street 
- Apartment_Number 

![[Pasted image 20250221002943.png]]

Composite attributes are useful to model situations in which a user sometimes refers to the composite attribute as a unit but at other times refers specifically to its components.

If the composite attribute is referenced only as a whole, there is no need to subdivide it into component attributes

#### **4. Multivalued Attributes**
Most attributes have a **`single value`**. In some cases, an attribute can have a **`set of values`**.

Examples:
- Entity: Car
  Attribute: Colors
  Cars with one color have a single value, whereas two-tone cars have two color values.
   
- Entity: Student
  Attribute: Degrees
  One person may not have a college degree, another person may have one, and a third person may have two or more degrees

A multivalued attribute may have lower and upper **bounds** to constrain the number of values allowed for each individual entity. 

For example, the Colors attribute of a car may be restricted to have between 1-3 values, if we assume that a car can have three colors at most.


#### **5. Complex Attributes**
Complex attributes are a mix of **composite** and **multivalued** attributes **nested arbitrarily**. 

We can represent arbitrary nesting by grouping components of a composite attribute between parentheses () and separating the components with commas, and by displaying multivalued attributes between braces { }. 

Such attributes are called complex attributes. 

For example, if a person can have more than one residence (multi-valued) and each residence can have a single address and multiple phones (composite), an attribute Address_phone for a person can be specified as shown in Figure 7.5.4 

  ![[Pasted image 20250221003547.png]]

Both Phone and Address are themselves composite attributes. 

---
## **Entity Types & Sets**

A database usually contains groups of entities that are similar. 
We can define an Entity Type **`T`** from which we can create instances. These instances form an Entity Set **`S`** that are of type **`T`**.

For example, a company employing hundreds of employees may want to store similar information concerning each of the employees. 
These employee entities share the same attributes, but each entity has its own value(s) for each attribute.

#### **Entity Type**
An **entity type** defines a **type** for entities.
Entities with the same entity type that have the **same attributes**.
Each entity type in the database is described by its **name** and **attributes**. 

Different entities can be of the same type with name and type of attributes that define them but have their own unique values for each attribute.

This is similar to a class vs object scheme in object-oriented programming.
The entity type is the class, and each unique entity is the object. 
A class defines the framework for objects to follow, and each object can have unique value for each attribute inside the class.  

Figure 7.6 shows two entity types: EMPLOYEE and COMPANY.
Entities can be of an EMPLOYEE type but have its own unique values for each attribute.

![[Pasted image 20250221003747.png]]

#### **Entity Set**
The collection of all entities of a particular entity type in the database at any point in time is called an entity set.
The entity set is usually referred to using the same name as the entity type. 

For example, EMPLOYEE refers to both a type of entity as well as the current set of all employee entities in the database.

An entity type describes the schema or intension for a set of entities that share the same structure. The collection of entities of a particular entity type is grouped into an entity set, which is also called the extension of the entity type.

----
## **Key Attributes of an Entity Type**

#### **Key Constraint**

An important **constraint** on the entities of an entity type is the **key (uniqueness) constraint** on **attributes**. 
#### **Key Attribute**

An entity type usually has one or more **attributes** whose values are **distinct** **for each individual** **entity in the entity set**. 

Such an attribute is called a **key attribute**, and its values can be **used to identify each entity** **uniquely**. 

For example, the Name attribute is a key of the COMPANY entity type in Figure 7.6 because no two companies are allowed to have the same name. 
For the PERSON entity type, a typical key attribute is Ssn (Social Security number). 
#### **Composite Key Attribute**

Sometimes **several attributes** together **form a key**, meaning that the combination of the attribute values must be distinct for each entity. 
This is known as a **composite key attribute**.  

The proper way to represent this in the ER model that we describe here is to **define a composite attribute** and designate it as a key attribute of the entity type. 

Note that a composite key must be **minimal**; that is, all component attributes must be included in the composite attribute to have the **uniqueness property**.   

In ER diagrammatic notation, **each key attribute has its name underlined inside the oval,** as illustrated in Figure 7.7(a).

![[Pasted image 20250221004123.png]]  

Specifying that an attribute is a key of an entity type means that the preceding uniqueness property must hold for every entity set of the entity type. 

It is not the property of a particular entity set; rather, it is a constraint on any entity set of the entity type at any point in time.   

Hence, it is a constraint that **prohibits any two entities from having the same value for the key attribute at the same time**. 
#### **Multiple Keys**

Some entity types have more than one key attribute. 

For example, each of the Vehicle_id and Registration attributes of the entity type CAR (Figure 7.7) is a key in its own right. The Registration attribute is an example of a composite key formed from two simple component attributes, State and Number, neither of which is a key on its own. An entity type may also have no key, in which case it is called a weak entity type (see Section 7.5).

In our diagrammatic notation, if two attributes are underlined separately, then each is a key on its own. Unlike the relational model (see Section 3.2.2), there is no concept of primary key in the ER model that we present here; the primary key will be chosen during mapping to a relational schema (see Chapter 9).
#### **Attribute Constraints**

Each simple attribute of an entity type is associated with a set of constraints. These constraints specify the set of values that may be assigned to that attribute for each individual entity. 

- Type
- Range
- Format
- etc...