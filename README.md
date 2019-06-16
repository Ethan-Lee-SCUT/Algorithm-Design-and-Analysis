# Algorithm Review

### Chapter 01 Introduction

#### KEY POINTS:

* What is an **algorithm** and its **properties**. 

#### 1. What is an algorithm?

An algorithm is **a composition of a set of steps to solve a specific problem**. It should satisfy the following properties:

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

#### KEY POINTS:

* What is the goodness of an algorithm? 

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

#### KEY POINTS:

* Shortest paths on a multi-stage graph
* Minimum spanning trees (MST) algorithms
  * Kruskal’s algorithm
  * Prim’s algorithm
* Knapsack problem. 

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

#### 4. Dijkstra’s algorithm for shortest path ???

​	add something

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

#### KEY POINTS:

* 2-D maxima finding problem

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

#### KEY POINTS:

* Hamiltonian circuit problem
* Personnel assignment problem
* Traveling salesperson optimization problem

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
* The search strategy consists of **best-first search**, 每次扩展除了根据界限，还会根据best-first search优先选择$f-cost$最少的节点扩展 ???

|                             BFS                              |                             DFS                              |                           BestFS                            |             Branch and bound strategy             |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :---------------------------------------------------------: | :-----------------------------------------------: |
| All nodes on the level of the tree are examined before the nodes on the next level are examined. |       We always select the deepest node for expansion.       |    Combine depth-first search and breadth-first search.     |      cut the non-optimal feasible solutions.      |
|       A queue can be used to hold all expanded nodes.        | Hill climbing (A stack can be used to guide the depth-first search.) | (A priority queue (heap) can be used as the data structure) | A multi-stage graph optimal problem can be solved |

#### 7. Personnel assignment problem (by Branch and Bound)



<img src="https://github.com/Ethan-Lee-SCUT/Algorithm-Design-and-Analysis/blob/master/pic/%E5%9B%BE%E7%89%873.png?raw=true" style="zoom:0.4" />

* Cost matrix

| Person\Jobs |  1   |  2   |  3   |  4   |
| :---------: | :--: | :--: | :--: | :--: |
|      1      |  29  |  19  |  17  |  12  |
|      2      |  32  |  30  |  26  |  28  |
|      3      |  3   |  21  |  7   |  9   |
|      4      |  18  |  13  |  10  |  15  |

* **Reduced cost matrix**
  * Subtract a constant from each row and each column respectively such that **-each row and each column contains at least one zero**. 
  * Total cost subtracted: 12+26+3+10+3 = 54
  * This is a **lower bound** of our solution.

| Person/Jobs |  1   |  2   |  3   |  4   |       |
| :---------: | :--: | :--: | :--: | :--: | :---: |
|      1      |  17  |  4   |  5   |  0   | (-12) |
|      2      |  6   |  1   |  0   |  2   | (-26) |
|      3      |  0   |  15  |  4   |  6   | (-3)  |
|      4      |  8   |  0   |  0   |  5   | (-10) |
|             |      | (-3) |      |      |       |

* **Solution tree**

<img src="https://github.com/Ethan-Lee-SCUT/Algorithm-Design-and-Analysis/blob/master/pic/%E5%9B%BE%E7%89%874.png?raw=true" style="zoom:0.7" />

#### 8. Traveling salesman problem ???

add something

#### 9. A* algorithm

* Used to solve optimization problems.
* Using the best-first strategy.
* **If a feasible solution (goal node) is obtained, then it is optimal and we can stop.**
* Cost function of node $n$: $f(n)=g(n)+h(n)$
  * $g(n)$: cost from root to node $n$
  * $h(n)$: estimated cost from node $n$ to a goal node.

* For shortest path finding:
  * $g(n)=$ path cost
  * $h(n)=$ estimated cost $=min\{next \ edges \}$ 

#### 10. 0/1 Knapsack problem





### Chapter 06 Prune and search

#### KEY POINTS:

* What is the Prune and search approach and the general prune-and-search? 
* Find the $k^{th}$ largest element in set $S$.

#### 1. What is pruning?

​	The prune-and-search strategy always consists of **several iteration**. At each iteration, it prunes away a fraction, say $f$, of the data, and then it invokes the same algorithm recursively to solve the problem for the remaining data.

