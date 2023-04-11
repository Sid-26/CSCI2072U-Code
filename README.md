# 2072U-Course-Codes
# Table of Contents
1. **[Lecture 2](#lecture-2)**
   - [Bisection](#bisection)
2. **[Lecture 3/4](#lecture-3--4)**
   - [Newton Raphson Theorum](#newton-raphson-theorum)
   - [Secant Method](#secant-method)

3. **[Lecture 5](#lecture-5)**
   - LU Decomposition
4. **[Lecture 6 / 7](#lecture-6--7)**
   - [LUP Decomposition](#lup-decomposition)
5. **[Lecture 7](#lecture-7)**
   - Vector Norms
6. **[Lecture 8](#lecture-8)**
   - Computational Complexity
   - Flops
5. **[Lecture 9](#lecture-9)**
   - Big O
   - Flop Calculation
6. **[Lecture 11](#lecture-11)**
7. **[Lecture 13](#lecture-13)**
8. **[Lecture 16](#lecture-16)**

   
This repository contains final versions of codes we've written during class, as well as other relevant codes.
## Lecture [2](https://learn.ontariotechu.ca/courses/21707/files/2796036?module_item_id=499488)
### [Bisection](https://github.com/royce-mathew/CSCI2072U-Code/blob/main/bisection_code.py)
#### Pseudocode - Page 33
#### Remarks
- Upper bound for eror: $x^{(k)} −x^∗| ≤ \epsilon^{(k)} = |b^{(k)} −a^{(k)}|$
- Error on kth iteration: $\epsilon^{(k)} = \frac{\epsilon^{(0)}}{2^k}$
- Linear Convergence.
- Straight line on a semilog plot
- Works only for one unknown
<br/><br/>

#### Questions
1. **Under what conditions does the algorithm converge?**
- Bisection converges to some $x^∗$ such that $$f(x^*) = 0, x^\* \in [a, b]$$
if f is continuous and f (a)f (b) < 0. If there are two or more solutions, we don’t know to which one it will converge to.
2. **How accurate will the result be?**
- Gives us $x^*$ up to machine precision.
3. **How fast does it converge?**
- The error $|x^* − x(k)|$ decreases by a factor of $\frac{1}{2}$ in each iteration.

## Lecture [3](https://learn.ontariotechu.ca/courses/21707/files/2809429?module_item_id=501240) / [4](https://learn.ontariotechu.ca/courses/21707/files/2817747?module_item_id=502691)
### Notes / topics covered
- Intermediate Value Theorum
- Lecture 4 shows the comparisons between Bisection and Newton / Secant methods
### [Newton Raphson Theorum](https://github.com/royce-mathew/CSCI2072U-Code/blob/main/NetwonRaphson_plot.py)
Pseudocode - Page 22

#### Remarks
- The newton raphson methods needs the derivative to function correctly. When you don't have derivative or can't calculate, look at secant or bisection.
- Need one/two initial guesses.
- Error Estimate: $\epsilon^{(k+1)} \approx (\epsilon^{(k)})^2$
- Quadratic Convergence
- Steeper than linear on semilog plot.
<br/><br/>

#### Questions
1. **Under what conditions does the algorithm converge?**
- Newton-Raphson iteration converges if $x_0$ is sufficiently close to
$x^∗$. Usually, we do not know a priori how close is close enough and must resort to trial and error. 
2. **How accurate will the result be?**
- Gives us $x^*$ up to machine precision.
3. **How fast does it converge?**
- In Newton-Raphson iterations, the error is approximately squared in each iteration (provided it is small enough!). $$\epsilon_0, \epsilon_0^2, \epsilon_0^4, \epsilon_0^8, ...$$

### [Secant Method](https://github.com/royce-mathew/CSCI2072U-Code/blob/main/Assignment3_Solutions/Secant.py)
Secant methods needs two initial guesses: $x_{(0)}$ and $x_{(1)}$
#### Remarks
- This method uses a `finite difference` approximation to $f′$.
- Need one/two initial guesses.
- Asymptotically (meaning if $|x_k − x^*|$ is small enough) the secant method converges as fast as Newton-Raphson method does.
- The secant method has extensions to problems with more than 1 unknown, but in this case Newton method tends to be less cumbersome.
- The secant method is a `second order recurrence relation`. It relates the next approximation to the two previous approximations
- If we can find an $a$ and $b$ such that $x^∗ \in [a, b]$, then $x_0 = a$ and $x_1 = b$ is a good starting point.
- Error Estimate: $\epsilon^{(k+1)} \approx (\epsilon^{(k)})^2$


## Lecture [5](https://learn.ontariotechu.ca/courses/21707/files/2839238?module_item_id=504808)
### Notes
- In general, to solve and find isolated solutions we need the same number of equations as unknowns. 
- Zero Matrices: Matrices that have all values set to 0
- Identity Matrices: Matrices that have the diagonal from $(1, 1)$ to $(n, n)$ as 1s and other values as 0s; 
- Coordinate Vectors: All 0s except one 1. 
- $k^{th}$ Coordinate Vectors: $k^{th}$ Column of $I$
- Matrix Properties - Page 18
- Nonsingular Matrix Properties - Page 19
- Never solve linear systems by computing $A^{−1}$ and $x = A^{−1}b$!
- `scipy.linalg.solve` - Solution of $Ax = b$
   - Gaussian Elimination - Page 32
      - Converting square matrix to triangular form
      - **Pivot element** on diagonal used to zero out entries
      - Multiplier for eliminating $A_{k, l}$ with pivot element $A_{k,k}$ is
      - Gaussian elimination is `equivalent` to finding L & U such that
      - Flops: $\frac{2}{3}n^3 + \frac{1}{2}n^2 - \frac{7}{6}n$
   - LU Decomposition
      - Pseudocode - Page 70
      - Flops: $\frac{2}{3}n^3 + \frac{1}{2}n^2 - \frac{7}{6}n$
   - Not every invertible matrix A has LU decomposition A = LU

## Lecture [6](https://learn.ontariotechu.ca/courses/21707/files/2837955?module_item_id=504697) / [7](https://learn.ontariotechu.ca/courses/21707/files/2890877?module_item_id=508963)
### [LUP Decomposition](https://github.com/royce-mathew/CSCI2072U-Code/blob/main/LUP_linalg_implement.py)
Pseudocode - Page 18
- L: Lower Triangle Matrix
- U: Upper Triangle Matrix
- P: Permutation matrix; A permutation matrix is any matrix obtained from interchanging the rows or columns of the identity matrix.

#### Questions
1. **Under what conditions does the algorithm converge?**
- The $A = LU$ decomposition works if and only if all leading principal submatrices of $A$ (i.e. $A(1 : k, 1 : k) for k ≤ n)$ are nonsingular. **Not recommended for linear solving!**
- The PA = LU decomposition works if A is nonsingular. This is the default method for linear solving:
   - step 1: solve Ly = Pb using forward substitution
   - step 2: solve Ux = y using backward substitution
2. **How accurate will the result be?**
- $‖x − x_{∗}‖$ small means $x_{*} ∈ \mathbb{R}^n$ approximates $x ∈ \mathbb{R}^n$ well.
- Define *relative error of x∗ as an approximation of x*:
   -  Relative error of $x_∗$ in norm $‖ · ‖ := ‖x − x_∗‖ ‖x‖$ (assuming $x \neq 0$)
- Computing (relative) error requires choosing a norm.
- Norm-wise errors can hide component-wise errors in vectors.

3. **How fast does it converge?**
- In Newton-Raphson iterations, the error is approximately squared in each iteration (provided it is small enough!). $$\epsilon_0, \epsilon_0^2, \epsilon_0^4, \epsilon_0^8, ...$$

### Notes
- It is not always possible to find $A = LU$ for A nonsingular
- When A nonsingular, *always* possible to find permutation $P$ such that $PA = LU$, i.e., so that $PA$ has an $LU$ decomposition, also called a Gauss factorisation.
- **Pivoting:** Using permutations of the rows and/or columns of a matrix to change a pivot element
- **Partial pivoting**: interchanging rows (not columns) to use small multipliers.
- Partial pivoting: multipliers $L_{k, l}$ satisfy $|L_{k, l}| ≤ 1$.
- $PA = LU$ decomposition is the default way to solve linear systems.

#### [Condition Number](https://github.com/royce-mathew/CSCI2072U-Code/blob/main/Assignment3_Solutions/CondNumFuncA3.py)
- The **condition number** of a matrix is defined as the quotient of its largest to its smallest singular values. (Page 39)
- The condition number $K(A)$ is an indicator of whether a system of linear equations $Ax = b$ is “good” or “bad”
- If $K(A)$ is small ($<= 1$), it’s “good”: we call it well-conditioned
- If $K(A)$ is large ($>1$), it’s “bad”: we call it ill-conditioned

#### [Vandermonte Matrix](https://github.com/royce-mathew/CSCI2072U-Code/blob/main/Accuracy_LinSys.py)
- Full Definition (Page 45)

## Lecture [7](https://learn.ontariotechu.ca/courses/21707/files/2890877?module_item_id=508963)
### Notes
- Vector norms - quantify lengths of / distances between vectors;
   - Euclidean norm or 2-norm
      - `scipy.linalg.norm(x,2)`
   - Manhattan norm or 1-norm 
      - `scipy.linalg.norm(x,scipy.inf)`
   - max/infinity/Chebyschev norm
- Error and Residual (Page 29)


## Lecture [8](https://learn.ontariotechu.ca/courses/21707/files/2890876?module_item_id=508962)
### Computational Complexity
Computational Complexity is the amount of work required to execute/carry out algorithm from start to finish.
#### Counting Flops
1. Write pseudocode of algorithm clearly.
2. In each line, count number of flops ( $+$ , $−$ , $×$ , $÷$ ).
3. Count number of times each line executes (e.g., in a for loop).
4. Multiply cost of each line by number of times it executes
#### Remarks
- Assume all floating-point operations have equal cost
- Ignore memory access or overwriting in computing cost
- Precise definitions of flops vary in distinct texts/papers
- Count special function evaluations (e.g., sqrt, etc.) as needed
- Count special function evaluations (e.g., sqrt, etc.) as needed

## Lecture [9](https://learn.ontariotechu.ca/courses/21707/files/2890875?module_item_id=508961)
Computational Complexity of LU Decomposition and Gaussian Elimination.
### Big O Notation
### Computing Solution of $Ux = c$ by back substitution
- Flops: $n^2$
### Horner Algorithm
- Flops: $2n$
- Page 61

The total cost of solving a linear system with Gaussian elimination is $$\frac{2}{3}n^2 + \frac{3}{2}n - \frac{7}{6}n$$
With LU Decomposition: $$\frac{2}{3}n^3 + \frac{5}{2}n^2 - \frac{7}{6}n$$
The cost of evaluating a polynomial of order $n$ is $2n$ – when done in the right way.
A simple re-ordering can reduce the complexity drastically!

## Lecture [11](https://learn.ontariotechu.ca/courses/21707/files/2897480?module_item_id=509266)
### Notes
- Used to find the solution for non-linear systems of equations
- Algorithm for Implementing NewtonSystem - Slide 6
- Branching statements ($if$ or $case$) can require extra care
- Complexity analysis possible for memory/storage, etc.
- Complexity analysis of recursively defined functions yields recurrence relations to solve


## Lecture [13](https://learn.ontariotechu.ca/courses/21707/files/2931521?module_item_id=511258)
### Remarks
- $\tilde{f}$ us called an interpolating function or interpolant
- $x_k$ are interpolatng points or nodes or abscissa
- $\tilde{f}$ provides value for points in between the nodes $x_k$
- Desirable to have smooth $\tilde{f}$, differentiable, easy to compute

### Notes
- There are a few types of interpolating functions:
   - Linear
   - Polynomial
   - Trignometric
   - Rational
- Polynomial interpolants - Slide 8/9
- Polynomial Interpolation Theorem (Existence/Uniqueness of Polynomial Interpolation): If all the interpolation nodes are distinct the interpolant exists. If we select the polynomial interpolant of the lowest possible order, it is unique.
- Vandermonde System, in matrix form, is defined as $Va = y$ where - Slide 12
- Polynomial coefficients are $a = V^{-1}y$ for an invertible Vandermonder matrix

## Lecture [16](https://learn.ontariotechu.ca/courses/21707/files/2991356?module_item_id=514972)
### Notes
- The error of polynomial interpolation is $|E_n(x)| = |f(x) - Π_n(x)|$ where `Π` is the unique polynomial interpolation of degree at most n.
- The upper bound (maximum error) of polynomial interpolation error - Slide 5 to 8
- Conclusions we can draw from the error formula:
   - Functions with small higher derivates are well-approximated by interpolating polynomials (such functions are smooth).
   - We can choose the location of the interpolating nodes to minimize the error. Equidistant nodes are bad but nodes near the boundaries are good.
   - Extrapolation is far more dangerous than interpolation. Upper bound for the error of extrapolation grows without bound.
- With a ***Newton Polynomial Basis***, the resulting system of linear equations for the coefficients is $Ma=y$ where $M$ is now triangular and depends on the interpolation points of $x_k$ - Slide 12/13
- Computational Complexity:
   - **Monomial Basis**: cost of building matrix is $O(n^2)$, cost of solving the system is $O(n^2)$
   - **Newton Polynomial Basis**: cost of building matrix; takes fewer but is still $O(n^2)$, cost of solving triangular system is $O(n^2)$; since it only requires forward substitution.
- Condition Number: The condition number of triangular matrix resulting from Newton Polynomial Basis is mich smaller than Vandermonde matrix, meaning Newton Polynomial Basis leads to more accurate results.
- Taylor's Theorem - Slide 15/21


## Lecture 18
### Notes
- The piecewise linear interpolant is **not differentiable**.
- Cubic Splines - Slide 9


### Lecture 19
### Notes
- Interpolation is useful for approximating smooth functions (hard to evaluate functions)
- Existence of the interpolant is guaranteed.
- There is an explicit upper bound for the interpolation error.
- Forcing the interpolant to go through noisy data gives strange results.
- The least squares solution is a low-order polynomial that could try to find a way to interpolate the noisy data.
   - The set of equations for this approximant will be over-determined; generically, the approximant cannot satisfy all conditions.
   - We can only find an *approximate* solution to these equations
- An overdetermined system of linear equations can be written as A**x** = **b** where A is "tall and thin", b is the RHS vector, and there are more equations than       unknowns.
- When solving A**y** = **b**, the residual of **y** is **r(y) = b**-A**y** where residual can be defined as the amount by which y fails to satisfy the system A**x** = **b**.
- **norms** are used to quantify the **size** of vectors.
- To solve an overdetermined system - Slide 9
   - Generically, no solution exists for overdetermined systems.
   - Goal: find vector $**x**^{\*} \in \mathbb{R}^{M}$ that ***minimizes size of residual $r(x^{\*}.***
   - To minimise $r(x^{\*})$, measure size with some norm... - Slide 9
   - $x^{\*}$ is a minimiser of ||r(x)|| in that norm... - Slide 9
- Least-squares approximation & normal equations
   - `scipy.linalg.lstsq(A,b)` computes least-squares approximations of overdetermined systems (only works tall/thin systems). This also computes the mean-square             residual (res), the rank of A (rnk) and the singular values of A (s)
      - ```A = numpy.array([[1.0,-2.0],[1.0,-1.0],[1.0,1.0]])
           b = numpy.array([0.5,1.0,-1.0])
           xstar, res, rnk, s = scipy.linalg.lstsqr(A,b)```
