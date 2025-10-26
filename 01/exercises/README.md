## Section 1.1

### Exercise 1.1-1

Give a real-world example that requires sorting or a real-world example that
requires computing a convex hull.

#### Solution

Cash sorting machines, using a "magic wand" selection tool in a photo editor.

### Exercise 1.1-2

Other than speed, what other measures of efficiency might one use in a
real-world setting?

#### Solution

Computational resource consumption (i.e., memory, disk usage), cost to
implement, ease of use, ease of explanation, simplicity.

### Exercise 1.1-3

Select a data structure that you have seen previously, and discuss its strengths
and limitations.

#### Solution

A linked list. The linked list is useful to create arbitrarily-large sets of
data in a set order without immediately allocating resources for a "maximum"
size. However, the linked list can be improperly linked leading to searching
through an endless loop or risk accessing incorrect or dangerous data.

### Exercise 1.1-4

How are the shortest-path and traveling-salesman problems given above similar?
How are they different?

#### Solution

Both problems involve path-finding and involve finding the least distance
travelled over a given set of coordinates. The difference is that the
traveling-salesman problem require return distance as its final coordinate point
rather than a one-way trip.

### Exercise 1.1-5

Come up with a real-world problem in which only the best solution will do. Then
come up with one in which a solution that is "approximately" the best is good
enough.

#### Solution

Eliminating pests. Getting rid of ninety-nine percent is not good enough if they
can breed back to full destructive capacity.

Harmonically analyzing a piece of Common Practice period music with figured bass
and Roman numerals. There may be multiple ways to interpret the given data, and
therefore an approximately-perfect solution is adequate.

### Exercise 1.1-6

Describe a real-world problem in which sometimes the entire input is available
before you need to solve the problem, but other times the input is not entirely
available in advance and arrives over time.

#### Solution

Spawning players in a multiplayer game. Sometimes all players will be ready and
the match can be made immediately, but sometimes some players are still joining
or the internet has connection issues, and the game cannot start until they've
joined.


## Section 1.2


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
