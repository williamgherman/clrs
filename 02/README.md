# Exercises

## Section 2.1

### 2.1-1


> Using Figure 2.2 as a model, illustrate the operation of
> $\text{Insertion-Sort}$ on an array initially containing the sequence
> $\langle 31, 41, 59, 26, 41, 58 \rangle$.


```
[31, 41, 59, 26, 41, 58]
      *

[31, 41, 59, 26, 41, 58]
          *

[31, 41, 59, 26, 41, 58]
^ --> --> --> |
|             |
+-------------+

[26, 31, 41, 59, 41, 58]
        ^ --> --> |
        |         |
        +---------+

[26, 31, 41, 41, 59, 58]
                ^ --> |
                |     |
                +-----+

[26, 31, 41, 41, 58, 59]
```

### 2.1-2

> Consider the procedure $\text{Sum-Array}$ on the facing page. It computes the
> sum of the $n$ numbers in array $A[1:n]$. State a loop invariant for this
> procedure, and use its initialization, maintenance, and termination properties
> to show that the $\text{Sum-Array}$ procedure returns the sum of the numbers in
> $A[1:n]$.
>
> ### $\text{Sum-Array}(A, n)$
>
> ```
> 1   sum = 0
> 2   for i = 1 to n
> 3       sum = sum + A[i]
> 4   return sum
> ```

Loop invariant: At the start of the **for** loop on line 2, `sum` is the
correct sum of $A[1:i]$

Initialization: Prior to the first iteration, there are no elements in the
sequence, and the sum is correctly zero.

Maintenance: Each iteration adds the value $A[i]$ to the `sum`, which means
that the `sum` still correctly reflects $A[1:i]$.

Termination: The loop variable *i* terminates after all values 1 to $n$ are
exhausted. Once $i=n+1$, sum will correctly equal the sum of all values
in $A[1:n]$, which means our algorithm is correct.

### 2.1-3

> Rewrite the $\text{Insertion-Sort}$ procedure to sort into monotonically
> decreasing instead of monotonically increasing order.

### $\text{Insertion-Sort}(A, n)$

```
1   for i = 2 to n
2       key = A[i]
3       // insert A[i] into sorted subarray A[1:i-1]
4       j = i - 1
5       while j > 0 and A[j] < key
6           A[j + 1] A[j]
7           j = j - 1
8       A[j + 1] = key
```

### 2.1-4

> Consider the *searching problem*:
>
> **Input:** A sequence of $n$ numbers $\langle a_1, a_2, \dots, a_n \rangle$
> stored in array $A[1:n]$ and a value $x$.
>
> **Output:** An index $i$ such that $x$ equals $A[i]$ or the special value
> $\text{NIL}$ of $x$ does not appear in $A$.
>
> Write pseudocode for *linear search*, which scans through the array from
> beginning to end, looking for $x$. Using a loop invariant, prove that your
> algorithm is correct. Make sure that your loop invariant fulfills the three
> necessary properties.

### $\text{Linear-Search}(A[n], x)$

```
1   for i = 1 to n
2       if A[i] == x
3           return i
4   return NIL
```

Loop invariant: At the start of each iteration of the **for** loop, the
subarray $A[1:i-1]$ do not contain the value $x$.

Initialization: Prior to the first iteration, the subarray is empty and
therefore cannot contain the value $x$.

Maintenance: Each iteration tests if $A[i]$ is the value $x$, which still means
that $A[1:i-1]$ cannot contain $x$.

Termination. The loop terminates when $A[i] = x$, in which case the subarray
$A[1:i-1]$ will still never actually include $A[i]$, i.e., $x$. Therefore, the
algorithm is correct.

### 2.1-5

