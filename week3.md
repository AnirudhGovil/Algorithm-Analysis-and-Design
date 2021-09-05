# Week3

## Applying Divide and Conquer to Polynomial Multiplication

The naive approch considers polynomials in their coefficient representation, and repeatedly applies the distributive property over these lists of coefficients, taking d<sup>2</sup> time to executre,w here d is the degree of the larger of the 2 polynomials.

The first key insight is to express polynomials as a set of d+1 unique points, as only one polynomial of degree d can be uniquely mapped to d+1 unique points. Let's call this the value representation.

Now to multiply two polynomials of degree d each, we simply convert them to their value repsentation at 2d+1 points and multiply them with each other to get the value representation of the resulting polynomial of degree 2d. Thus multiplication is now an 0(d) operation.

Our overarching approach is, given two polynomials of degree d, convert them to their their value representations. Multiply these value representations to get the value representation of the resulting polynomial in 0(d) time and convert the value representation of the resulting polynomial back into the coefficeint representation.

## Fast Fourrier Transform

The key here is to optimise the conversion from coefficient representation to value representation and vice versa.

In order to optimise the process of converting coefficient representation into value representation, we can consider positive - negative pairs for evaulation. In even degree polynomials, this means if evaulating the the polynomial at a gives f(a) means the polynomial at -a is also f(a), while in odd degree polynomials the polynomial at -a will give -f(a). Thus we can half the number of evaulations required.

We factor a polynomial inot two halves, even degree terms and odd degree terms. We then take an x out of the odd degree terms to get 2 polynomials with only even degree terms. These new polynomials are of half the degree of our original polynomials whcih means we need to evaulte only half as many points.

However, these new polynomials can be further split into 2 just like we did before, giving rise a a recursive approach.

it is important to notice that the new ploynomials are actually polynomials of not x but x<sup>2</sup> which means that in order to find positive negative pairs even for an x<sup>2</sup> polynomial, we need to expand the domain to complex numbers, so that the recursion can continue.

If n is the smallest power of 2 that bounds the degree of the polynomial, the n<sup>th</sup> roots of unity give us our positive negative pair evaulations points. The n<sup>th</sup> roots of unity are the solutions of z<sup>n</sup>=1. Using Euler's formula, we can compactly write them as &omega;<sup>2&pi;i/n</sup>.

Thus we evaulate the polynomial at [1,&omega;,&omega;<sup>2</sup>,&omega;<sup>3</sup>...]. When we split into 2 smaller polynomials and square the roots of unity to [1,&omega;<sup>2</sup>,&omega;<sup>4</sup>...] we get half the number of points and perfect positive - negative pairs.

Thus by recursively splitiing the polynomial into halves, evaulting it at roots of unity, and merging after evaulation, we can get the the value representation of the polynomial in O(nlogn) time.

## Concluding polynomial mutiplication

After using the FFT to find a value representation and multiplying the value representations together, we must interpolta the value representation back into. Since evaulation can be represented as applying a transformation matrix to a vector of coefficeints to get a vector of values (value representation). Since our evaluation points are the  n<sup>th</sup>roots ofunity, our transformation matrix is the DFT matrix (Discrete Fourrier Transform) interpolation involves multiplying the value representaion vector into the inverse of the DFT matrix to get the vector of coeffcients.

[!InverseDFT](DFTmatrix.png)

## Greedy Strategy

Fundamentally the Greedy Strategy means picking the local optimum in every step hoping the get a global optimum overall.

We look at the Greedy Strategy to solve the MST problem. Our solution relies on the Cut property for its correctness.

We can define a cut as the splitting of a graph’s nodes to two non-empty sets A and B.

We define a crossing edge as an edge which connects a node from set A to a node from set B.

Cut Property states that given any cut, the minimum weight crossing edge is in the MST.

The proof for the cut property is as follows: Suppose (for the sake of contradiction) that the minimum crossing edge e were not in the MST. Since it is not a part of the MST, if we add that edge, a cycle will be created. Because there is a cycle, this implies that some other edge f must also be a crossing edge (for a cycle, if e crosses from set A to set B, there must be another edge that crosses back over to set A). Thus, we can remove f and keep e, and this will give us a lower weight spanning tree. But this is a contradiction because we supposedly started with a MST, but now we have a collection of edges which is a spanning tree but that weighs less, thus the original MST was not actually minimal. As a result, the cut property must hold.

Using Cut property, one popular algorithm to find the MST is Krusal's algorithm. Which simply adds the lightest edge that doesn't result in a cycle, repeatedly until impossible.
The Cut Property gurantees that as long as we don't create a cycle, the lightest edge will be the minimum weight crossing edge which implies it is in the MST. The Greedy appraoch of choosing the local optimum i.e. the lightest non-cyclic edge in this case yields an efficeint algorithm.
