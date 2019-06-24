# *Database Review

题型：选择+大题

不会直接考定义，会考用自己的话描述（理解）

着重实践，例如ER diagram与逻辑间的转换 依赖关系的推导等





## Chapter-01 Introduction

### 1.1. What is a Database

* A **collection of data**, typically describing the activities of one or more related organizations.

 ### 1.2. DBMS

* A **DBMS** is a **collection of software programs** to enable users to create, maintain and utilize a database.





## Chapter-02 ER Diagram

### 2.1. ER Model (Entity-Relationship model)

* ER model views the real world as a collection of **entities** and **relationships** among entities.

### 2.2. Entity

* An **object** in the real world that is distinguishable from other objects.
  * e.g. A classroom, A teacher, The address of the teacher
* Using a set of **attributes** whose values are used to distinguish one entity from another of same type.
* An **entity set** is a collection of entities of the same type
* All **entries** in a given entity set have the same attributes (the values may be different).
  * e.g. employee = (name, address, age, phone)
* The **ER model** can be presented gra04phically by an **ER diagram**.

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/er_diagram.JPG" style="zoom:0.4" />

### 2.3. Attributes Types

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

### 2.4. Key attributes

1. **Key**
   * A set of attributes that can **uniquely** identity an entity.
2. **Composite Key**
   * Two or more attributes are used to serve as a key.
     * E.g., Name or Address alone cannot uniquely identify an employee, but together they can.

* A **minimal set of attributes** that uniquely identifies an entity is called a **candidate key**.
* If there are many candidate keys, we should choose one candidate key as the **primary key**.

### 2.5. Relationship

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

### 2.6. Strong Entity/Weak Entity

* **Strong Entity**
  * An entity can **be uniquely identified** by some attributes related to this entity.
    * e.g. Employee has an attribute $EmpID$.
* **Weak Entity**
  * An entity **CANNOT be uniquely identified** by all attributes related to this entity.
  * Definition: 
    * If a weak entity set $W$ is dependent on a strong entity set $E$, we say that $E$ **owns** $W$.
      * e.g. Employee owns Dependent

### 2.7. Class Hierarchy

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

### 2.8. Non-binary Relationship

* Ternary Relationship

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/ternary_relationship.JPG" style="zoom:0.5" />





## Chapter-04 Relational Model

### 4.1. Terminology

* **Relation $\leftrightarrow$ Table**
  * denoted by $R(A_1,A_2,...,A_n)$ where $R$ is **relation name** and $(A_1,A_2,...,A_n)$ is the relation schema of $R$
* **Attribute $\leftrightarrow$ Column (Collectively a schema)**
  * denoted by $A_i$ 
* **Tuple $\leftrightarrow$ Row**
* **Attribute value $\leftrightarrow$ value stored in a table cell**
* **Domain $\leftrightarrow$ legal type and range of values of an attribute.**
  * denoted by $dom(A_i)$

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/terminology.JPG" style="zoom:0.4" />

### 4.2. Foreign Key

* A set of attributes in one relation $R$ that is used to refer to a tuple in another relation $S$. (it must correspond to the primary key of the second relation)
  * Student
    * (<u>Student-id</u>, Student_Name)
  * Take
    * (<u>Student-id</u>, Course_id, semester_No)
  * Student-id in relation Student is a **primary key**
  * Student-id in relation Take is a **foreign key**

### 4.3. ER-to-Relational Mapping (???)

1. **Strong Entity Set**

   * For each **strong entity set** $E$ in the ER schema,
     * create a relation schema $R$ that includes all the attributes of $E$.
     * choose one set of key attributes of $E$ as a primary key for $R$

2. **Weak Entity Set**

   * For each weak entity set $W$ in the ER model,
     * create a relation schema $R$, and include all attributes.
     * In addition, include the primary $key(s)$ of the $owner(s)$.
     * The primary key of $R$ is the combination of the primary $key(s)$ of the $owner(s)$ and the discriminator of the weak entity set $W$.

3. **1-to-1 Relationship**

   * For each binary one-to-one (1:1) relationship set $R$

     $T----S$

     * Choose one of the 2 relation schemas, say $S$,
       * get primary key of $T$,
       * include it as foreign keys in $S$.
     * Better if S has total participation in $R$
     * Include the attributes of the relationship set $R$ as attributes of $S$

4. **1-to-many Relationship**

   * For each binary one-to-many relationship set

     $T----S$

     * Include as foreign key in $S$ the primary key that represents the other entity set $T$ participating in $R$.
     * Include any attributes of the one-to-many relationship set as attributes of $S$.

