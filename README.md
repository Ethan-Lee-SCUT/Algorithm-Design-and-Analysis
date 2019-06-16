# Algorithm Review

### Chapter 01 Introduction

#### 1. What is an algorithm?

An algorithm is composed of a set of steps for solving a specific problem. It should satisfy the following properties:

1. **Finiteness** (the number of steps should be finite)
2. **Definiteness** (to compute 5/0 is not definite)
3. **Effectiveness** (to compute 1/3 as an infinite decimal is not effective)
4. **Zero or more inputs** and **one or more outputs**
5. **Termination** (OS is not an algorithm)]

such as a recipe(食谱), a flowchart, a program.

#### 2. Algorithm Representation?

1. Natural language
2. Flowchart
3. Pseudo code
4. High level language

#### 3.  Difference between Algorithm and Problem

1. Algorithm is a group of roles.
2. A step-by-step procedure for solving a problem or accomplishing some end.
3. An algorithm solves a problem if it produces an acceptable output on **EVERY** input.

#### 4. Difference between Algorithm and Numerical Analysis

* Numerical Analysis is used to solve some numerical problems. 

#### 5. Difference between Algorithm and Artificial Intelligence AI

1. Artificial Intelligence AI is used to solve all kinds of problems in almost all of fields. 
2. Algorithms solving well specific computational problem.

#### 6. Measure the goodness of algorithms

1. Efficiency 
2. Asymptotic notations: e.g. $O(n^2)$
3. Worst case
4. Average case
5. Amortized

#### 7. Measure the difficulty of problems

1. NP-complete
2. Undecidable
3. Lower bound



### Chapter 02 The complexity of Algorithms and The lower Bounds of Problems

#### 1. The goodness of an algorithm

1. Time complexity (more important)

2. Space complexity

3. For a parallel algorithm

   * time-processor product

4. For a VLSI circuit :

   * area-time ($AT$, $AT^2$)  

   

#### 2. Some simple questions

1. 问题的边界是否唯一？
2. 这个问题的lower bound和算法有无关系?

* $O$: Upper bound
* $Ω$: Lower Bound (Not unique)
* $θ$: Exact
* $o$: Exact, even constant



### Chapter 03 The Greedy Method

​	Suppose that a problem can be solved by a sequence of decisions.  The greedy method has that **each decision is locally optimal.  These locally optimal solutions will finally add up to a globally optimal solution.**

#### 1. Minimum Spanning Tree (MST)

* $G=(V,E)$: weighted connected **undirected graph**

* **Spanning Tree**: $S=(V,T)$, $T\subseteq E$, undirected tree
* **Minimum Spanning Tree**: a spanning tree with the smallest total weight. 


#### 2. Kruskal’s algorithm for MST

1. Sort all edges into nondecreasing order. 
2. Add the next **smallest weight edge** to the forest if it **does not form a cycle**.
3. Stop if $n-1$ edges. Otherwise, go to Step.

#### 3. Prim’s algorithm for MST

1. Sort all edges between A and B. 
2. Add the next smallest weight edge to the forest;
3. Renew A and B sets;
4. Stop if n-1 edges. Otherwise, go to Step2.
5. Result

#### 4. Dijkstra’s algorithm for shortest path



#### 5. Activity On Edge (AOE) Networks

#### 6. 2-way merging problem 

#### 7. Huffman codes

#### 8. Knapsack problem

How to select them according to optimal value?

1. Calculate the profit per weight $P/W$.
2. Sort them into decreasing order. 

#### 9. Job Sequencing with Deadlines

#### 10. Optimal Storage on Tapes



### Chapter 04 Divide-and-Conquer Strategy

#### 1. What is divide and conquer?

​	A powerful paradigm for designing efficient algorithms. This approach first divides a problem into **two smaller sub-problems** and each sub-problem is **identical to its original problem**. Both of them are then solved and the sub-solutions are **finally merged into the final solution**.  

#### 2. General divide-and-conquer algorithm

1. If the problem size is small, solve this problem directly; otherwise, **split** the original problem into 2 sub-problems with equal sizes.
2. **Recursively** solve these 2 sub-problems by applying this algorithm.
3. **Merge** the solutions of the 2 sub- problems into a solution of the original problem.

#### 3. What is the difference between the divide-and-conquer method and the finite element method?

