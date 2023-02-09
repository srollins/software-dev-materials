Recursion
=========

A *recursive* function is a function defined in terms of itself. The general idea behind recursion is that a problem lends itself to a recursive solution if the problem can be broken down into a smaller version of the same problem. A non-CS example of recursion is the [Matroyshka doll](https://en.wikipedia.org/wiki/Matryoshka_doll). A mathematical example of this is the computation of the factorial of a number. factorial(N) is N*factorial(N-1).

Exercise 1: Implement a function `def factorial(n):` in Python.

Exercise 2: Now, do the same without using a loop.

#### Comparision
1. Some problems are more easily solved recursively.
2. Recursion can be highly inefficient as resources are allocated for each function call.

If you can solve a problem iteratively, you usually should!

### Rules of Recursion

Courtesy of *Data Structures and Algorithms in C++* by Mark Allen Weiss

**The Base Case** - "You must always have some bases cases, which can be solved without recursion." A recursive algorithm must have a base case that has a trivial solution. In the factorial example the factorial of 1 is 1. If you fail to specify a base case you will end up with *infinite recursion*.

A general tail-recursive algorithm is as follows:

```
if(base case)
	apply trivial solution
else
	make recursive call
```

**The Recursive Case** - "For cases that are to be solved recursively, the recursive call must always be to a case that makes progress toward a base case." Consider what would happen if we called recursive factorial by passing in `n` instead of `n-1` on the last line of the function. Because we would not be making progress toward the base case the program would continue calling itself with the same input until we encountered a `RecursionError`. 

**Design Rule** - "Assume that all recursive calls work." This is probably the hardest rule to apply!

**Compound Interest Rule** - "Never duplicate work by solving the same instance of a problem in separate recursive calls." A recursive solution to calculating the nth [Fibonacci](https://en.wikipedia.org/wiki/Fibonacci_number) number would violate this rule!

### Linear Recursion

A linear recursive algorithm contains at most one recursive call at each iteration. Factorial is an example of this. The general algorithm followed by factorial is (1) test for the base case; (2) recurse. Factorial is also an example of tail recursion. In tail recursion, the recursive call is the last operation in the function. Tail recursive functions can easily be converted to iterative algorithms.

Exercise 3: Implement a recursive function that takes as input a str and prints the characters of the str one per line *without using a loop*. 

Exercise 4: Implement a recursive function that takes as input a str and prints the characters of the str *in reverse* one per line *without using a loop*. 

Forward

```
if(base case)
	solve
else
	do task
	recursive call
```

Backward

```
if(base case)
	solve
else
	recursive call
	do task
```


Exercise 5: Implement the following without using a loop.

```python
def print_nums_iterative(n):
	for i in range(1, n+1):
		print(i, end = " ")	
```

Hints:

1. A *helper function* is necessary here.
2. The control variable of the loop becomes the input to the function.
3. The base case is that `start` and `end` are equal.
4. Make sure to increment `start` for each recursive call.

Exercise: Implement a function that returns the number of times the character "a" appears in a str without using a loop. You may not take a slice of the string, and you may only access a single character of the string in any iteration of the function.

### Traversing a File System

A common problem solved using recursion is the traversal of a file system. Recursion is useful in this case because you tyipcally do not know how deep the file system goes. The base case is that you find a single file that you wish to process. The recursive case is that you find a directory. For each file or directory inside of that directory you need to recursively call your function.


### Binary Search

Consider a *sorted* list of numbers. How many operations do you need to perform (i.e., how many times do you need to test an if condition) to determine whether a target value exists in the list?

*Linear search* iterates over the list one item at a time until the target is found or the end of the list is reached. If the list contains N items then the condition may be tested N times in the worst case.

*Binary search* takes advantage of the fact that the list is sorted and cuts the problem size in half each time.

```
if the list has only one element
	if the element matches, return true
	else, return false
if the target is larger than the middle element
	recurse on the list containing all elements to the right of the middle
else 
	recurse on the list containing all elements to the left of the middle
```
It turns out that this reduces the number of comparisons to log(N) in the worst case.
