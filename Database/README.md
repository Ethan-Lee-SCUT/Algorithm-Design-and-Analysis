# Database Review

题型：选择+大题

不会直接考定义，会考用自己的话描述（理解）

着重实践，例如ER diagram与逻辑间的转换 依赖关系的推导等

### Chapter-01 Introduction

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
* The **ER model** can be presented gra04phically by an **ER diagram**.

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

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/ternary_relationship.JPG" style="zoom:0.5" />





### Chapter-04 Relational Model

### 1. Terminology

* **Relation $\leftrightarrow$ Table**
  * denoted by $R(A_1,A_2,...,A_n)$ where $R$ is **relation name** and $(A_1,A_2,...,A_n)$ is the relation schema of $R$
* **Attribute $\leftrightarrow$ Column (Collectively a schema)**
  * denoted by $A_i$ 
* **Tuple $\leftrightarrow$ Row**
* **Attribute value $\leftrightarrow$ value stored in a table cell**
* **Domain $\leftrightarrow$ legal type and range of values of an attribute.**
  * denoted by $dom(A_i)$

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/terminology.JPG" style="zoom:0.4" />

#### 2. Foreign Key

* A set of attributes in one relation $R$ that is used to refer to a tuple in another relation $S$. (it must correspond to the primary key of the second relation)
  * Student
    * (<u>Student-id</u>, Student_Name)
  * Take
    * (<u>Student-id</u>, Course_id, semester_No)
  * Student-id in relation Student is a **primary key**
  * Student-id in relation Take is a **foreign key**

#### 3. ER-to-Relational Mapping (???)

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





### Chapter-05 Relational Algebra

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

#### 1. Projection $\pi_L(R)$

* Deletes attributes that are not in projection list $L$.
* Schema of result contains exactly the fields in the projection list, with the same names that they had in the (only) input relation.
* Projection operator **eliminates duplicates!**

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/projection.JPG" style="zoom:0.7" />

#### 2. Selection $\sigma_c(R)$

* Selects rows (records/tuples) that satisfy a selection **condition** $c$.

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/selection.JPG" style="zoom:0.7" />

#### 3. Set Operations

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

#### 4.Renaming $\rho$

   * If attributes or relations have the same name, it may be convenient to rename one

$$
   \rho(R'(N_1\rightarrow N'_1,...,N_n\rightarrow N'_n),R)
$$

   * The new relation $R’$ has the same instance as $R$, but its schema has attribute $N’_i$ instead of attribute $N_i$

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/renaming.JPG" style="zoom:0.5" />

#### 5. Division $A/B$

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

#### 6. Additional Operators - Outer Join

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





### Chapter-06 SQL

#### 1. Domain Types in SQL
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

#### 2. Data Definition Language (DDL) (Fundamental concepts)

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

#### 3. Data Manipulation Language (DML)

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

#### 4. Data Definition Language (DDL) (Advanced concepts)

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





### Chapter-08 Functional Dependency, Schema Refinement & Normal Forms
#### 1. Problems caused by redundancy

* Waste of resources of storage
* Potential inconsistency

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/redundancy.JPG" style="zoom:0.35" />

<img src="https://raw.githubusercontent.com/imethanlee/course-review/master/Database/pics/inconsistency.JPG" style="zoom:0.35" />

* Solution:
  * Decomposition

#### 2. Functional dependencies

* Functional dependency is a type of constraint that is **a generalization of the notation of key**.

* **Definition**

  * $R$ -- a relation schema, $\alpha\subset R, \beta\subset R$

  * $\alpha\rightarrow\beta$ if and only if

  ​        for any relation $r$ on $R$

  ​            for any two tuples $t_1,t_2$ of $r$

  ​                $\Pi_\alpha(t_1)=\Pi_\alpha(t_2)\Rightarrow\Pi_\beta(t_1)=\Pi_\beta(t_2)$

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
    * Additional rules (inferred from Armstrong's axioms)
      * $A\rightarrow B$ and $A\rightarrow C\Rightarrow A\rightarrow BC$ ???
      * $A\rightarrow BC\Rightarrow A\rightarrow B$ and $A\rightarrow C$
      * $A\rightarrow B$ and $BC\rightarrow D\Rightarrow AC\rightarrow D$
  * **Algorithm to compute $\alpha^+$**

  add pics