5. **Many-to-many Relationship**

   * For each binary many-to-many relationship set $R$
     * create a new relation schema $S$ to represent $R$
     * Include as foreign key attributes in $S$ the primary keys of the relation schemas for the  participating entity sets in $R$
     * their combination will form the primary key of $S$
     * Also include attributes of the many-to-many relationship set as attributes of $S$.

6. **Non-binary Relationship**

   * For each non-binary relationship set,
     * create a new relation schema $S$ to represent $R$.
     * Include as foreign key attributes in $S$ the primary keys of the participating entity sets.
     * Also include any attributes of the nonbinary relationship set as attributes of $S$.





## Chapter-05 Relational Algebra

* **Basic operations**
  * Projection
  * Selection
  * Set-difference
  * Union
  * Cross-product
  * Rename
* **Additional operations**
  * Intersection, join, division: Not essential, but (very!) useful.
* Each operation returns a relation, and **operations can be composed!**

### 5.1. Projection $\pi_L(R)$

* Deletes attributes that are not in projection list $L$.
* Schema of result contains exactly the fields in the projection list, with the same names that they had in the (only) input relation.
* Projection operator **eliminates duplicates!**

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/projection.JPG" style="zoom:0.7" />

### 5.2. Selection $\sigma_c(R)$

* Selects rows (records/tuples) that satisfy a selection **condition** $c$.

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/selection.JPG" style="zoom:0.7" />

### 5.3. Set Operations

* **Union, Intersection, Set-Difference**
* These three operations take two input relations, which must be **union-compatible**.
  * Same number of fields
  * Corresponding fields have the same type
* Output is a single relation (that does not contain duplicates).

1. **Union** $Plane_1\cup Plane_2$

   <img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/union.JPG" style="zoom:0.6" />

2. **Set Difference** $Plane_1- Plane_2$

   * $R_1-R_2=\sigma_{}$

   <img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/set_difference.JPG" style="zoom:0.6" />

3. **Intersection** $Plane_1\cap Plane_2$

   <img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/intersection.JPG" style="zoom:0.6" />

4. **Cartesian Product** $R_1\times R_2$
   
* Combines each row of one table with every row of another table
  
5. **Join** $R_1\triangleright \triangleleft  R_2=\sigma_{c}(R_1\times R_2) $
* Join is a **cartesian product** followed by **a selection**
   * **Natrual join???**
   * **$\theta-$join???**

### 5.4.Renaming $\rho$

   * If attributes or relations have the same name, it may be convenient to rename one