> Consider the problem of adding two $n$-bit binary integers $a$ and $b$,
> stored in two $n$-element arrays $A[0:n-1]$ and $B[0:n-1]$, where each
> element is either 0 or 1, $a = \sum_{i=0}^{n-1} A[i] \cdot 2^{i}$, and $b =
> \sum_{i=0}^{n-1} B[i] \cdot 2^{i}$. The sum $c = a + b$ of the two integers
> should  be stored in binary form in an $(n + 1)$-element array $C[0:n]$,
> where $c = \sum_{i=0}^{n} C[i] \cdot 2^{i}$. Write a procedure
> $\text{Add-Binary-Integers}$ that takes as input arrays $A$ and $B$, along
> with the length $n$, and returns array $C$ holding the sum.

### $\text{Add-Binary-Integers}(A, B, n)$

```cpp
carry = 0
for i = 0 to n-1
    if A[i] + B[i] == 2
        carry = 1
        C[i] = 1
    else
        C[i] = A[i] + B[i]
        carry = 0
C[n+1] = carry
return C
```

## Section 2.2

### 2.2-1

> Express the function $n^3/1000 + 100n^2 - 100n + 3$ in terms of
> $\Theta$-notation.

$\Theta(n^3)$

### 2.2-2

> Consider sorting $n$ numbers stored in array $A[1:n]$ by first finding the
> smallest element of $A[1:n]$ and exchanging it with the element in $A[1]$.
> Then find the smallest element of $A[2:n]$, and exchange it with $A[2]$. Then
> find the smallest element of $A[3:n]$, and exchange it with $A[3]$. Continue
> in this manner for the first $n - 1$ elements of $A$. Write pseudocode for
> this algorithm, which is known as *selection sort*. What loop invariant does
> this algorithm maintain? Why does it need to run for only the first $n - 1$
> elements, rather than for all $n$ elements? Give the worst-case running time
> of selection sort in $\Theta$-notation. Is the best-case running time any
> better?

### $\text{Selection-Sort}(A, n)$

```cpp
for i = 1 to n - 1
    current = A[i]
    smallest_index = i
    for j = i + 1 to n - 1
        if A[j] < A[smallest_index]
            smallest_index = j
    A[i] = A[smallest_index]
    A[smallest_index] = current
```

Loop-invariant: The subarray $A[1:i-1]$ always contains the sorted minimum values
of $A$. The final value does not need to be sorted, because there is no other
element it can be exchanged with: it is already in the correctly-sorted
position. In the worst case, this algorithm runs at $\Theta(n^3)$ time, and in
the best-case scenario (all items are already sorted), the algorithm still
needs to check every single value in the array, so it is still $\Theta(n^3)$
time.

### 2.2-3

> Consider linear search again (see Exercise 2.1-4). How many elements of the
> input array need to be checked on the average, assuming that the element being
> searched for is equally likely to be any element in the array? How about in the
> worst case? Using $\Theta$-notation, give the average-case and worst-case
> running times of linear search. Justify your answers.

If the average use of linear search is in the middle, it would take $n/2$
elements to find the correct element. In the worst case, it would take $n$
elements, as it would be in the end. Because the difference is just from a
constant $(1/2)$, both $\Theta$-notation running times would be linear,
$\Theta(n)$.

### 2.2-4

> How can you modify any sorting algorithm to have a good best-case running
> time?

Ensure there is a base-case so that the best-case returns in a constant time.

## Section 2.3

### 2.3-1

> Using Figure 2.4 as a model, illustrate the operation of merge sort on an
> array initially containing the sequence $\langle 3, 41, 52, 26, 38, 57, 9, 49
> \rangle$.

```
            [3, 41, 52, 26, 38, 57, 9, 49]
divide   [3, 41, 52, 26]          [38, 57, 9, 49]
divide  [3, 41]   [52, 26]     [38, 57]     [9, 49]
divide [3]  [41] [52]  [26]  [38]   [57]   [9]   [49]
merge   [3, 41]   [26, 52]     [38, 57]     [9, 49]
merge    [3, 26, 41, 52]          [9, 38, 49, 57]
merge        [3, 9, 26, 38, 41, 49, 52, 57]
```

