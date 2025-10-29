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
> $\text{Add-Binary-Integers$ that takes as input arrays $A$ and $B$, along
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
