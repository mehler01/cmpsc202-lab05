# Lab 5: Introduction to Graphs

This lab introduces you to a new data structure: graphs. Graphs are a fundamental data structure in computer science and are used to model relationships between objects. In this lab, you will learn about the basic concepts of graphs, including vertices, edges, and various properties of graphs. 

**Instructions:** To complete this lab, you may work in groups, but you must write your solutions yourself. Complete all of the exercises below. Once you have completed the lab, push your changes to your forked repository.

Your name: Josh Mehler

## Introduction to Graphs

Graphs consist of a set of vertices (also called nodes) and a set of edges that connect pairs of vertices. Graphs are used to model relationships between objects in various domains. We can represent real-world problems using the language of graphs and solve them using graph algorithms. Common applications include finding the shortest driving route between cities, identifying fraud in financial transactions, or determining social media influencers. Graphs can represent diverse systems like communication networks, circuits, internet routing, social relationships, and protein interactions.

![Representation of a graph](images/representations.png)

## Core Definitions
- **Graph**: A graph $G=(V,E)$ consists of a set of nodes (vertices) $V$ and a set of edges (pairs of vertices) $E$.
- **Size**: A graph has $n=\vert{}V\vert{}$ vertices and $m=\vert{}E\vert{}$ edges.
- **Edges**: An edge $e=\{u,v\}$, usually written as $e=(u,v)$, is a set of vertices. The vertices $u$ and $v$ are neighbors, are adjacent, and are the endpoints of $e$. The edge $e$ is incident to $u$ and $v$.

### Exercise 1

For the following graph, list the vertices and edges. What is the size of the graph?

![ex1](images/ex1.png)

- **Vertices**: $V=\{0,1,2,3,4\}$

- **Edges**: $E=\{(0,1),(0,2),(0,3),(1,2),(3,4)\}$

- **Size**: $|V|=5,\ |E|=5$


## Paths and Distances

- **Path**: A sequence $P=v_1, v_2, ..., v_k$ such that each consecutive pair $v_i$, $v_{i+1}$ are joined by an edge in $G$.
- **Simple Path**: A path where all vertices are distinct.
- **Cycle**: A path $c=v_1, v_2, ..., v_{k-1}, v_k$ where the first and last vertices are the same ($v_1=v_k$), the first $k-1$ vertices are distinct, and all edges are distinct.
- **Distance**: The distance from vertex $u$ to vertex $v$ is the minimum number of edges in a $u-v$ path.

### Exercise 2

The graph below shows the state of the internet in 1970s. Vertices represent computers and edges represent connections between them. Use this graph to answer the following questions.

![ex2](images/ex2.png)

1. Find a path from RAND to SRI. What is the distance between these two vertices?

- **Path**: $P=RAND,\ UCLA,\ SRI$

- **Distance**: $|E|=2$

2. Find a path from RAND to MIT. What is the distance between these two vertices?

- **Path**: $P=RAND,\ BBN,\ MIT$

- **Distance**: $|E|=2$

3. Classify each of the following paths as simple, not simple, or a cycle. State your reasoning!

- **Path 1**: LINC, MIT, LINC, CASE
- **Classification**: This is not simple because all vertices are not distinct, LINC appears twice. Additionally, it is not a cycle because the first 3 terms are not distinct and the first and last terms are different.

- **Path 2**: UCSB, SRI, STAN, UCLA, UCSB
- **Classification**: This is a cycle because the first and last terms are the same (UCSB), and also the first four terms are distinct.

- **Path 3**: UCSB, SRI, UTAH
- **Classification**: This is a simple path because all terms are distinct.

## Connectivity and Trees

- **Connected Graph**: A graph with paths between every pair of vertices.
- **Tree**: A connected graph with no cycles.

### Exercise 3

Think through these with your partner(s) before answering the questions below. If you get stuck, try drawing a few graphs to help you visualize the problem.

1. A connected graph is defined as a graph with paths between every pair of vertices. If a graph with 10 vertices has exactly 8 edges, is it possible for the graph to be connected? Explain your reasoning based on the minimum number of edges required to link all vertices.

    No, this graph could not be a connected graph. At minimum, one element must be connected to all nine other elements. Therefore, there must be at least nine vertices in the graph (connecting one element to all the others). Since this graph has eight vertices, it cannot be a connected graph. Note that the total number of vertices for a connected graph with $n$ elements is $(n-1)+(n-2)+(n-3)+...+2+1=\sum_{i=1}^{n-1}{i}$. Fix the first element. Then it must be connected to the other $n-1$ elements. Then fix the second element. It is already connected to the first element, so it needs to be connected to the remaining $n-2$ elements. You can continue this trend until you get that the last two elements need to be connected together.

2. A tree is a connected graph with no cycles. If you take an existing tree and add exactly one new edge between two non-adjacent vertices, what structural property is immediately violated?

    Once you add an edge between two non-adjacent vertices, you immediately create a cylce. Say that you have the vertices $p_1,\ p_2$. In order for $p_1$ and $p_2$ to not be adjecent, there must be a vertex in between $p_1$ and $p_2$, call it $p'$. Thus we have edges: $(p_1,p')$ and $(p',p_2)$. If we add the edge $(p_2,p_1)$, we create the path: $p_1,\ p',\ p_2,\ p_1$, which is closed because it starts and ends with $p_1$.