### 2.3-2

> The test in line 1 of the $\text{Merge-Sort}$ procedure reads "**if** $p \ge
> r$" rather than "**if** $p \ne r$." If $\text{Merge-Sort}$ is called with
> $p>r$, then the subarray $A[p:r]$ is empty. Argue that as long as the initial
> call of $\text{Merge-Sort}(A, 1, n)$ has $n \ge 1$, the test "**if** $p \ne
> r$" suffices to ensure that no recursive call has $p > r$.

> [!IMPORTANT]
> This problem wording is in error, it should read "**if** $p = r$" for all
> cases of "**if** $p \ne r$. Otherwise, $\text{Merge-Sort}(A, 1, 1)$ would end
> up successfully running and call $\text{Merge-Sort}(A, 2, 1)$.


If $\text{Merge-Sort}(A, 1, n)$ is called, given $n \ge 1$: in the edge case
$\text{Merge-Sort}(A, 1, 1)$, it successfully halts and returns. Otherwise, it
will always result in a call of $\text{Merge-Sort}$ where $p = r$ and halts.

### 2.3-3

> State a loop invariant for the **while** loop of lines 12-18 of the
> $\text{Merge}$ procedure. Show how to use it, along with the **while** loops
> of lines 20-23 and 24-27, to prove that the $\text{Merge}$ procedure is
> correct.

The **while** loop is valid when the following loop invariant is true: the
subarray of $A[p:k-1]$ contains the smallest values in $L$ and $R$ up to their
$i$ and $j$ numbered elements, respectively, all in sorted order.

Initialization: $k = p$, so $A[p:k-1]$ is empty, still fullfilling the loop
invariant.

Maintenance: during each call, $A[k]$ is assigned the smallest value of either
$L[i]$ or $R[j]$, whose counters are incremented. The invariant remains valid.

Termination: After the **while** loop, either $L$ or $R$ is entirely used, but
$k$ has still increased, but since the invariant counts to $k-1$, the invariant
remains valid.

Afterwards, the two additional **while** loops are run, adding the last few
elements of $L$ or $R$ into $A$, but each time, the smallest element of the
relevant array is copied in, and $i$ or $j$ is increased alongside $k$. By the
end, all values are correctly copied to $A$ in sorted order up to the length of
$R$ and $L$ ($n_L$ and $n_R$).

### 2.3-4

> Use mathematical induction to show that when $n \ge 2$ is an exact power of 2,
> the solution of the recurrence
>
> $$
> T(n) =
> \begin{cases}
> 2 & \text{if} n = 2 \\
> 2T(n/2) + n & \text{if} n > 2
> \end{cases}
> $$
>
> is $T(n) = n \lg n$.

Base case: $n = 2$, $2 = 2 \lg 2$ is true. If we assume $T(n) = n \lg n$ is
true, and assuming that $T(2^k)$ is true, then the inductive case $T(2^{k+1})$ is:

$$
\begin{align}
2T(2^k/2) + 2^k &= 2^k \lg 2^k \\
2T(2^{k+1}/2) + 2^{k+1} &= 2^{k+1} \lg 2^{k+1} \\
2T(2^k) + 2^{k+1} &= 2^{k+1}(k+1) \\
2(2^k \lg 2^k) + 2^{k+1} &= 2^{k+1}(k+1) \\
2^{k+1}k + 2^{k+1} &= 2^{k+1}(k+1) \\
2^{k+1}(k + 1) &= 2^{k+1}(k+1)
\end{align}
$$

Therefore, all values of $n = 2^k$ (i.e., all powers of two) allow the solution
$n \lg n$ to be true for $T(n)$.

### 2.3-5

> You can also think of insertion sort as a recursive algorithm. In order to
> sort $A[1:n]$, recursively sort the subarray $A[1:n-1]$ and
> then insert $A[n]$ into the sorted subarray $A[1:n - 1]$. Write
> pseudocode for this recursive version of insertion sort. Give a recurrence
> for its worst-case running time.