#### 2. The significance of pruning

​	It is used to solve **optimization problems** and usually gives **efficient** algorithms for solving these problems. It make the problem so small to be solved directly in a constant time. Pruning reduces the size of a learning tree without reducing predictive accuracy.

#### 3. $k^{th}$ largest element

* $S={a_1, a_2, …, a_n}$
* Let $p \in S$, use $p$ to partition $S$ into 3 subsets $S_1 , S_2 , S_3$: 
  * $S_1= \{ a_i|a_i<p, 1 \le i \le n\}$
  * $S_1= \{ a_i|a_i=p, 1 \le i \le n\}$
  * $S_1= \{ a_i|a_i>p, 1 \le i \le n\}$

* 3 cases:
  * If $|S_1| > k$ , then the $k^{th}$ smallest element of $S$ is in $S_1$, prune away $S_2$ and $S_3$.
  * Else, if $|S_1| + |S_2| \ge k$, then $p$ is the $k^{th}$ smallest element of $S$.
  * Else, the kth smallest element of S is the $(k - |S_1| - |S_2|)^{th}$ smallest element in $S_3$, prune away $S_1$ and $S_2$.





### Chapter 07 Dynamic Programming

#### KEY POINTS:

* What is dynamic programming strategy? 
* The shortest path in multistage graphs (include forward approach, and Backward approach)
* Longest common subsequence (LCS) problem
* 0/1 knapsack problem
* Matrix-chain multiplication

#### 1. What is dynamic programming strategy? 

​	DP is an algorithm design method that can be used when the solution to a problem may be viewed as the result of a sequence of decisions



#### 2. The shortest path in multistage graph

* **Multistage graph**

<img src="https://raw.githubusercontent.com/Ethan-Lee-SCUT/Algorithm-Design-and-Analysis/master/pic/%E5%9B%BE%E7%89%875.png" style="zoom:0.8" />

* **Define**
  * $d(V_1,V_2)$ is the minimum distance from $V_1$ to $V_2$

* **Forward approach (Backward reasoning)**
  * $d(S, A) = 1$
  * $d(S, B) = 2$
  * $d(S, C) = 5$
  * $d(S,D)=min \{d(S,A)+d(A,D), d(S,B)+d(B,D) \} = min \{1+4, 2+9 \} = 5$
  * $d(S,E)=min \{d(S,A)+d(A,E), d(S,B)+d(B,E) \} = min \{1+11, 2+5 \} = 7$
  * $d(S,F)=min \{d(S,B)+d(B,F), d(S,C)+d(C,F) \} = min \{2+16, 5+2 \} = 7$
  * $d(S,T) = min \{d(S, D)+d(D, T), d(S,E)+d(E,T), d(S, F)+d(F, T) \}=min \{ 5+18, 7+13, 7+2 \} = 9$
* **Backward approach (Forward reasoning) **
  * $d(S, A) = 1$
  * $d(S, B) = 2$
  * $d(S, C) = 5$
  * $d(S,D)=min \{d(S,A)+d(A,D), d(S,B)+d(B,D) \}= min \{ 1+4, 2+9 \} = 5$
  * $d(S,E)=min \{d(S,A)+d(A,E), d(S,B)+d(B,E) \}= min \{ 1+11, 2+5 \} = 7$
  * $d(S,F)=min \{d(S,B)+d(B,F), d(S,C)+d(C,F) \}= min \{ 2+16, 5+2 \} = 7$
  * $d(S,T) = min \{d(S, D)+d(D, T), d(S,E)+d(E,T), d(S, F)+d(F, T) \}= min \{ 5+18, 7+13, 7+2 \}=9 $



#### 3. Longest common subsequence (LCS) problem

* **Multistage graph**

<img src="https://raw.githubusercontent.com/Ethan-Lee-SCUT/Algorithm-Design-and-Analysis/master/pic/%E5%9B%BE%E7%89%876.png" style="zoom:0.6" />

* Define
  * $L_{i,j}$ be the length of longest common longest common subsequence of $a_1 a_2 ... a_i$ from $A$ and $b_1 b_2 ... b_j$ from $B$.