1. Finite element method split the problem into some sub-problems and the number of the sub-problems is **fixed** and solve the sub-problems one by one. Divide and conquer solves the problem recursively. The main difference is the finite element problem is **continuous** and the divide-and-conquer is **discrete**.
2. Finite element method solves the problem part by part. And **do not use the recursive methods**. However divide and conquer **use the recursive methods** to solve each sub-problem recursively.

#### 4. 2-D maxima finding problem

**Definition**: A point $(x_1, y_1)$ dominates $(x_2, y_2)$ if $x_1 > x_2$ and $y_1 > y_2$.  A point is called a maxima if no other point dominates it.

* Straightforward method: $O(n^2)$
* Divide and conquer: $O(nlogn)$

1. If $S$ contains only one point, return it as the maxima. Otherwise, find a line $L$ perpendicular to the $X$-axis which **separates** $S$ into $S_L$ and $S_R$, with equal sizes.
2. **Recursively** find the maximal points of $S_L$ and $S_R$ .
3. Find the largest $y$-value of $S_R$, denoted as $y_R$. Discard each of the maximal points of $S_L$ if its $y$-value is less than $y_R$.

#### 5. Closest pair problem ???

1. Sort points in $S$ according to their $y$-values.
2. If $S$ contains only one point, return **infinity** as its distance.
3. Find a median line $L$ perpendicular to the $X$-axis to divide $S$ into $S_L$ and $S_R$, with equal sizes.
4. **Recursively **apply Step 2 and 3 to solve the closest pair problems of $S_L$ and $S_R$.  Let $d_L (d_R)$ denote the distance between the closest pair in $S_L (S_R)$.  Let $d = min(d_L, d_R)$.
5. For a point $P$ in the half-slab bounded by $L-d$ and $L$, let its $y$-value be denoted as $y_P$ .  For each such $P$, find all points in the half-slab bounded by $L$ and $L+d$ whose $y$-value fall within $y_P+d$ and $y_P-d$.  If the distance $d'$ between $P$ and a point in the other half-slab is less than $d$, let $d=d'$.  The final value of $d$ is the answer.



### Chapter 05 Tree Searching Strategy

#### 1. What is tree search?
​	All the possible solution can be included and represented in the tree.

#### 2. Breadth-first Search

* All nodes on a level of tree are examined before the nodes on the next level are examined.
* Data structure: **Queue**

1. Form a 1-element queue consisting of the root node;
2. Test to see if the first element in the queue is goal node or not? If it is, stop; otherwise, go to step 3;
3. Remove the first element from the queue. Add the first element’s descendants, if any, to the end of the queue;
4. If the queue is empty, then failure. Otherwise, go to step 2.

#### 3. Depth-first search(DFS)

* Select the deepest node for expansion
* Data structure: **Stack**

1. Form a 1-element stack consisting of the root node;
2. Test to see if the first element in the stack is goal node or not? If it is, stop; otherwise, go to step 3;
3. Remove the first element from the stack . Add the first element’s descendants, if any, to the top of the stack ;
4. If the stack is empty, then failure. Otherwise, go to step 2.

#### 4. Hill climbing

* A variant of DFS
* Selects the locally optimal node (greedy method used here) to expand.

#### 5. Best-first search

* Select the node with the best estimated cost.
* Data structure: **Min/Max heap**

1. Form a one-element heap consisting of the root node
2. Remove the first element from the list. Expand the first element. If one of the descendants of the first element is a goal node, then stop; otherwise, add the descendants into the heap.
3. Sort the heap (automatically by min/max heap).
4. If the list is empty, fail. Otherwise, go to step 2

#### 6. Branch-and-bound strategy

* The solution space should be cut by discovering that many feasible solutions can not be optimal solutions.
* The search strategy consists of **hill-climbing**, 每次扩展除了根据界限，还会根据hill climbing 优先选择path cost最少的节点扩展?

|                             BFS                              |                             DFS                              |                           BestFS                            |             Branch and bound strategy             |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :---------------------------------------------------------: | :-----------------------------------------------: |
| All nodes on the level of the tree are examined before the nodes on the next level are examined. | We always select the deepest local optimal node for expansion. |    Combine depth-first search and breadth-first search.     |      cut the non-optimal feasible solutions.      |
|       A queue can be used to hold all expanded nodes.        | Hill climbing (A stack can be used to guide the depth-first search.) | (A priority queue (heap) can be used as the data structure) | A multi-stage graph optimal problem can be solved |

















