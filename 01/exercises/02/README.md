### Exercise 1.2-1

Give an example of an application that requires algorithmic content at the
application level, and discuss the function of the algorithms involved.

### Solution

Any sort of matchmaking or dating application requiring the user's data to have
some relation to each other, like location, interests or biographical keywords.

### Exercise 1.2-2

Suppose we are comparing implementations of insertion sort and merge sort on the
same machine. For inputs of size *n*, insertion sort runs in 8*n*<sup>2</sup>
steps, while merge sort runs in 64*n*&nbsp;lg&nbsp;*n* steps. For which values
of *n* does insertion sort beat merge sort?

### Solution

When the two functions are graphed, their equations meet at around 1 and 43.
Therefore, insertion sort beats merge sort for inputs of size 43 or fewer.

### Exercise 1.2-3

What is the smallest value of *n* such that an algorithm whose running time is
100*n*<sup>2</sup> runs faster than an algorithm whose running time is
2<sup>*n*</sup> on the same machine?

### Solution

The smallest positive integer value solution to the inequality
100*n*<sup>2</sup> < 2<sup>*n*</sup> is 15, which is therefore the smallest
value of *n* that would run faster on the 100*n*<sup>2</sup> algorithm.
