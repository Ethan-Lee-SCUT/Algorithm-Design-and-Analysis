# Database Review

#### Chapter-01 Introduction

#### 1. What is a Database

* A **collection of data**, typically describing the activities of one or more related organizations

 #### 2. DBMS

* A **DBMS** is a **collection of software programs** to enable users to create, maintain and utilize a database.





### Chapter-02 ER Diagram

#### 1. ER Model (Entity-Relationship model)

* ER model views the real world as a collection of **entities** and **relationships** among entities.

#### 2. Entity

* An **object** in the real world that is distinguishable from other objects
  * e.g. A classroom, A teacher, The address of the teacher
* Using a set of **attributes** whose values are used to distinguish one entity from another of same type
* An **entity set** is a collection of entities of the same type
* All **entries** in a given entity set have the same attributes (the values may be different).
  * e.g. employee = (name, address, age, phone)
* The **ER model** can be presented graphically by an **ER diagram**

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
     * e.g., age can be computed from data of birth and the
       current date

   <img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/derived_attribute.JPG" style="zoom:0.4" />







