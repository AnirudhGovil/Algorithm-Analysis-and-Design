# Week2

## Master Theorem

The master method is auseful tool for solving recurrence relations of the form T(n) = aT(n/b) + f(n).

n = size of input

a = the contant number of subproblems the recursion splits into

n/b = size of each subproblem

f(n) = cost of the work done outside the recursive call, like the cost of dividing and merging the solutions

f(n) is an asymptotically positive function

According to Master Theorem T(n) has the following asymptotic bounds:

* If f(n) = O(n<sup>log<sub>b</sub>a</sup>), then T(n) = Θ(n<sup>log<sub>b</sub>a</sup>). This means that if the cost of solving the sub-problems at each level increases by a certain factor, the value of f(n) will become overwhelmed by the cost of the last level = n<sup>log<sub>b</sub>a</sup>.
 
* If f(n) = Θ(n<sup>log<sub>b</sub>a</sup>), then T(n) = Θ(n<sup>log<sub>b</sub>a</sup> * log n). This means that if the cost of solving the sub-problem at each level is  equal, then the value of f(n) will be nlogb a meaking the time complexity  f(n) times the number of levels ie.  n<sup>log<sub>b</sub>a</sup> * log n

* If f(n) = Ω(n<sup>log<sub>b</sub>a</sup>), then T(n) = Θ(f(n)). This means that if the cost of solving the subproblems at each level decreases by a certain factor, the value of f(n) will be overwhelmed by the cost of f(n).



## Computing the Fibonacci Series

We aim to check the Correctness of a few algorithms, how much time they will take, and whether we can do any better.

The standard recursive and iterative implementations to calculate the nth Fibonacci number are O(n2) algorithms, even with optimisation techniques like memoisation due to the simple fact that an upto O(n) multiplication must be done upto n-1 times to calculate the nth member of the Fibonacci series.

An alternate approach would be to treat the computation of the next member of the Fibonacci series as a transformation of the form 
![Linear Transformation](Fibonacci_as_a_linear_transformation.jpeg)

The next steps would be to diagonalise the transformation to simplify multiplying it n times.

While addition of integers can be considered to be a constant time operation, the multiplication of large integers still adds O(n) to any algorithm's complexity. Thus we must try to minimise the number of multiplications we have to do.

Here comes the divide and conquer approach of Karatsuba’s Multiplication.

We split each integer into two halves, creating 4 numbers out of the face values digits of the original two integers, and through 3 multiplications, along with addition, subtraction and shifts, we are able to achieve the original result. If we are to carry out this division process recursively, we can fundamentally reduce the complexity from O(n<sup>2</sup>) to O (n<sup>log<sub>2</sub>3</sup>).

Anoter example of this Divide adn Conquer approach can be seen in the Merge Sort Algorithm, where we recursively split the list into 2 halves and sort the halves before merging them back together. Any sorting algorithm involving n numbers has n! permutations. A sorting algorithm would have to make at least log<sub>2</sub>(n!) omparisons in order to sort the list of numbers. If the comparison time is constant, this means any sorting algortihm can be mapped to a binary number of length log<sub>2</sub>(n!). Thus &Omega;(nlogn) is the lower bound on comparison based sorting as it can be broken down to n comparisons at log(n) levels of the decision tree.

## Computing matrix products using Strassesn's Algorithm

Another example of Divide and Conquer is Strassen's algorithm for multiplying matrices. We split the an n x n matrix into 4 smaller matrices of size n/2 x n/2 size. Under the naive aproach to calculating matrix prodeucts, we would then need eight multiplications to reach the answer, giving an O(n<sup>3</sup>) runtime. Strassen's Algorithm reduces this to 7 multiplications per step.

![Strassen's Algorithm](strassen.png)

This reduces the time complexity to O(n<sup>log<sub>2</sub>7</sup>)

## Computing the Median using Divide and Conquer

We can also apply the Divide and Conquer approach to speed up Median Finding. The naive approach would be to sort the list of number using an nlogn algorithm like merge sort and output the middle element however we can achive O(n) time as follows:

* We can divide the elements into groups of 5. 
* Find the median of the n/5 groups. 
* Find the median of the medians of the n/5 groups, let's call it x

Then,

![Median 1](medians1.png)
![Median 2](medians2.png)

Thus at the end of every iteration when split the elments into groups of 5, we can reduce the number of elements by a factor 7/10. Analysis reveals than the recurrence relation T(n) = c([n/5]) + c([7n/10]+6) + an evaluates to O(n).


