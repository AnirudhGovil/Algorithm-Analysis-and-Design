# Week3

## Greedy Strategy

Fundamentally the Greedy Strategy means picking the local optimum in every step hoping the get a global optimum overall.

We look at the Greedy Strategy to solve the MST problem. Our solution relies on the Cut property for its correctness.

We can define a cut as the splitting of a graph’s nodes to two non-empty sets A and B.

We define a crossing edge as an edge which connects a node from set A to a node from set B.

Cut Property states that given any cut, the minimum weight crossing edge is in the MST.

The proof for the cut property is as follows: Suppose (for the sake of contradiction) that the minimum crossing edge e were not in the MST. Since it is not a part of the MST, if we add that edge, a cycle will be created. Because there is a cycle, this implies that some other edge f must also be a crossing edge (for a cycle, if e crosses from set A to set B, there must be another edge that crosses back over to set A). Thus, we can remove f and keep e, and this will give us a lower weight spanning tree. But this is a contradiction because we supposedly started with a MST, but now we have a collection of edges which is a spanning tree but that weighs less, thus the original MST was not actually minimal. As a result, the cut property must hold.

Using Cut property, one popular algorithm to find the MST is Krusal's algorithm. Which simply adds the lightest edge that doesn't result in a cycle, repeatedly until impossible.
The Cut Property gurantees that as long as we don't create a cycle, the lightest edge will be the minimum weight crossing edge which implies it is in the MST. The Greedy appraoch of choosing the local optimum i.e. the lightest non-cyclic edge in this case yields an efficeint algorithm.
