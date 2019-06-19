# Database Review

#### Chapter-01 Introduction

#### 1. What is a Database

* A **collection of data**, typically describing the activities of one or more related organizations.

 #### 2. DBMS

* A **DBMS** is a **collection of software programs** to enable users to create, maintain and utilize a database.





### Chapter-02 ER Diagram

#### 1. ER Model (Entity-Relationship model)

* ER model views the real world as a collection of **entities** and **relationships** among entities.

#### 2. Entity

* An **object** in the real world that is distinguishable from other objects.
  * e.g. A classroom, A teacher, The address of the teacher
* Using a set of **attributes** whose values are used to distinguish one entity from another of same type.
* An **entity set** is a collection of entities of the same type
* All **entries** in a given entity set have the same attributes (the values may be different).
  * e.g. employee = (name, address, age, phone)
* The **ER model** can be presented graphically by an **ER diagram**.

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/er_diagram.JPG" style="zoom:0.4" />

#### 3. Attributes Types

1. **Simple attribute**

   * contains a single value

     <img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/simple_attribute.JPG" style="zoom:0.4" />

2. **Composite attribute**

   * contains several components

   <img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/composite_attribute.JPG" style="zoom:0.4" />

3. **Multi-valued attribute**

   * Contains more than one value

   <img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/multi_val_attribute.JPG" style="zoom:0.4" />

4. **Derived attribute**

   * Computed from other attributes
     * e.g., age can be computed from data of birth and the current date.

   <img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/derived_attribute.JPG" style="zoom:0.4" />

#### 4. Key attributes

1. **Key**
   * A set of attributes that can **uniquely** identity an entity.
2. **Composite Key**
   * Two or more attributes are used to serve as a key.
     * E.g., Name or Address alone cannot uniquely identify an employee, but together they can.

* A **minimal set of attributes** that uniquely identifies an entity is called a **candidate key**.
* If there are many candidate keys, we should choose one candidate key as the **primary key**.

#### 5. Relationship

* A relationship is an association among several entities.
* The **degree** refers to the number of entity sets that participate in a relationship set.
* Relationship sets that involve two entity sets are **binary**.
* Relationships among more than two entity sets are rare.

1. **Binary relationship**
   * A relationship can also have attributes which are used to describe the info about the relationship.
     * Employees work in departments (start date)
2. **Recursive Relationship**
   * Entity sets of a relationship need NOT be distinct.
   * Sometimes, a relationship might involve two entities in the same entity set.
     * e.g. employees related to employees
3. **Constraints**

* Mapping
  * 1-to-1
    * An entity in $A$ is related to **at most one** entity in $B$.
    * An entity in $B$ is related to **at most one** entity in $A$.
  * 1-to-many
    * An entity in $B$ can be associated with **at most one** entity in $A.$
  * many-to-1
    * similar to 1-to many.
  * many-to-many
    * An entity in $A$ is related to **any number** of entities in $B.$
    * An entity in $B$ is related to **any number** of entities in $A.$
    * **No restriction** in the mapping.

4. **Participation Constraint**
   * **Total**
     * Each entity in the entity set **must be associated in at least one** relationship.
       * e.g. Every loan must be borrowed by a customer.
   * **Partial**
     * Each entity in the entity set **may (or may not) be associated** in a relationship.
       * e.g. Some customers may (or may not) borrow loans.

#### 6. Strong Entity/Weak Entity

* **Strong Entity**
  * An entity can **be uniquely identified** by some attributes related to this entity.
    * e.g. Employee has an attribute $EmpID$.
* **Weak Entity**
  * An entity **CANNOT be uniquely identified** by all attributes related to this entity.
  * Definition: 
    * If a weak entity set $W$ is dependent on a strong entity set $E$, we say that $E$ **owns** $W$.
      * e.g. Employee owns Dependent

#### 7. Class Hierarchy

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/class_hierachy.JPG" style="zoom:0.5" />

* Attributes are **inherited** by the entity set in the subclass.
  * e.g. the attributes defined for an $Hourly\_Emps$ entity are the attributes for Employees plus that of $Hourly\_Emps$
* A class hierarchy can be viewed in one of the two ways.
  * A class is **specialized** into subclasses.
  * The subclasses are **generalized** by a superclass.
* **Constraints**
  * Overlap constraints (Can an employee be an $Hourly\_Emps$ as well as a $Contract\_emps$ entity?)
  * Covering constraints (Does every Employees entity also have to be an $Hourly\_Emps$ or a $Contract\_emps$)
* Why we use class hierarchy?
  * Add descriptive attribute that make sense only for the entities in a subclass.
  * Identify the set of entities that participate in some relationships.

#### 8. Non-binary Relationship

* Ternary Relationship