### $\text{Insertion-Sort}(A, n)$:

```cpp
if n == 1
    return A[n]
j = n - 1
INSERTION_SORT(A, j)
key = A[n]
while j > 0 and A[j] > key
    A[j+1] = A[j]
    j = j - 1
A[j+1] = key
```

In the worst case, in which the values are reverse-sorted, we get the
recurrence:

$$
T(n) =
\begin{cases}
\Theta(1) & \text{if} n = 1 \\
T(n-1) + \Theta(n) & \text{if} n > 1
\end{cases}
$$

### 2.3-6

> Referring back to the searching problem (see Exercise 2.1-4), observe that if
> the subarray being searched is already sorted, the searching algorithm can
> check the midpoint of the subarray against $v$ and elimate half of the
> subarray from further consideration. The *binary search* algorithm repeats
> this procedure, halving the size of the remaining portion of the subarray
> each time. Write pseudocode, either iterative or recursive, for binary
> search. Argue that the worst-case running time of binary search is
> $\Theta(\lg n)$.

> [!IMPORTANT]
> Slight correction in the problem, it should refer to $x$, not $v$ for the
> searched value.

### $\text{Binary-Search}(A, x, begin, end)$:

```cpp
if begin > end
    return NIL
midway = floor((begin + end)/2)
if A[midway] == x
    return midway
else if A[midway+1] > x
    return BINARY_SEARCH(A[begin:midway-1], x)
else
    return BINARY_SEARCH(A[midway+1:end], x)
```

Because the algorithm removes half of the elements in each iteration, we end up
with $T(n) = T(n/2) + \Theta(1)$ which is $\Theta(\lg n)$.

### 2.3-7

> The **while** loop of lines 5-7 of the $\text{Insertion-Sort}$ procedure in
> Section 2.1 uses a linear search to scan (backward) through the sorted
> subarray $A[1:j - 1]$. What if insertion sort used a binary search
> (see Exercise 2.3-6) instead of a linear search? Would that improve the
> overall worst-case running time of insertion sort to $\Theta(n \lg n)$?

Although the search would be improved to half of the operations in the worst
case, the algorithm also moves every element individually to the right which
still must be done with this improved algorithm. Therefore, this improvement
would not reduce the running time to $\Theta(n \lg n)$.

### 2.3-8

> Describe an algorithm that, given a set $S$ of $n$ integers and another
> integer $x$, determines whether $S$ contains two elements that sum to exactly
> $x$. Your algorithm should take $\Theta(n \lg n)$ time in the worst case.

> [!NOTE]
> Since $S$ is a mathematical set, each integer within only appears exactly
> once. Therefore, $x/2$ if within the set cannot be a solution to the problem.

This algorithm must first sort the elements in $S$ and then perform a search
for each element's compliment $j = x - i$. If $i$ and $j$ exist, then that is
the solution. In the worst case, $T(n) = \Theta(n \lg n)$ time since there
would be $n$ iterations of binary search ( $\Theta(\lg n)$ ).

# Problems

## Problem 2-1: Insertion sort on small arrays in merge sort

> Although merge sort runs in $\Theta(n \lg n)$ worst-case time and insertion
> sort runs in $\Theta(n^2)$ worst-case time, the constant factors in insertion
> sort can make it faster in practice for small problem sizes on many machines.
> Thus it makes sense to *coarsen* the leaves of the recursion by using
> insertion sort within merge sort when subproblems become sufficiently small.
> Consider a modification to merge sort in which $n/k$ sublists of length $k$
> are sorted using insertion sort and then merged using the standard merging
> mechanism, where $k$ is a value to be determined.
>
> ***a.*** Show that insertion sort can sort the $n/k$ sublists, each of length $k$
> in $\Theta(nk)$ worst-case time.
>
> ***b.*** Show how to merge the sublists in $\Theta(n \lg (n / k))$ worst-case
> time.
>
> ***c.*** Given that the modified algorithm runs in $\Theta(nk + n \lg(n/k))$
> worst-case time, what is the largest value of $k$ as a function of $n$ for
> which the modified algorithm has the same running time as standard merge
> sort, in terms of $\Theta$-notation?
>
> ***d.*** How should you choose $k$ in practice?

