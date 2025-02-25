## What Are Requirements?
The **requirements** for a product or system are the **descriptions** of the **services** that a system should provide and the **constraints** on its operation.

Requirements reflect the **needs** of customers for a product or system. 
The process of finding out, analyzing, documenting, and checking these services and constraints is called **requirements engineering**.

Problems can arise during the requirements engineering process are a result of failing to make a clear separation between different levels of description. 
You can distinguish between them by using the terms **user requirements** and **system requirements**.

- **User requirements** are natural language statements of what services the system is expected to provide to system users and the constraints under which it must operate. 

- **System requirements** are more detailed descriptions of the software system’s functions, services, and operational constraints. 

## Software Requirement Specification
The system requirements document should define exactly what is to be implemented. 

Software specification or requirements engineering is the process of understanding and defining what services are required from the software system and identifying the constraints on the system’s operation and development. 

A **software requirements specification** (SRS) is **a description** of a software system to be developed. 

It lays out the following:
- functional requirements
- non-functional requirements
- constraints
- use cases
## Functional Requirements

The **functional requirements** for a system describe what the system **must** do. 

These requirements depend on:
1. The **type** of software being developed
2. The expected **users** of the software
- The general approach taken by the organization when writing requirements

When expressed as **user requirements**, functional requirements should be written in natural language so that system users and **managers** can understand them. 

Functional **system requirements** expand the user requirements and are written for **system developers**. They should describe the system functions, their inputs and outputs, and exceptions in detail.

For example, here are examples of functional requirements for the Mentcare system, used to maintain information about patients receiving treatment for mental health problems:

1. A user shall be able to search the appointments lists for all clinics.
2. The system shall generate each day, for each clinic, a list of patients who are expected to attend appointments that day.
3. Each staff member using the system shall be uniquely identified by his or her eight-digit employee number.

Ideally, the functional requirements specification of a system should have:

**Precision**
Ambiguous requirements may have different interpretations

**Completeness**
All services required by the user should be defined

**Consistency**
Requirements should not have contradictory definitions
## Non-Functional Requirements

Non-functional requirements are **constraints** on the services or functions offered by the system.

They may relate to emergent system properties such as reliability, response time, and memory use.
  
Non-functional requirements are often more critical than individual functional requirements. 
Unlike functional reqs, failing to meet a non-functional requirement can mean that the whole system is unusable. 

For example, if an aircraft system does not meet its reliability requirements, it will not be certified as safe for operation; if an embedded control system fails to meet its performance requirements, the control functions will not operate correctly.

Whenever possible, you should write non-functional requirements **quantitatively** so that they can be **objectively tested**.

![[20250123221457.png]]