$$
   \rho(R'(N_1\rightarrow N'_1,...,N_n\rightarrow N'_n),R)
$$

   * The new relation $R’$ has the same instance as $R$, but its schema has attribute $N’_i$ instead of attribute $N_i$

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/renaming.JPG" style="zoom:0.5" />

### 5.5. Division $A/B$

* Let $A$ have two attributes $x$ and $y$ 
* Let $B$ have one attribute $y$
* $A/B$ contains all $x$ tuples, such that for every $y$ tuple in $B$ there is a $xy$ tuple in $A$

1. Find all student IDs (sids) of the students who took **all​** courses in table Course.

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/division1.JPG" style="zoom:0.4" />
$$
Answer=Take/Course
$$

2. Find all student IDs (sids) of the students who took **all** courses provided by CSE.

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/division2.JPG" style="zoom:0.4" />
$$
Answer=Take/\pi_{cid}(\sigma_{dept="CSE"}(Course))
$$

### 5.6. Additional Operators - Outer Join

* An extension of the join operation that avoids loss of information.
* Computes the join and then adds **tuples** from one relation that do not match **tuples** in the other relation to the result of the join.

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/outer_join.JPG" style="zoom:0.5" />

* **Left outer join $=\triangleright \triangleleft$**

  * Keep the entire left relation (Loan) and fill in information from the right relation, use null if information is missing

  <img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/outer_join_left.JPG" style="zoom:0.5" />

* **Right outer join $\triangleright \triangleleft =$**

  * Keep the entire right relation (borrower) and fill in information from the left relation, use null if information is missing

  <img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/outer_join_right.JPG" style="zoom:0.5" />

* **Full outer join $=\triangleright \triangleleft =$**

  * Keep the entire left relation (loan) and the entire right relation (borrower), and use null if information is missing

  <img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/outer_join_full.JPG" style="zoom:0.5" />





## Chapter-06 SQL

### 6.1. Domain Types in SQL
* char($n$) 
  * Fixed length character string, with user-specified length $n$.
* varchar($n$) 
  * Variable length character string, with user-specified maximum length $n$.
* int
* smallint
* Numeric($p,d$)
  * $p$ digits, $d$ digits to the right of decimal point
* real, double precision
* float($n$)
* date
* time

### 6.2. Data Definition Language (DDL) (Fundamental concepts)

* **Create Table**

  * e.g. Custermer(<u>customer-name</u>, customer street)

  ```sql
  create table customer
  	(	customer-name	   char(20)	not null,
  		customer-street	   char(30),
  		customer-city	   char(30),
  		primary key (customer-name)	)
  ```

* **Drop Table**

  ```sql
  drop table custermer
  ```

* **Alter Table**

  ```sql
  alter table customer add phone char(10) 
  alter table customer drop phone 
  ```

* **Integrity Constraints (ICs)**
  
  * nut null

### 6.3. Data Manipulation Language (DML)

1. **The basic form of SQL**

   ```sql
   SELECT       [DISTINCT]  target-list		# projections
   FROM         relation-list					# cross-product
   WHERE        qualification (condition)		# selection
   ```

   $$
   \pi_{a_1,a_2,...,a_n}(\sigma_P(R_1\times R_2\times...\times R_m))
   $$

2. **Arithmetic Operation**

   * Select clause:  $+$,$-$,$/$ and $\times$ operating on constants or attributes of tuples.

   ```sql
   select branch-name, loan-number, amount * 100 from loan
   ```

   * Where clause: Logical expression (and, or, not)

   ```sql
   select loan-number from loan where branch-name=“Perryridge” and amount >1200
   ```

   * Where clause: Between

   ```sql
   select loan-number from loan where amount between 90000 and 100000
   ```

   * From clause: Join
     * Cartisian product with wherec clause

3. **Rename Operation**

   * 'as' is usually omitted

   * Select clause: 

   ```sql
   select distinct customer-name, borrower.loan-number as loan-id from borrower, loan
   ```

   * From clause:

   ```sql
   select distinct customer-name, T.loan-number from borrower as T, loan as S
   ```

4. **String Operation**

   * $\%$ matches any substring
   * $\_$ matches any single character
   * Find the name of all customers  whose street includes the substring ‘Main’. (E.g., Mainroad, Small Main Road, AMainroad,…)

   ```sql
   select customer-name from customer where customer-street like “%Main%”
   ```

5. **Ordering the Display of Tuples**

   * 'asc' for ascending order
   * 'desc' for descending order
   * List the names of all customers in the ascending order of customer-city and then descending order of customer-name

   ```sql
   select distinct customer-name from customer order by customer-city asc, customer-name desc
   ```

6. **Aggregate Operator**
   * COUNT ([DISTINCT] A)
   * SUM ([DISTINCT] A)
   * AVG ([DISTINCT A)
   * MAX (A)
   * MIN (A)

7. **Set Operation**

   * **Union $\cap$**
   * **Intersection $\cup$**
   * **Except $-$**
   * Each of the above operations **automatically eliminates duplicates**; To retain all duplicates, we can use **union all, intersect all and except all**.
   * Find all customers who have a loan, an account, or both:

   ```sql
   (select customer-name from depositor)
   union  
   (select customer-name from borrower)
   ```

   * Find all customers who have both a loan and an account

   ```sql
   (select customer-name from depositor)
   intersect
   (select customer-name from borrower)
   ```

   * Find all customers who have an account but no loan.

   ```sql
   (select customer-name from depositor)
   except
   (select customer-name from borrower)
   ```

   * **Nested Subquery**
     * **in** 
     * **not in**
     * **some**
     * **all**
     * **exist** (Test for empty relations)

8. **Division ???**

9. **Group By**

   * Find the number of accounts for each branch. 

   ```sql
   select branch-name, count(account-number) from account group by branch-name
   ```

   * **Having** clause
     * predicates in the **having** clause are applied to each group after the formation of groups.

10. **NULL value**

    * Logic with unknown values

    <img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/null_logic.JPG" style="zoom:0.5" />

11. **Sequence ???**

    * A sequence is a database object that generates numbers in sequential order. 

### 6.4. Data Definition Language (DDL) (Advanced concepts)

1. Domain constraints

   ```sql
   create domain hourly-wage numeric(5,2) constraint wage-value-test check (value > 4.00)
   ```

2. Possibly many **candidate keys**  (specified using **UNIQUE**), one of which is chosen as the **primary key**.

   ```sql
   CREATE TABLE Enrolled
      (sid CHAR(20)
        cid  CHAR(20),
        grade CHAR(2),
        PRIMARY KEY  (sid),
        UNIQUE (cid, grade) )
   ```

3. Foreign key

   * use **cascade delete** or **cascade update** to  maintain data

   ```sql
   create table depositor
       (customer-name		char(15),
   	account-number		char(10)    not null,
   	primary key (customer-name, account-number),
   	foreign key (customer-name) references customer	on delete cascade,
   	foreign key (account-number) references account	on delete cascade)
   
   ```

4. Record deletion

   ```sql
   delete from account where branch-name = “Perryridge”
   ```

5. Record insertion

   ```sql
   insert into account account (branch-name, balance, account-number) 	values (“Perryridge”, 1200, “A-9732”)
   ```

6. Record update

   ```sql
   update account set balance = 2000 where account-number = “A-123”
   ```

7. Views (likes a relation)

   * Provide a mechanism to hide certain data from the view of certain users.

   ```sql
   create view view-name as <query expression>
   ```

   ```sql
   Drop view view-name
   ```

8. Assertion ???

   * An assertion is a complex constraint that the database must always satisfy.

   ```sql
   create assertion <assertion-name> check <predicate>
   ```

   * When an assertion is made, the system tests it for validity.

9. Trigger ???

   * A trigger is a statement that is executed automatically by the system as a side effect of a modification to the database.

   ```sql
   create trigger <trigger-name> …
   ```





## Chapter-08 Functional Dependency, Schema Refinement & Normal Forms
### 8.1. Problems caused by redundancy

* Waste of resources of storage
* Potential inconsistency

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/redundancy.JPG" style="zoom:0.35" />

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/inconsistency.JPG" style="zoom:0.35" />

* Solution:
  * Decomposition

### 8.2. Functional dependencies

* Functional dependency is a type of constraint that is **a generalization of the notation of key**.

* **Definition**

  * $R$ -- a relation schema, $\alpha\subset R, \beta\subset R$

  * $\alpha\rightarrow\beta$ if and only if

    * For any relation $r$ on $R$
    * For any two tuples $t_1,t_2$ of $r$
        * $\Pi_\alpha(t_1)=\Pi_\alpha(t_2)\Rightarrow\Pi_\beta(t_1)=\Pi_\beta(t_2)$

* **Trivial Functional Dependency ???**

  * $\alpha\rightarrow\beta$ where $\beta\subseteq\alpha$
    * e.g. $AB\rightarrow A$

* **Non-Trivial Functional Dependency ???**

  * ?
    * e.g. $AB\rightarrow C$

* **Information deduced from functional dependencies**

  * $\alpha$ is a **key** for $R$

    $\Leftrightarrow\alpha\rightarrow R$

  * $\alpha$ is a **candidate key** for $R$

    $\Leftrightarrow\alpha\rightarrow R$, and there is no $\gamma$ s.t. $\gamma\subset\alpha$, $\gamma\rightarrow R$

    * e.g. $AC\rightarrow R$, $AD\rightarrow R$, $ACD\rightarrow R$
    * $AC$, $AD$ are candidate keys
    * $ACD$ is not a candidate key

* **Reasoning about FDs**

  * $F$: a set of functional dependencies
  * $f$: an individual functional dependency
  * $f$ is implied by $F$ if
    * whenever all functional dependencies in $F$ are true
      * then $f$ is true
  * e.g. $F = {A \rightarrow B, B\rightarrow C}$ implies $A\rightarrow C$

* **Closure of $F$**

  * $F^+$ – closure of $F$: the set of all functional dependencies that $F$ implies
    * e.g. $F={A\rightarrow B}$
      * $F^+={A\rightarrow A, B\rightarrow B, A\rightarrow B, A\rightarrow AB, AB\rightarrow A,AB\rightarrow B,AB\rightarrow AB}$

  * **Armstrong’s axioms**
    * If $\beta\subseteq\alpha$ then $\alpha\rightarrow\beta$ (reflexivity)
      * e.g. $\{A,C\}\subseteq\{A,B,C\}\Rightarrow ABC\rightarrow AC$
    * If $\alpha\rightarrow\beta$ then $\gamma\alpha\rightarrow\gamma\beta$ (augmentation)
      * $A\rightarrow\beta\Rightarrow CA\rightarrow CB$
    * If $\alpha\rightarrow\beta,\beta\rightarrow\gamma$ then $\alpha\rightarrow\gamma$ (transitivity)
      * $A\rightarrow BD$, $BD\rightarrow C\Rightarrow A\rightarrow C$
    * Additional rules (inferred from Armstrongs axioms) 
      * $A\rightarrow B$ and $A\rightarrow C\Rightarrow A\rightarrow BC$ ???
      * $A\rightarrow BC\Rightarrow A\rightarrow B$ and $A\rightarrow C$
      * $A\rightarrow B$ and $BC\rightarrow D\Rightarrow AC\rightarrow D$
  * **Algorithm to compute $\alpha^+$**

  <img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/alg_closure1.JPG" style="zoom:0.35" />

  <img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/alg_closure2.JPG" style="zoom:0.35" />

### 8.3. Boyce Codd normal form (BCNF)

* $R$ – a relation schema
* $F$ – a set of functional dependencies on $R$
* $R$ is in **BCNF** if for **any** $\alpha\rightarrow A$ in $F$
  * $\alpha\rightarrow A$ is trivial ($A\in\alpha$), or
  * $\alpha $ is a key for $R$
* e.g.

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/bcnf.JPG" style="zoom:0.4" />

### 8.4. Third normal form (3NF)

* $R$ – a relation schema
* $F$ – a set of functional dependencies on $R$
* $A$ – a single attribute in $R$
* $R$ is in **3NF** if for **any** $\alpha\rightarrow A$ in $F$
  * $\alpha\rightarrow A$ is trivial ($A\in\alpha$), or
  * $\alpha $ is a key for $R$, or
  * $A$ is part of some key(s) for $R$
    * e.g. $AB$ is a key for $R$
    * $A$ is a part of the key, $B$ is also a part of the key.
* $R$ is in BCNF $\Rightarrow$ $R$ is in 3NF
* e.g. 

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/3nf.JPG" style="zoom:0.4" />

### 8.5. Decomposition

* **Definition**
  * $\{R_1,...,R_n\}$ – a set of relation schemas
  * $\{R_1,...,R_n\}$ is a **decomposition** of $R$ if $R_1\cup R_2\cup...\cup R_n=R$
  * $\{R_1,...,R_n\}$ is a **lossless-join decomposition** of $R$ if for all relations $r$ on schema $R$, $\Pi_{R_1}(r)\times...\times\Pi_{R_n}(r)=r$
* **Imply**
  * $R$ – a relation schema
  * $F$ – a set of functional dependencies on $R$
    * ${R_1,F_2}$ is a lossless-join decomposition of $R$
    * $\Leftrightarrow(R_1\cap R_2)\rightarrow R_1\in F^+$ or $(R_1\cap R_2)\rightarrow R_2\in F^+$
    * $\Leftrightarrow(R_1\cap R_2)$ is a key for $R_1$ or $R_2$
* Example (non-lossless)

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/decom1.JPG" style="zoom:0.35" />

* Example (lossless)

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/decom2.JPG" style="zoom:0.35" />

### 8.6. Dependency preservation

* $R$ – a relation schema
* $F$ – a set of functional dependencies on $R$
* $\{R_1,R_2\}$ is a decomposition of $R$
* $F_i$ – a subset of $F$ with only attributes in $R_i$
* **Dependency is preserved** if $(F_1\cup F_2)^+=F^+$
* e.g.

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/dependency_preservation.JPG" style="zoom:0.35" />

### 8.7. BCNF decomposition algorithm ???

* Suppose $R$ is not in BCNF, $A$ is an attribute, and $X\rightarrow A$ is a FD that violates the BCNF
  condition.
  1. Remove $A$ from $R$
  2. Decompose $R$ into $XA$ and $R-A$
  3. Repeat this process until all the relations become BCNF

* BCNF decomposition guarantees that the decomposition is a lossless-join
* It does not guarantees that the decomposition is dependency preserving

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/bcnf_decom.JPG" style="zoom:0.35" />

### 8.8. 3NF decomposition algorithm ??????

* **Canonical Cover $F_c$**
  * **repeat**
    * Replace any $\alpha_1\rightarrow\beta_1$ and $\alpha_1\rightarrow\beta_2$ by $\alpha_1\rightarrow\beta_1\beta_2$
    * Delete any **extraneous attribute** from any $\alpha\rightarrow\beta$
    * **until** $F$ does not change
* **Algorithm**
  * Find a canonical cover $F_c$ for $F$
  * result = { }
  * for each $\alpha\rightarrow \beta$ in $F_c$ do
    * if no schema in result contains $\alpha\beta$ then
      * add schema $\alpha \beta$ to result
  * end for
  * if no schema in result contains a candidate key for $R$
    * choose any candidate key $\alpha $ for R
    * add schema $\alpha $ to result
  * end if
* 3NF decomposition guarantees that the decomposition is a lossless-join
* It guarantees that the decomposition is dependency preserving

### 8.9. Design goal

* Goal for a relational database design
  * BCNF
  * Lossless-join
  * Dependency Preservation
* If we cannot achieve this, we accept
  * 3NF
  * Lossless-join
  * Dependency Preservation





## Chapter-09 File and Index Structure

### 9.1. Disks and Files

* Why Not Store Everything in Main Memory?
  * **Costs too much**. RAM is much more expensive than disk.
  * **Main memory is volatile**. We want data to be saved between runs.

### 9.2. Indexes and Databases

* Indexing mechanisms speed up access to desired data.
* **Search key** - attributes used to look up records in a file.
* An **index file** consists of records (called **index entries**) of the format:

$$
Search\_Key---Pointer
$$

* Index files are typically much smaller than the original file
* Two basic kinds of indices:
  * **Ordered indices**: search keys are stored in sorted order
  * **Hash indices**: search keys are distributed uniformly across “buckets” using a “hash function”.

* **How are indexing techniques evaluated?**
  * What access operation can be supported?
  * Time (access, insertion, deletion)
  * Space overhead

#### 9.2.1 Ordered indices

* **Primary index (clustering index)**: in a sequentially ordered file, the index whose search key specifies the sequential order of the file.
* **Secondary index (non-clustering index.)**: an index whose search key specifies an order different from the sequential order of the file. 
* **Dense index**
  * **Every search-key value** in the data file is indexed.
* **Sparse index**
  * Not all of the search-key values are indexed.
    * Adv: reduce index size
    * Disadv: slower
  * To locate a record with search-key value $K$ we
    * find index record with largest search-key value $≤ K$
    * search file sequentially starting at the record to which index record points
* **Multilevel index**
  * **Outer index**: A sparse index of primary index
  * **Inner index**: The primary index file
* **Index update (Deletion)**
  * Dense index
    * similar to file record deletion
  * Sparse index
    * If an entry for the search key exists in the index, it is deleted by replacing the entry in the index with the next search-key value in the file (in search-key order). If the next search-key value already has an index entry, the entry is deleted instead of being replaced.
* **Index update (Insertion)**
  * **Perform a lookup** using the search-key value appearing in the record to be inserted.
  * **Dense indices** - if the search-key value does not appear in the index, insert it.
  * **Sparse indices** - if index stores an entry for each block of the file, no change needs to be made to the index unless a new block is created. In this case, the first search-key value appearing in the new block is inserted into the index.
* **Primary and secondary indices**
  * Secondary indices have to be dense because records are not sorted by the secondary index values.

### 9.3. Hash Files

* A hash method includes a **hash function** and a **collision handling mechanism**

#### 9.3.1. Static hashing (bucket hashing)

* A hash file consists of M buckets of the **same size**

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/static_hashing.JPG" style="zoom:0.5" />

* Hash indices
  * Hash indices are **always secondary indices**.

#### 9.3.2.  Dynamic hashing ???

* **Extendable hashing**

  * At any time, use **only a prefix** of the $b$ -bit integers to index into a table of bucket addresses. Let the length of the prefix be $i$ bits, $0 < i < 32$

  * Initially i = 1, meaning that it can index **at most 2 buckets**

  * When the 2 buckets are full, we can use 2 bits ($i = 2$), meaning that we can now index at most 4 buckets, and so on and so forth.

  * $i$ grows and shrinks as the size of the database grows and shrinks.

  * Actual number of buckets is $< 2^i$, which may change due to bucket merging and splitting.

    <img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/extendable_hashing.JPG" style="zoom:0.65" />

## Chapter-10 B+ Tree

* It is **balanced**: all leaf nodes are at the same level
* Each node has a special structure

* Minimum height $H$ of B+ tree
  * $H\ge \log_F(\frac{D}{F-1})$
  * $F$ is the number of pointers, $D$ is the number of data entries.

### 10.1. Manipulation

* Query
* Insert
* Delete





## Chapter-11 External Sort

* **Two-way external merge sort** 
  * Requires 3 buffers

#### 11.1. General External Merge Sort

* To sort a file with $N$ pages using $B$ buffer pages:
  * Pass 0: use $B$ buffer pages
    * Produce $\lceil N/B\rceil$sorted runs of $B$ pages each.
  * Pass 2, …, etc.: merge $B-1$ runs

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/external_sort.JPG" style="zoom:0.4" />

* **Number of passes**: $1+\lceil\log_{B-1}\lceil N/B\rceil\rceil$
*  **Cost**: $2N\times(\# passes)$





## Chapter-12 Join Algorithm

e.g. 

* **Student: 500 pages, 80 tuples/page, 50 bytes/tuple**

* **Take: 1000 pages, 100 tuples/page, 40 bytes/tuple**

* **200 courses in table Take**

* **1, 2, …, 40 in attribute Age of table Student**

### 12.1. Simple-Nested Loop Join

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/simple_nested_loop_join.JPG" style="zoom:0.5" />

```pseudocode
For each page p of T (T is called outer relation )
	for each page q of S (S is called inner relation )
		for each tuple t ∈ p and each tuple s ∈ q
			such that t.sid = s.sid
			output <t, s> to the output
```

* We need **3 pages for buffer**
  * 1 page for $p$ (from $T$)
  * page for $q$ (from $S$)
  * 1 page for the output
* Cost of Reading $T$ = $1000$ pages
  * The total number of times that $S$ is read = $1000$
* Cost of Reading $S$ (with multiple times) = $1000\times 500 = 500000$ pages
* Total Cost = $1000 + 500000 = 501000$ pages

### 12.2. Block-Nested Loop Join

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/block_nested_loop_join.JPG" style="zoom:0.5" />

```pseudocode
For each page p of T (T is called outer relation )
	for each page q of S (S is called inner relation )
		for each tuple t ∈ p and each tuple s ∈ q
			such that t.sid = s.sid
			output <t, s> to the output
```

* We have $B$ pages in memory (or $B$ buffer pages)
  * $B=6$

* $B-2$ pages for $p$ (from $T$)
* 1 page for $q$ (from $S$)
* 1 page for the output
* Cost of Reading $T$ = 1000 pages
* The total number of times that $S$ is read = $\lceil1000/(6-2)\rceil=250$
* Cost of Reading $S$ (with multiple times) = $250*500 = 125000$ pages
* Total Cost = $1000 + 125000 = 126000$ pages

### 12.3. Sort-Merge Join

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/sort_merge_join.JPG" style="zoom:0.5" />

```pseudocode
1. Sort table T according to sid
2. Sort table S according to sid
3. Merge table T and table S
```

* Cost of Sorting T =$2\times1000\times(1+\lceil\log_{6-1}\lceil1000/6\rceil\rceil)=10000$
* Cost of Sorting S =$2\times500\times(1+\lceil\log_{6-1}\lceil1000/6\rceil\rceil)=4000$
* Cost of Merging = Cost of Reading $T$ + Cost of Reading $S$ = $1000+500=1500$
* Total Cost = $10000 + 4000 + 1500 = 15500$ pages

### 12.4. Index-Nested Loop Join ???

* Assume that there is an index built on attribute sid for table Student

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/index_nested_join.JPG" style="zoom:0.5" />

```pseudocode
For each tuple t of T
	ID = t.sid
	use the index to obtain a tuple s (or tuples) in S
		with s.sid = ID
	for each such s in S
		output <t, s> to the output
```

* We have $B$ pages in memory (or $B$ buffer pages)
  * $B=6$
* Cost of Reading $T = 1000$ pages
  * The total number of tuples in $T =1000*100=100000$
* Cost of Reading $S$ (with multiple times) $=100000*(1.2 + 1) = 220000$ pages
  * $1.2$ for hashing (given)
  * $1$ for $\lceil(500*80/(100,000))\rceil$
* Total Cost $= 1000 + 220000 = 221000$ pages

### 12.2. Hash Join

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/hash_join.JPG" style="zoom:0.4" />

```pseudocode
1. Hash all tuples in T based on sid
2. Hash all tuples in S based on sid
3. For each hash slot,
	1. Join all tuples t from T and all tuples s from S where
		t.sid = s.sid
	2. Output all these tuples
```





## Chapter-13 Query Optimization

* DBMS’s job is to optimize the users’ query by
  * Converting the query to a number of evaluation plans
  * Estimate the cost of each evaluation plan
  * Find the evaluation plan with the lowest
    cost

### 13.1. Materialization and On-the-fly

* Let $op1$ and $op2$ be two relational algebra operations, and $op1$ is performed on the result of $op2$
* The evaluation of $op1$ is **on-the-fly** if **the result of op2 is directly sent to $op1$** (i.e, not stored in a temporary file)
* It is **materialized** if that **result is stored in a temporary file first**
* **On-the-fly evaluation** is called **pipelined evaluation**
* On-the-fly can be more efficient than materialized

#### 13.1.1. Materialization

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/materialization.JPG" style="zoom:0.4" />

#### 13.1.2. On-the-fly

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/on_the_fly1.JPG" style="zoom:0.4" />

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/on_the_fly2.JPG" style="zoom:0.4" />



### 13.2. Join over Two Tables ???

**Example schema**

* Assuming the following table sizes:
  * Student: 500 pages, 80 tuples/page, 50 bytes/tuple
  * Take: 1000 pages, 100 tuples/page, 40 bytes/tuple
* Assume that there are 200 courses in table Take

此处省略很多字，根据Evaluation plan，一个一个步骤去分析cost

### 13.3. Join over Multiple Tables

#### 13.3.1. Relational algebra equivalences

* **Selection**

$$
\sigma_{c1}(\sigma_{c2}(R))\equiv\sigma_{c2}(\sigma_{c1}(R)) \\
\sigma_{c1\and ...\and cn}(R)\equiv\sigma_{c1}(...\sigma_{cn}(R))
$$

* **Join**

$$
R\triangleright\triangleleft(S\triangleright\triangleleft T)\equiv (R\triangleright\triangleleft S)\triangleright\triangleleft T\\
(R\triangleright\triangleleft S))\equiv(S\triangleright\triangleleft R))
$$



* For multi-relation query, **plan space** can be very large and must be pruned.
  * As # of joins increases, # of alternative plans grows rapidly.
* Typically, **only left-deep trees** (the right child of each join node is a base table) are considered.
  * Significantly fewer, but still lots
    * $n!$
* Left-deep trees allow us to generate **fully pipelined** plans.
  * Intermediate results not written to temporary files.
  * Not all plans from left-deep trees are fully pipelined (e.g., sort-merge join).

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/left_deep_plan.JPG" style="zoom:0.45" />





## Chapter-14 Concurrency Control
### 14.1. Transaction

* Sequence of operations
* E.g. T1: Read(A), A=A+100, Write(A) 
  * R(A), W(A)
  * Can be denoted by R1(A), W1(A)
* E.g. T2 : W(B), R(A)

### 14.2. ACID Property

1. Atomicity
2. Consistency
3. Isolation
4. Durability

### 14.3. Schedules

* A sequence of operations in a set of transactions $\{T_1,T_2,...,T_n\}$
* e.g. If a set of transactions is $\{T_1, T_2\}$

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/schedules.JPG" style="zoom:0.5" />

### 14.4 Serial schedules

* **Serial schedule**
  * A schedule which the operations belonging to one single transaction **appear together**.
    * $H_1$ is serial schedule ($T_1T_2$).
    * $H_2,H_3$ are not serial schedule.
* **Serializable schedules**
  * Equivalent to some serial schedule.
    * $H_1$ and $H_2$ are serializable schedules (to $T_1T_2$).
    * $H_3$ is a serializable schedule (to $T_2T_1$).

### 14.5 Conflict Serializability

* Two operations are **conflict** if
  * They are **operations of different transactions** on the **same data object**.
  * At least one of them is a **write** operation.

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/conflict.JPG" style="zoom:0.5" />

* Two operations are **non-conflict**

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/non_conflict.JPG" style="zoom:0.5" />

* Two schedules $S_1$ and $S_2$ are **conflict equivalent** if
  * $S_1$ and $S_2$ involve the same operations of the same transaction.
  * Every pair of conflicting operations is **ordered in the same way** in $S_1$ and $S_2$.

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/conflict_eq1.JPG" style="zoom:0.4" />

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/conflict_eq2.JPG" style="zoom:0.4" />

* $S$ is **conflict serializable** if it is conflict equivalent to a serial schedule

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/conflict_serializable.JPG" style="zoom:0.4" />

* **Precedence Graph**
  * Test for conflict serializability
  * A directed graph $G=(V,E)$, where
    * $V$ includes all transactions involved in the schedule
    * $E$ consists of all edges $T_i\rightarrow T_j$ for which one of three conditions holds: (**Conflict Operations**)
      * $T_i$ executes write($X$) before $T_j$ executes read($X$)
      * $T_i$ executes read($X$) before $T_j$ executes write($X$)
      * $T_i$ executes write($X$) before $T_j$ executes write($X$)
      * 