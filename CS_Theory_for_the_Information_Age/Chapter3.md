# Chapter 3

## Random Graphs(p. 46)

* Large graph study -> graphs + statistics.  Like the move from classical to statistical mechanics

* Abstract, but convenient mathematically and guide in useful in  many situations.

*What are these?*
*How are they useful in other applications?*

## G(n,p) model
n = number of vertices
p = edge probability

Between each pair of vertices, the edge is present with probability p.  P is often a function, like p = d/n

A "giant component" emerges even though all edges are statistically independent.

## Degree Distribution
The number of vertices of given degree.

In G(n,p) the degree of each vertex is the sum of n-1 independent random variables -> binomial distribution.

*Since n is large, using n instead of (n-1) for simplicity.*

### p. 48

Binomial distribution for G(n, 1/2).  Mean = n/2, variance = n/4.  Behaves like a normal distribution near the mean.  Can also model general degree distribution for G(n, p) as binomial.

Binomial distribution falls off exponentially fast away from the mean.  Most real world graphs are not like this.

Many follow the power law:

$$Number of degree k vertices = c * \frac{n}{k^r}$$

Where r is often just less than 3

**Theorem 3.1** 
Consider the probability of a given edge existing as following the Bernoulli distribution.  For a vertex, the degree is the sum of n-1 independent Bernoulli random variables.

We can use Chernoff bounds to bound the probability that a given vertex will deviate from expected degree, np, by too much.  Use the union bound when looking at all vertices. 

### p. 50

In many real applications, use p = d/n where d is constant so that expected degree is d even as n increases.  As n goes to infinity, can use Poisson distribution as an approximation. 

## Existence of Triangles in G(n,d/n) (p.51)

*What are triangles in G(n, d/n)?*
3 vertices connected by edges.

For G(n, d/n), the number of triples of vertices grows as n^3, but the probability of an edge between two specific vertices goes down linearly with n.  The probability of edges between three vertices in a triple is proportional to:

$$\frac{1}{n^3}$$

So the growth in triples of vertices is cancelled out. 
There are: ${n \choose 3}$ triples for n vertices.

If the probability of an edge is: $\frac{d}{n}$ the probability of a triangle is: $\left(\frac{d}{n}\right)^3$
and the resulting expected number of triangles is: $${n \choose 3}\left(\frac{d}{n}\right)^3 = \frac{d^3}{6}$$

It is possible for a graph of size n to have no triangles, and it is possible to derive the probablity that this will(not) happen(p.52).

## Phase Transitions

Analogous to abrupt changes in physical materials.  These happen when p reaches 1/n (cycles form) and at log(n)/n  (disappearance of isolated vertices).  The "giant component" also emerges at d = 1.

What is a *threshold*?

If there exists a function p(n) such that when 
$\lim_{n \to \infty}\frac{p_1(n)}{p(n)} = 0$ and $G(n, p_1(n))$ does not have a certain property, but
when $\lim_{n \to \infty}\frac{p_2(n)}{p(n)} = 0$ and $G(n, p_2(n))$
does have a certain property, then we say that a *phase transition* 
occurs and p(n) is the *threshold*. 

The existence of a giant component has a *sharp threshold* at
$1/n$.

*First moment method* follows from Markov inequality.  If the expected number of occurrence of an item in a graph goes to zero,
the probability that the number of occurrences is onre ore more in a randomly selected graph also goes to zero. 

*The opposite is not true about the expected value of x(n) going to infinity meaning that a randomly chosen graph will likely have an item*.  i.e., there could be a large number of occurrences in a vanishingly small number of graphs.  This can be shown using the *second moment method* and Chebyshev inequality.  


## Threshold for graph diameter two

*Diameter* - The maximum length of the shortest path between a pair of nodes.

**Theorem 3.5** The property that G(n,p) has diameter two has a sharp threshold at $p=\sqrt{2}\sqrt{\frac{ln(n)}{n}}$.

The expected value, $E(x) \approx \frac{1}{2}n^{2-c^2}$.

So, when $c > \sqrt{2}$, $\lim_{n \to \infty} E(x) = 0$ and when $c < \sqrt{2}$, $\lim_{n \to \infty} E(X) = \infty$

## Disappearance of Isolated Vertices

Happens at $\frac{ln(n)}{n} because the giant component has absorbed all small components.

## Transitions

Branching Processes

Nonuniform and Growth Models of Random Graphs

Growth Models

Small World Graphs

