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
> O(g(n,m)) = \Big\lbrace f(n,m) : & \text{there exist positive constants } c, n_{0}, \text{ and } m_{0} \\
> & \text{such that } 0 \le f(n,m) \le cg(n,m) \\
> & \text{for all } n \ge n_{0} \text{ or } m \ge m_{0} \Big\rbrace.
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
> a^{\log_{b}c} = c^{\log_{b}a}
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

# Problems

## Problem 3-1: Asymptotic behavior of polynomials

> Let
>
> $$
> p(n) = \sum_{i=0}^{d} a_{i}n^{i} \text{ ,}
> $$
>
> where $a_{d} > 0$, be a degree-$`d`$ polynomial in $`n`$, and let $k$ be a
> constant. Use the definitions of the asymptotic notations to prove the
> following properties.
>
> ***a.*** If $k \ge d$, then $p(n) = O(n^{k})$.
>
> ***b.*** If $k \le d$, then $p(n) = \Omega(n^{k})$.
>
> ***c.*** If $k = d$, then $p(n) = \Theta(n^{k})$.
>
> ***d.*** If $k > d$, then $p(n) = o(n^{k})$.
>
> ***e.*** If $k < d$, then $p(n) = \omega(n^{k})$.

## Problem 3-2: Relative asymptotic growths

> Indicate, for each pair of expressions $(A,B)$ in the table below whether $A$
> is $O$, $o$, $\Omega$, $\omega$ or $\Theta$ of $B$. Assume that $k \ge 1$,
> $\epsilon > 0$, and $c > 1$ are constants. Write your answer in the form of
> the table with "yes" or "no" written in each box.
>
> $$
> \begin{align}
> & A & B & O & o & \Theta & \Omega & \omega & \Theta \\
> a. & \lg^{k} n & n^{\epsilon} \\
> b. & n^{k} & c^{n} \\
> c. & \sqrt{n} & n^{\sin n} \\
> d. & 2^{n} & s^{n/2} \\
> e. & n^{\lg c} & c^{\lg n} \\
> f. & \lg(n!) & \lg(n^{n}) \\
> \end{align}
> $$

## Problem 3-3: Ordering by asymptotic growth rates

> ***a.*** Rank the following functions by order of growth. That is, find an
> arrangement $`g_1, g_2, \dots, g_{30}`$ of the functions satisfying $`g_1 =
> \Omega(g_2), g_2 = \Omega(g_3), \dots, g_{29} = \Omega(g_{30})`$. Partition
> your list into equivalence classes such that functions $f(n)$ and $g(n)$
> belong to the same class if and only if $f(n) = \Theta(g(n))$.
>
> $$
> \begin{align}
> \lg(\lg^{\ast}n) & 2^{\lg^{\ast}n} & (\sqrt{2})^{\lg n} & n^2 & n! & (\lg n)! \\
> (3/2)^n & n^3 & \lg^2 n & \lg(n!) & 2^{2^{n}} & n^{1/\lg n} \\
> \ln \ln n & \lg^{\ast} n & n \cdot 2^n & n^{\lg \lg n} & \ln n & 1 \\
> 2^{\lg n} & (\lg n)^{\lg n} & e^n & 4^{\lg n} & (n + 1)! & \sqrt{\lg n} \\
> \lg^{\ast}(\lg n) & 2^{\sqrt{2 \lg n}} & n & 2^n & n \lg n & 2^{2^{n+1}}
> \end{align}
> $$
>
> ***b.*** Give an example of a single nonnegative function $f(n)$ such that
> for all functions $g_{i}(n)$ in part (a), $f(n)$ is neither $O(g_{i}(n))$ nor
> $\Omega(g_{i}(n))$.

## Problem 3-4: Asymptotic notation properties

> Let $f(n)$ and $g(n)$ be asymptotically positive functions. Prove or disprove
> each of the following conjectures.
>
> ***a.*** $f(n) = O(g(n))$ implies $g(n) = O(f(n))$.
>
> ***b.*** $f(n) + g(n) = \Theta(\text{min}\lbrace f(n), g(n) \rbrace)$.
>
> ***c.*** $f(n) = O(g(n))$ implies $\lg f(n) = O(\lg g(n))$, where $\lg g(n)
> \ge 1$ and $f(n) \ge 1$ for all sufficiently large $n$.
>
> ***d.*** $f(n) = O(g(n))$ implies $2^{f(n)} = O\left(2^{g(n)}\right)$.
>
> ***e.*** $f(n) = O\left((f(n))^{2}\right)$.
>
> ***f.*** $f(n) = O\left(g(n)\right)$ implies $g(n) =
> \Omega\left(f(n)\right)$.
>
> ***g.*** $f(n) = \Theta\left(f(n/2)\right)$.
>
> ***h.*** $f(n) + o(f(n)) = \Theta(f(n))$.

## Problem 3-5: Manipulating asymptotic notation