### a.

Insertion sort runs in quadratic time, $\Theta(k^2)$ in the worst case. But
since we are solving $n/k$ sublists, we get $\Theta(k^2 \cdot nk^{-1})$ which
reduces to $\Theta(nk)$.

### b.

You would have to merge the lists one pair at a time again and again until
there is one big list. If you just merged all the lists together at once, it
would still take $\Theta(n^2/k)$ time.

### c.

Since merge sort runs at $\Theta(n \lg n)$, so we just have to reduce the
expressions:

$$
\begin{align}
nk + n \lg(n/k) &= n \lg n
k + \lg (n/k) &= \lg n
\end{align}
$$

See that $k$ cannot be greater than $n \lg n$ since then it would make the
insertion sort algorithm run at $\Theta(n^2)$ or greater since $k$ grows
relative to $n$. Therefore, the largest value for $k$ would be $\lg n$.

### d.

$k$ should actually be small enough so that the algorithm runs faster than
merge sort, whatever that is on that machine.

## Problem 2-2: Correctness of bubblesort

> Bubblesort is a popular, but inefficient, sorting algorithm. It works by
> repeatedly swapping adjacent elements that are out of order. The procedure
> $\text{Bubblesort}$ sorts array $A[1:n]$.
>
> ### $\text{Bubblesort}(A,n)$
>
> ```cpp
> for i = 1 to n - 1
>     for j = n downto i + 1
>         if A[j] < A[j - 1]
>             exchange A[j] with A[j-1]
> ```
>
> ***a.*** Let $A'$ denote the array $A$ after $\text{Bubblesort}(A,n)$ is
> executed. To prove that $\text{Bubblesort}$ is correct, you need to prove
> that it terminates and that
>
> $$
> A'[1] \le A'[2] \le \dots \le A'[n] \text{    (2.5)}
> $$
>
> In order to show that $\text{Bubblesort}$ actually sorts, what else do you
> need to prove?
>
> The next two parts prove inequality (2.5 *[equation above]*).
>
> ***b.*** State precisely a loop invariant for the **for** loop in lines 2-4,
> and prove that this loop invariant holds. Your proof should use the structure
> of the loop-invariant proof presented in this chapter.
>
> ***c.*** Using the termination condition of the loop invariant proved in part
> (b), state a loop invariant for the **for** loop in lines 1-4 that allows you
> to prove inequality (2.5). Your proof should use the structure of the
> loop-invariant proof presented in this chapter.
>
> ***d.*** What is the worst-case running time of $\text{Bubblesort}$? How does
> it compare with the running time of $\text{Insertion-Sort}$?

### a.

You need to show that $A'$ is actually a reordering of $A$ and not just some
$n$ numbers in sequential order. Otherwise `return [1..n]` would be accepted.

### b.

Loop invariant: $A[j]$ contains the smallest element in $A[j:n]$, which is a
permutation of $A[j:n]$ before the loop ran.
order.

Initialization: Before the loop is ran, $A[j:n] = A[n]$ which, since it is just
one element, must be its smallest element.

Maintenance: Through each iteration of the second **for** loop, $A[j:n]$ sorts
$A[j]$ down one element if it is smaller than the previous element in $A$,
therefore it must be the smallest element in $A[j:n]$.

Termination: After the loop is completed, $j = i$ and $A[i]$ is the smallest
element in $A[i:n]$ which satisfies the loop invariant.

### c.

Loop invariant: $A[1:i-1]$ contains $i-1$ of the smallest values of $A[1:n]$ in
sorted order, and the remaining elements $A[i:n]$ are the remaining larger
values of $A$.

