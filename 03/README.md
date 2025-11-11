# Exercises

## Section 3.1

### 3.1-1

> Modify the lower-bound argument for insertion sort to handle input sizes that
> are not necessarily a multiple of 3.


### 3.1-2

> Using reasoning similar to what we used for insertion sort, analyze the
> running time of the selection sort algorithm from Exercise 2.2-2.

## 3.1-3

> Suppose that $\alpha$ is a fraction in the range $0 < \alpha < 1$. Show how
> to generalize the lower-bound argument for insertion sort to consider an
> input in which the $\alpha n$ largest values start in the first $\alpha n$
> positions. What additional restriction do you need to put on $\alpha$? What
> value of $\alpha$ maximizes the number of times that the $\alpha n$ largest
> values must pass through each of the middle $(1 - 2\alpha)n$ array positions?

## Section 3.2

### 3.2-1

> Let $f(n)$ and $g(n)$ be asymptotically nonnegative functions. Using the
> basic definition of $\Theta$-notation, prove that $`max\lbrace f(n), g(n)
> \rbrace = \Theta(f(n) + g(n))`$.

### 3.2-2

> Explain why the statement, "The running time of algorithm $A$ is at least
> $O(n^2)$," is meaningless.

### 3.2-3

> Is $2^{n+1} = O(2^n)$? Is $2^{2n} = O(2^n)$?

### 3.2-4

> Prove Theorem 3.1.

### 3.2-5

> Prove that the running time of an algorithm is $\Theta(g(n))$ if and only if
> its worst-case running time is $O(g(n))$ and its best-case running time is
> $\Omega(g(n))$.

### 3.2-6

> Prove that $o(g(n)) \cap \omega(g(n))$ is the empty set.

### 3.2-7

> We can extend our notation to the case of two parameters $n$ and $m$ that can
> go to $\infty$ independently at different rates. For a given function
> $g(n,m)$, we denote by $O(g(n,m))$ the set of functions
>
> $$
> \begin{align}
> O(g(n,m)) = \lbrace f(n,m) &: \text{there exist positive constants } c, n_{0}, \text{ and } m_{0} \\
> & \text{such that } 0 \le f(n,m) \le cg(n,m) \\
> & \text{for all } n \ge n_{0} \text{ or } m \ge m_{0} \rbrace.
> \end{align}
> $$
>
> Give corresponding definitions of $\Omega(g(n,m))$ and $\Theta(g(n,m))$.

## Section 3.3

### 3.3-1

> Show that if $f(n)$ and $g(n)$ are monotonically increasing functions, then
> so are the functions $f(n) + g(n)$ and $f(g(n))$, and if $f(n)$ and $g(n)$
> are in addition nonnegative, then $f(n) \cdot g(n)$ is monotonically
> increasing.

### 3.3-2

> Prove that $\lfloor \alpha n \rfloor + \lceil (1 - \alpha)n \rceil = n$ for
> any integer $n$ and real number $\alpha$ in the range $0 \le \alpha \le 1$.

### 3.3-3

> Use equation (3.14) or any other means to show that $(n + o(n))^k =
> \Theta(n^k)$ for any real constant $k$. Conclude that $\lceil n \rceil ^k =
> \Theta(n^k)$ and $\lfloor n \rfloor ^k = \Theta(n^k)$.
>
> Equation (3.14):
>
> $$
> \begin{equation}
> 1 + x \le e^x
> \tag{3.14}
> \end{equation}
> $$

### 3.3-4

> Prove the following:
>
> ***a.*** Equation (3.21)
>
> $$
> a^{log_{b}c} = c^{log_{b}a}
> \tag{3.21}
> $$
>
> where logarithm bases are not 1.
>
> ***b.*** Equations (3.26)-(3.28).
>
> $$
> \begin{align}
> n! &= o(n^n) \tag{3.26} \\
> n! &= \omega(2^n) \tag{3.27} \\
> \lg (n!) &= \Theta(n \lg n) \tag{3.28}
> \end{align}
> $$
>
> ***c.*** $\lg(\Theta(n)) = \Theta(\lg n)$.

### 3.3-5

> Is the function $\lceil \lg n \rceil !$ polynomically bounded? Is the
> function $\lceil \lg \lg n \rceil !$ polynomially bounded?

### 3.3-6

> Which is asymptotically larger: $`\lg(\lg ^{*} n)`$ or $`\lg^{*}(\lg n)`$?

### 3.3-7

> Show that the golden ration $\phi$ and its conjugate $\hat{\phi}$ both
> satisfy the equation $x^{2} = x + 1$.

### 3.3-8

> Prove by induction that the $`i`$th Fibonacci number satisfies the equation
>
> $$
> F_{i} = (\phi^{i} - \hat{\phi}^{i})/\sqrt{5}
> $$
>
> where $\phi$ is the golden ratio and $\hat{\phi}$ is its conjugate.

### 3.3-9

> Show that $k \lg k = \Theta(n)$ implies $k = \Theta(n / \lg n)$.