> Let $f(n)$ and $g(n)$ be asymptotically positive functions. Prove the
> following identities:
>
> ***a.*** $\Theta(\Theta(f(n))) = \Theta(f(n))$.
>
> ***b.*** $\Theta(f(n)) + O(f(n)) = \Theta(f(n))$.
>
> ***c.*** $\Theta(f(n)) + \Theta(g(n)) = \Theta(f(n) + g(n))$.
>
> ***d.*** $\Theta(f(n)) \cdot \Theta(g(n)) = \Theta(f(n) \cdot g(n))$.
>
> ***e.*** Argue that for any real constants $`a_1, b_1 > 0`$ and integer
> constants $`k_1, k_2`$, the following asymptotic bound holds:
>
> $$
> (a_{1}n)^{k_{1}} \lg^{k_{2}}(a_{2}n) =
> \Theta\left(n^{k_{1}}\lg^{k_{2}}n\right)\text{ .}
> $$
>
> ***f.*** Prove that for $S \subseteq \mathbb{Z}$, we have
>
> $$
> \sum_{k \in S} \Theta(f(k)) = \Theta\left(\sum_{k \in S} f(k)\right)\text{ ,}
> $$
>
> assuming that both sums converge.
>
> ***g.*** Show that for $S \subseteq \mathbb{Z}$, the following asymptotic
> bound does not necessarily hold, even assuming that both products converge,
> by giving a counterexample:
>
> $$
> \prod_{k \in S} \Theta(f(k)) = \Theta \left(\prod_{k \in S} f(k)\right)\text{ .}
> $$

## Problem 3-6: Variations on $O$ and $\Omega$

> Some authors define $`\Omega`$-notation in a slightly different way than this
> textbook does. We'll use the nomenlature $`\overset{\infty}{\Omega}`$ (read
> "omega infinity") for this alternative definition. We say that $`f(n) =
> \overset{\infty}{\Omega}(g(n))`$ if there exists a positive constant $c$ such
> that $f(n) \ge cg(n) \ge 0$ for inifinitely many integers $n$.
>
> ***a.*** Show that for any two asymptotically nonnegative functions $f(n)$
> and $g(n)$, we have $f(n) = O(g(n))$ or $f(n) =
> \overset{\infty}{\Omega}(g(n))$ (or both).
>
> ***b.*** Show that there exist two asymptotically nonnegative functions
> $f(n)$ and $g(n)$ for which neither $f(n) = O(g(n))$ nor $f(n) =
> \Omega(g(n))$ holds.
>
> ***c.*** Describe the potential advantages and disadvantages of using
> $`\overset{\infty}{\Omega}`$-notation instead of $`\Omega`$-notation to
> characterize the funning times of programs.
>
> Some authors also define $O$ in a slightly different manner. We'll use $O'$
> for the alternative definition: $f(n) = O'(g(n))$ if and only if $|f(n)| =
> O(g(n))$.
>
> ***d.*** What happens to each direction of the "if and only if" in Theorem
> 3.1 on page 56 if we substitute $O'$ for $O$ but still use $\Omega$?
>
> Some authors define $\widetilde{O}$ (read "soft-oh") to mean $O$ with
> logarithmic factors ignored:
>
> $$
> \begin{align}
> \widetilde{O}(g(n)) = \lbrace f(n) : & \text{there exist positive constants
> $c$, $k$ and $n_{0}$ such that} \\
> & 0 \le f(n) \le cg(n) \lg^{k}(n) \text{ for all } n \ge n_{0} \rbrace \text{ .}
> \end{align}
> $$
>
> ***e.*** Define $\widetilde{\Omega}$ and $\widetilde{\Theta}$ in a similar
> manner. Prove the corresponding analog to Theorem 3.1.

## Problem 3-7: Iterated functions

> We can apply the iteration operator $\ast$ used in the $`\lg^{\ast}`$
> function to any monotonically increasing function $f(n)$ over the reals. For
> a given constant $c \in \mathbb{R}$, we define the iterated function
> $f_{c}^{\ast}$ by
>
> $$
> f_{c}^{\ast}(n) = \text{min} \lbrace i \ge 0 : f^{(i)}(N) \le c \rbrace \;,
> $$
>
> which need not be well defined in all cases. In other words, the quantity
> $f_{c}^{\ast}(n)$ is the minimum number of iterated applications of the
> function $f$ required to reduce its argument down to $c$ or less.
>
> For each of the functions $f(n)$ and constants $c$ in the table below, give
> as tight a bound as possible on $f_{c}^{\ast}(n)$. If there is no $i$ such
> that $`f^{(i)}(n) \le c`$, write "undefined" as your answer.
>
> $$
> \begin{align}
> & f(n) & c & f_{c}^{/ast}(n) \\
> a. & n-1 & 0 \\
> b. & \lg n & 1 \\
> c. & n/2 & 1 \\
> d. & n/2 & 2 \\
> e. & \sqrt{n} & 2 \\
> f. & \sqrt{n} & 1 \\
> g. & n^{1/3} & 2 \\
> $$
