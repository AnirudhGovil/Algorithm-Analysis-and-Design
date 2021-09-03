# Week2

## Computing the Fibonacci Series

We aim to check the Correctness of a few algorithms, how much time they will take, and whether we can do any better.

The standard recursive and iterative implementations to calculate the nth Fibonacci number are O(n2) algorithms, even with optimisation techniques like memoisation due to the simple fact that an upto O(n) multiplication must be done upto n-1 times to calculate the nth member of the Fibonacci series.

An alternate approach would be to treat the computation of the next member of the Fibonacci series as a transformation of the form 
![Linear Transformation](Linear)

The next steps would be to diagonalise the transformation to simplify multiplying it n times.

While addition of integers can be considered to be a constant time operation, the multiplication of large integers still adds O(n) to any algorithm's complexity. Thus we must try to minimise the number of multiplications we have to do.

Here comes the divide and conquer approach of Karatsuba’s Multiplication.

We split each integer into two halves, creating 4 numbers out of the face values digits of the original two integers, and through 3 multiplications, along with addition, subtraction and shifts, we are able to achieve the original result. If we are to carry out this division process recursively, we can fundamentally reduce the complexity from O(n<sup>2</sup>) to O (n<sup>log<sub>2</sub>3</sup>).

