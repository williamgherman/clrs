<!---
N.B: This file is formatted for displays larger than 80 columns (163 cols) to
properly format the Markdown table.
-->

# Exercises

## Section 1.1

### 1.1-1

> Give a real-world example that requires sorting or a real-world example that
> requires computing a convex hull.

Cash sorting machines, using a "magic wand" selection tool in a photo editor.

### 1.1-2

> Other than speed, what other measures of efficiency might one use in a
> real-world setting?

Computational resource consumption (i.e., memory, disk usage), cost to
implement, ease of use, ease of explanation, simplicity.

### 1.1-3

> Select a data structure that you have seen previously, and discuss its strengths
> and limitations.

A linked list. The linked list is useful to create arbitrarily-large sets of
data in a set order without immediately allocating resources for a "maximum"
size. However, the linked list can be improperly linked leading to searching
through an endless loop or risk accessing incorrect or dangerous data.

### 1.1-4

> How are the shortest-path and traveling-salesman problems given above similar?
> How are they different?

Both problems involve path-finding and involve finding the least distance
travelled over a given set of coordinates. The difference is that the
traveling-salesman problem require return distance as its final coordinate point
rather than a one-way trip.

### 1.1-5

> Come up with a real-world problem in which only the best solution will do. Then
> come up with one in which a solution that is "approximately" the best is good
> enough.

Eliminating pests. Getting rid of ninety-nine percent is not good enough if they
can breed back to full destructive capacity.

Harmonically analyzing a piece of Common Practice period music with figured bass
and Roman numerals. There may be multiple ways to interpret the given data, and
therefore an approximately-perfect solution is adequate.

### 1.1-6

> Describe a real-world problem in which sometimes the entire input is available
> before you need to solve the problem, but other times the input is not entirely
> available in advance and arrives over time.

Spawning players in a multiplayer game. Sometimes all players will be ready and
the match can be made immediately, but sometimes some players are still joining
or the internet has connection issues, and the game cannot start until they've
joined.

## Section 1.2

### 1.2-1

> Give an example of an application that requires algorithmic content at the
> application level, and discuss the function of the algorithms involved.

Any sort of matchmaking or dating application requiring the user's data to have
some relation to each other, like location, interests or biographical keywords.

### 1.2-2

> Suppose we are comparing implementations of insertion sort and merge sort on
> the same machine. For inputs of size $n$, insertion sort runs in $8n^2$
> steps, while merge sort runs in $64n\lg n$ steps. For which values of $n$
> does insertion sort beat merge sort?

When the two functions are graphed, their equations meet at around 1 and 43.
Therefore, insertion sort beats merge sort for inputs of size 43 or fewer.

### 1.2-3

> What is the smallest value of $n$ such that an algorithm whose running time is
> $100n^2$ runs faster than an algorithm whose running time is $2^n$ on the same
> machine?


The smallest positive integer value solution to the inequality $100n^2 < 2^n$
is 15, which is therefore the smallest value of $n$ that would run faster on
the $100n^2$ algorithm.

# Problems

## Problem 1-1: Comparison of running times

> For each function $f(n)$ and time $t$ in the following table, determine the
> largest size $n$ of a problem that can be solved in time $t$, assuming that the
> algorithm to solve the problem takes $f(n)$ microseconds.


|          |1 second  |1 minute           |1 hour                |1 day                    |1 month                   |1 year                    |1 century                 |
|:--------:|---------:|------------------:|---------------------:|------------------------:|-------------------------:|-------------------------:|-------------------------:|
|$\lg n$   |$2^{10^6}$|$2^{6 \times 10^7}$|$2^{3.6\times 10^8}$  |$2^{8.64 \times 10^{10}}$|$2^{2.592 \times 10^{12}}$|$2^{3.153 \times 10^{13}}$|$2^{3.155 \times 10^{15}}$|
|$\sqrt{n}$|$10^12$   |$3.6 \times 10^15$ |$1.296 \times 10^{19}$|$7.464 \times 10^{21}$   |$6.718 \times 10^{24}$    |$9.945 \times 10^{26}$    |$9.958 \times 10^{30}$    |
|$n$       |$10^6$    |$6 \times 10^7$    |$3.6 \times 10^9$     |$8.64 \times 10^{10}$    |$2.592 \times 10^{12}$    |$3.153 \times 10^{13}$    |$3.155 \times 10^{15}$    |
|$n\lg n$  |$62746$   |$2801417$          |$133378058$           |$2755147513$             |$71870856404$             |$797633893349$            |$68654697441062$          |
|$n^2$     |$1000$    |$7745$             |$60000$               |$293938$                 |$1609968$                 |$5615692$                 |$56175382$                |
|$n^3$     |$100$     |$391$              |$1532$                |$4420$                   |$13736$                   |$31593$                   |$146677$                  |
|$2^n$     |$19$      |$25$               |$31$                  |$36$                     |$41$                      |$44$                      |$51$                      |
|$n!$      |$9$       |$11$               |$12$                  |$13$                     |$15$                      |$16$                      |$17$                      |