Initialization: $A[1:0]$ is empty, therefore valid.

Maintenance: The second **for** loop makes $A[i]$ the smallest element in
$A[i:n]$ (from part (b)), and now $A[1:i-1]$ contains elements of $A$ smaller
than $A[i]$, in sorted order as a permutation of $A[1:n]$.

Termination: When the loop terminates, $i=n$, which is in the last position in
$A$. Since $A[1:n-1]$ is in correct, sorted order, $A[n] \ge A[i-1]$ and the
invariant holds.

### d.

For each value of $i$, the second **for** loop runs $n-1$ iterations, checking
all values to $n-1$, therefore:

$$
\begin{align}
\sum_{i=1}^{n-1}(n-1) &= \sum_{i=1}^{n-1}n - \sum_{i=1}^{n-1}i \\
&= n(n-1) - \frac{n(n-1)}{2} \\
&= \frac{n(n-1)}{2} \\
&= \frac{n^2-n}{2} \\
\end{align}
$$

Whose largest factor is $n^2$, so $\text{Bubblesort}$ runs in the same scale as
$\text{Insertion-Sort}$, $\Theta(n^2)$.

## Problem 2-3: Correctness of Horner's rule

> You are given the coefficients $a_0, a_1, a_2, \dots , a_n$ of a polynomial
>
> $$
> \begin{align}
> P(x) &= \sum_{k=0}^{n} a_k x^k \\
> &= a_0 + a_1 x + a_2 x^2 + \dots + a_{n-1} x^{n-1} + a_n x^n
> \end{align}
> $$
>
> and you want to evaluate this polynomial for a given value of $x4. *Horner's
> rule* says to evaluate the polynomial according to this parenthesization:
>
> $$
> P(x) = a_0 + x\left(a_1 + x\left(a_2 + \dots + x\left(a_{n-1} + xa_n\right) \dots \right) \right)
> $$
>
> The procedure $\text{Horner}$ implement's Horner's rule to evaluate $P(x)$,
> given the coefficients $a_0, a_1, a_2, \dots , a_n$ in an array $A[0:n]$ and
> the values of $x$.
>
> ### $\text{Horner}(A, n, x)$
>
> ```cpp
> p = 0
> for i = n downto 0
>     p = A[i] + x * p
> return p
> ```
>
> ***a.*** In terms of $\Theta$-notation, what is the running time of this
> procedure?
>
> ***b.*** Write pseudocode to implement the naive polynomial-evaluation
> algorithm that computes each term of the polynomial from scratch. What is the
> running time of this algorithm? How does it compare with $\text{Horner}$?
>
> ***c.*** Consider the following loop invariant for the procedure
> $\text{Horner}$:
>
> At the start of each iteration of the **for** loop of lines 2-3,
>
> $$
> p = \sum_{k=0}^{n-(i+1)} A[k+i+1] \cdot x^k
> $$
>
> Interpret a summation with no terms as equaling 0. Following the structure of
> the loop-invariant proof presented in this chapter, use this loop invariant to
> show that, at termination, $p = \sum_{k=0}^{n} A[k] \cdot x^k$.

## Problem 2-4: Inversions

> Let $A[1:n]$ be an array of $n$ distinct numbers. If $i < j$ and $A[i] >
> A[j]$, then the pair $(i, j)$ is called an inversion of $A$.
>
> ***a.*** List the five inversions of the array $\langle 2, 3, 8, 6, 1
> \rangle$.
>
> ***b.*** What array with elements from the set $\{1, 2, \dots , n\}$ has the
> most inversions? How many does it have?
>
> ***c.*** What is the relationship between the running time of insertion sort
> and the number of inversions in the input array? Justify your answer.
>
> ***d.*** Give an algorithm that determines the number of inversions in any
> permutation on $n$ elements in $\Theta(n \lg n)$ worst-case time. (*Hint:*
> Modify merge sort.
