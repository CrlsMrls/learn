# O-notation

Scientific method.
* Observe some feature of the natural world.
* Hypothesize a model that is consistent with the observations.
* Predict events using the hypothesis.
* Verify the predictions by making further observations.
* Validate by repeating until the hypothesis and observations agree.

## Cost of basic operations
| variable declaration | int a | constant |
| assignment statement | a = b | constant |
| integer compare | a < b | constant |
| array element access | a[i] | constant |
| array length | a.length | constant |
| 1D array allocation | new int[N] | N * constant |
| 2D array allocation | new int[N][N] | N^2 * constant |
| string length | s.length() | constant |
| substring extraction | s.substring(N/2, N) | constant |
| string concatenation | s + t | N * constant |

## Common order-of-growth classifications
| order of growth | name | description | example | 
| 1 | constant | statement | add two numbers | 
| log N | logarithmic | divide in half | binary search| 
| N | linear | loop | find the maximum | 
| N log N | linearithmic | divide and conquer | mergesort | 
| N2 | quadratic |  double loop | check all pairs | 
| N3 | cubic | triple loop | check all triples | 
| 2N | exponential | exhaustive search | check all subsets | 

## Types of running time analyses
* Best case. Lower bound on cost.
** Determined by “easiest” input.
** Provides a goal for all inputs.

* Worst case. Upper bound on cost.
** Determined by “most difficult” input.
** Provides a guarantee for all inputs.

* Average case. Expected cost for random input.
** Need a model for “random” input.
** Provides a way to predict performance.

## Commonly-used notations in academics
* Big Theta (classify): asymptotic order of growth, e.g. Θ(N^2)
* Big Oh (upper bond performance): Θ(N^2) and smaller, e.g. O(N^2)
* Big Omega (lower bounds performance): Θ(N^2) and larger, e.g. Ω(N^2)

In industry's meaning, big O is similar to what academics mean by Theta.

Asymptotic runtime or big O time

## Multi-part algorithms, when to add or multiply?
* if the algorithm is "do this A, when you are done, do that B" the runtimes is `A + B`
* if the algorithm is "do thisA for each time you do that B" the runtime is `A * B`

## Amortized time
how do describe a mixed cost time? e.g. insertion in ArrayList.

Analysis how many times the runtime for each case and aromtize the time

## Log N runtimes
when the number of elements in the problem space gets halved each time or search a binary tree, it will likely be O(log N)
eg. n=16, n=8, n=4, n=2, n=1
what is k in the epression 2^k = N? lg N = k 

## Recursive runtimes
when a recursive function makes **multiple calls**, the urntime will often look like O(branches^depth), where branches is the number of times each recursive call branches

Generally speaking, when you see an algorith with multiple recursive calls, you are looking at exponential runtime.



The sum of 1 through N-1 is (N(N-1))/2
CCI - Example 8, 9, 12, 13 vs 15





