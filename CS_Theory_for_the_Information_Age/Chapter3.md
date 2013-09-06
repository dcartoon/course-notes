# Chapter 3

## Random Graphs(p. 46)

* Large graph study -> graphs + statistics. Like the move from classical to statistical mechanics

* Abstract, but convenient mathematically and guide in useful in  many situations.

*What are these?*
*How are they useful in other applications?*

## G(n,p) model
n = number of vertices
p = edge probability

Between each pair of vertices, the edge is present with probability p. P is often a function, like p = d/n

A "giant component" emerges even though all edges are statistically independent.

## Degree Distribution
The number of vertices of given degree.

In G(n,p) the degree of each vertex is the sum of n-1 independent random variables -> binomial distribution.

*Since n is large, using n instead of (n-1) for simplicity.*

### p. 48

Binomial distribution for G(n, 1/2). Mean = n/2, variance = n/4. Behaves like a normal distribution near the mean. Can also model general degree distribution for G(n, p) as binomial.

Binomial distribution falls off exponentially fast away from the mean. Most real world graphs are not like this.

Many follow the power law:

$$Number of degree k vertices = c * \frac{n}{k^r}$$

Where r is often just less than 3

**Theorem 3.1** 
Consider the probability of a given edge existing as following the Bernoulli distribution. For a vertex, the degree is the sum of n-1 independent Bernoulli random variables.

We can use Chernoff bounds to bound the probability that a given vertex will deviate from expected degree, np, by too much. Use the union bound when looking at all vertices. 

### p. 50

In many real applications, use p = d/n where d is constant so that expected degree is d even as n increases. As n goes to infinity, can use Poisson distribution as an approximation. 

## Existence of Triangles in G(n,d/n) (p.51)

*What are triangles in G(n, d/n)?*
3 vertices connected by edges.

For G(n, d/n), the number of triples of vertices grows as n^3, but the probability of an edge between two specific vertices goes down linearly with n. The probability of edges between three vertices in a triple is proportional to:

$$\frac{1}{n^3}$$

So the growth in triples of vertices is cancelled out. 
There are: ${n \choose 3}$ triples for n vertices.

If the probability of an edge is: $\frac{d}{n}$ the probability of a triangle is: $\left(\frac{d}{n}\right)^3$
and the resulting expected number of triangles is: $${n \choose 3}\left(\frac{d}{n}\right)^3 = \frac{d^3}{6}$$

It is possible for a graph of size n to have no triangles, and it is possible to derive the probablity that this will(not) happen(p.52).

## Phase Transitions

Analogous to abrupt changes in physical materials. These happen when p reaches 1/n (cycles form) and at log(n)/n  (disappearance of isolated vertices). The "giant component" also emerges at d = 1.

What is a *threshold*?

If there exists a function p(n) such that when 
$\lim_{n \to \infty}\frac{p_1(n)}{p(n)} = 0$ and $G(n, p_1(n))$ does not have a certain property, but
when $\lim_{n \to \infty}\frac{p_2(n)}{p(n)} = 0$ and $G(n, p_2(n))$
does have a certain property, then we say that a *phase transition* 
occurs and p(n) is the *threshold*. 

The existence of a giant component has a *sharp threshold* at
$1/n$.

*First moment method* follows from Markov inequality. If the expected number of occurrence of an item in a graph goes to zero,
the probability that the number of occurrences is onre ore more in a randomly selected graph also goes to zero. 

*The opposite is not true about the expected value of x(n) going to infinity meaning that a randomly chosen graph will likely have an item*. i.e., there could be a large number of occurrences in a vanishingly small number of graphs. This can be shown using the *second moment method* and Chebyshev inequality. 


## Threshold for graph diameter two

*Diameter* - The maximum length of the shortest path between a pair of nodes.

**Theorem 3.5** The property that G(n,p) has diameter two has a sharp threshold at $p=\sqrt{2}\sqrt{\frac{ln(n)}{n}}$.

The expected value, $E(x) \approx \frac{1}{2}n^{2-c^2}$.

So, when $c > \sqrt{2}$, $\lim_{n \to \infty} E(x) = 0$ and when $c < \sqrt{2}$, $\lim_{n \to \infty} E(X) = \infty$

## Disappearance of Isolated Vertices

Happens at $\frac{ln(n)}{n} because the giant component has absorbed all small components.

**Proof:** Let *x* be the number of isolated vertices in G(n,p). Then

$$E(x) = n(1-p)^{n-1}$$

By substituting $p = c\frac{ln(n)}{n} and taking the limit as $n \to \infty$, we end up with:

$$\lim_{n \to \infty} n^{1-c}$$

*This derivation is missing a step(maybe there's a certain expansion that can be used?)*

When c > 1, E(x), or the expected number of isolated vertices goes to 0. When c < 1, E(x) goes to infinity. If E(x) goes to 0, then it follows that almost all graphs have no isolated vertices. 
Otherwise, if E(x) goes to infinity, have to use the second moment argument to show that almost all graphs have an isolated vertex.

## Threshold for Graph Connectivity

# 3.2 Branching Processes(p.80)

A *branching process* is a method for creating a random tree. Read about generating functions.

By determining the expected number of children for each node, we can determine whether a tree will become extinct(finite number of children).

# 3.3 Nonuniform and Growth Models of Random Graphs(p. 85)

Graphs in which the expected degree of the vertices varies.  Real-world large graphs tend to have power law degree distributions.
The number of vertices of degree is: $f(d) \lt c/d^\alpha$

In a graph where half the vertices are degree 1 and half are degree 2, randomly selecting a vertex is equally likely to yield a vertex of degree 1 or 2.  However, randomly selecting an edge and then going to its endpoint is twice as likely to select a degree 2 vertex.  In general, the probability of reaching a vertex of degree i is proportional to $i\lambda_i$, where $\lambda_i$ is the fraction of vertices that are degree i.

## Giant Component in Random Graphs with Given Degree Distribution

There will be a giant component iff $\sum_{i=1}^{\infty} i(i-2)\lambda_i > 0$. There is a good intuitive explanation at the bottom of p. 86.  Consider starting at a random vertex and then exploring by followind edges. 
Vertices of degree 2 are neutral with regards to increasing graph size(i.e. enter via one edge and exit via one edge). 
Vertices of degree i > 2 increase the frontier by i-2 edges. $i\lambda_i$ is the probability of reaching a vertex of degree i.  

# 3.4 Growth Models(p.87)

Many real graphs are grown over time from small graphs.
There are multiple ways to select which vertices get new edges.  Selecting randomly with uniform probability -> without preferential attachment.  An alternative approach is with probability proportional to the degree of the vertex -> preferential attachment.

Without preferential attachment:
1. At each unit of time generate a new vertex
2. Randomly select two vertices and add an edge with probability $\delta$
    a. It is possible to add an edge between two already connected vertices.  The graph then becomes a multi-graph.


# 3.5 Small World Graphs(p. 95)

This sub-chapter would be well-served by a few illustrations.  Imagine a 2D lattice of connected vertices.  Any vertex is probabilistically also connected to a non-neighboring vertex inversely proportional to the Manhattan distance between those vertices raised to some exponent.  I.e.: Probability of long-distance connection from u->v = $\frac{1}{d^r(u,v)}$, where r is a constant, and d(u,v) is the distance between u and v.
