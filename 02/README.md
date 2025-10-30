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
> $\text{Sum-Array}(A, n)$:
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

Rewrite the $\text{Insertion-Sort}$ procedure to sort into monotonically
decreasing instead of monotonically increasing order.

#### Solution

$\text{Insertion-Sort}(A, n)$:

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

$\text{Linear-Search}(A[n], x)$:

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

$\text{Add-Binary-Integers}(A, B, n)$:

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

$\text{Selection-Sort}(A, n)$:

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