$$
L_{i,j}=\left\{
\begin{aligned}
&L_{i-1,j-1}+1&if\ a_i=b_j  \\
&max \{ L_{i,j-1},L_{i-1,j}\}&if\ a_i\ne b_j \\

\end{aligned}
\right.
$$

* Solve

  $e.g.\ A=b a c a d\ B= a c c b a d c b$

<img src="https://raw.githubusercontent.com/Ethan-Lee-SCUT/Algorithm-Design-and-Analysis/master/pic/%E5%9B%BE%E7%89%877.png" style="zoom:0.7" />

#### 4. 0/1 knapsack problem

* **Multistage graph**

<img src="https://raw.githubusercontent.com/Ethan-Lee-SCUT/Algorithm-Design-and-Analysis/master/pic/%E5%9B%BE%E7%89%8712.png" style="zoom:0.6" />

* **Define**
  * $f_i(Q)$ be the the value of an optimal solution to objects $1,2,3,…,i$ with capacity $Q$

$$
f_i(Q)=\left\{
\begin{aligned}
&f_{i-1}(Q)&if\ Q<W_i  \\
&max \{f_{i-1}(Q), f_{i-1}(Q-W_i)+P_i\} &if\ Q\ge W_i \\
\end{aligned}
\right.
$$

* **Solution for the following case (M=80)**

| $i$  | $W_i$ | $P_i$ |
| :--: | :---: | :---: |
|  1   |   5   |  50   |
|  2   |  25   |  200  |
|  3   |  30   |  180  |
|  4   |  45   |  225  |

| I\Q  |  0   |  5   |  10  |  15  |  20  |  25  |  30  |  35  |  40  |  45  |  50  |  55  | 60   |  65  |  70  |  75  |   80    |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | ---- | :--: | :--: | :--: | :-----: |
|  0   |  0   |  0   |  0   |  0   |  0   |  0   |  0   |  0   |  0   |  0   |  0   |  0   | 0    |  0   |  0   |  0   |    0    |
|  1   |  0   |  50  |  50  |  50  |  50  |  50  |  50  |  50  |  50  |  50  |  50  |  50  | 50   |  50  |  50  |  50  |   50    |
|  2   |  0   |  50  |  50  |  50  |  50  | 200  | 250  | 250  | 250  | 250  | 250  | 250  | 250  | 250  | 250  | 250  |   250   |
|  3   |  0   |  50  |  50  |  50  |  50  |  50  | 250  | 250  | 250  | 250  | 250  | 380  | 430  | 430  | 430  | 430  |   430   |
|  4   |  0   |  50  |  50  |  50  |  50  |  50  | 250  | 250  | 250  | 250  | 275  | 275  | 275  | 275  | 275  | 475  | **475** |



#### 5. Matrix-chain multiplication

* **Multistage graph**

<img src="https://raw.githubusercontent.com/Ethan-Lee-SCUT/Algorithm-Design-and-Analysis/master/pic/%E5%9B%BE%E7%89%878.png" style="zoom:0.5" />

* **Define**
  * $m(i,j)$ denotes the minimum cost for computing $A_i\times A_{i+1}\times ...\times A_j$

$$
m(i,j)=\left\{
\begin{aligned}
&0&if\ i=j  \\
&\mathop{min}_{i\leq k\leq j-1 } \{m(i,k)+m(k+1,j)+p_{i-1}p_kp_j\} &if\ i < j \\
\end{aligned}
\right.
$$

* **Solution for the following case**

$$
M=\mathop{M_1}_{[10\times 20]}\times \mathop{M_2}_{[20\times 50]}\times \mathop{M_3}_{[50\times 1]}\times \mathop{M_4}_{[1\times 100]}
$$

|   $m_{1,1}=0$   |  $m_{2,2}=0$   |  $m_{3,3}=0$   | $m_{4,4}=0$ |
| :-------------: | :------------: | :------------: | :---------: |
| $m_{1,2}=10000$ | $m_{2,3}=1000$ | $m_{3,4}=5000$ |             |
| $m_{1,3}=1200$  | $m_{2,4}=3000$ |                |             |
| $m_{1,4}=2200$  |                |                |             |





