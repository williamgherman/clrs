# Exercises

## Section 2.1

### 2.1-1

Using Figure 2.2 as a model, illustrate the operation of $\text{Insertion-Sort} on
an array initially containing the sequence «31, 41, 59, 26, 41, 58».

#### Solution

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

Consider the procedure **Sum-Array** on the facing page. It computes the sum of
the *n* numberes in array *A*[1:*n*]. State a loop invariant for this
procedure, and use its initialization, maintenance, and termination properties
to show that the **Sum-Array** procedure returns the sum of the numbers in
*A*[1:*n*].

**Sum-Array**(*A*, *n*):

```
1   sum = 0
2   for i = 1 to n
3       sum = sum + A[i]
4   return sum
```

#### Solution

Loop invariant: At the start of the **for** loop on line 2, `sum` is the
correct sum of *A*[1:*i*]

Initialization: Prior to the first iteration, there are no elements in the
sequence, and the sum is correctly zero.

Maintenance: Each iteration adds the value *A*[*i*] to the `sum`, which means
that the `sum` still correctly reflects *A*[1:[*i*]].

Termination: The loop variable *i* terminates after all values 1 to *n* are
exhausted. Once *i* = *n* + 1, sum will correctly equal the sum of all values
in *A*[1:*n*], which means our algorithm is correct.

### 2.1-3

Rewrite the **Insertion-Sort** procedure to sort into monotonically decreasing
insteadof monotonically increasing order.

#### Solution

**Insertion-Sort**(*A*, *n*):

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

Consider the *searching problem*:

**Input:** A sequence of *n* numbers «*a*<sub>1</sub>, *a*<sub>2</sub>, ...
*a*<sub>*n*</sub>» stored in arrayt *a*[1:*n*] and a value *x*.

**Output:** An index *i* such that *x* equals *A*[*i*] or the special value
`NIL` of *x* does not appear in *A*.

Write pseudocode for *linear search*, which scans through the array from
beginning to end, looking for *x*. Using a loop invariant, prove that your
algorithm is correct. Make sure that your loop invariant fulfills the three
necessary properties.

#### Solution

**Linear-Search**(*A*[*n*], *x*):

```
1   for i = 1 to n
2       if A[i] == x
3           return i
4   return NIL
```

Loop invariant: At the start of each iteration of the **for** loop, the
subarray $A[1..i-1]$ do not contain the value $x$.

Initialization: Prior to the first iteration, the subarray
