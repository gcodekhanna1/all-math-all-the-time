---
title: Numbers - A Gentle Introduction
label: chap:numbers_a_gentle_introduction
author: Gaurav Khanna, Ph.D.
---

(sec:hierarchy_of_numbers)=
## Hierarchy of Numbers

Let's give some basic definitions of the different number classes:

- **Integers, $\mathbb{Z}$:** Numbers without a fractional part that can be positive or negative.

  Within this class of numbers, we can define two sub-classes:

  - **Whole Numbers:** The set of numbers including zero and the positive integers.

  - **Natural Numbers, $\mathbb{N}$** The set of whole numbers excluding zero.

- **Rational Numbers, $\mathbb{R}$:** A rational number is a number $q$ that can be written as a fraction of the form $q = \frac{a}{b}$, where $a$ and $b$ are integers and $b \neq 0$. So a number such $\frac{1}{3}$ is a rational number since it meets this definition, even though it is a repeating decimal.

  This is a key point -- don't get confused by thinking that a repeating decimal such as $0.3333\ldots$ is "irrational" because it never ends (and therefore we will "never really know" what it is). The only criteria for something to be a rational number is that it can be expressed as a ratio of two integers. So $\frac{1}{3} = 0.3333\ldots = 0.\overline{3}$ can be expressed as a ratio of integers, it is a rational number. In fact, look at it this way: if a decimal repeats indefinitely then we know *exactly* how it behaves!

- **Irrational Numbers**: An irrational number cannot be expressed as a ratio of integers. For example is $\sqrt{2}, \sqrt{5}$ etc.

  A subset of irrational numbers that are **transcendental**. These are numbers that are not algebraic. That is, they cannot be expressed as the root of a non-zero polynomial with integer (or rational) coefficients. Transcendental numbers can be part of real or complex numbers. For example, $\pi$ is probably the most famous transcendental number.

- **Imaginary Numbers**: Any number that when squared gives a negative result. We will cover these in more detail in {ref}`chap:complex_numbers_a_gentle_introduction`.

Figure {ref}`fig:heirarchy_of_numbers_1` is a way to show how the different groups of numbers form subsets of one another. As we can see, all the numbers are in fact a subset of the complex numbers. A useful mnemonic is:

$$
\mathbb{N} \subset \mathbb{Z} \subset \mathbb{Q} \subset \mathbb{R} \subset \mathbb{C}
$$

:::{figure} TODO_heirarchy_of_numbers_1.pdf
:alt: TODO
**[Figure placeholder — standalone TikZ PDF not yet created]**
:::


## Order of Operations

Thankfully, mathematics has built-in rules governing the order in which we are to perform operations.

The following examples fall in the category of: "when in doubt, always trust the order of operations".


(sec:intervals)=
## Intervals

:::{figure} TODO_intervals_table_1.pdf
:alt: TODO
**[Figure placeholder — Intervals table with number line diagrams, standalone TikZ PDF to be created]**
:::

(sec:divisibility_rules)=
## Divisibility Rules

It's always fun to revisit something I'm sure I learned in elementary school... but forgot! Here are some divisibility rules that tell you very quickly whether a number is divisible by integers from 1 - 10. These are shown in Table {ref}`tab:basic_divisibility_rules`.

:::{table} Basic divisibility rules for integers less than 10
:label: tab:basic_divisibility_rules

| **Divisor** | **Rule** | **Example** |
|---|---|---|
| 2 | If the last digit is 0, 2, 4, 6 or 8 | *C'mon Man!* |
| 3 | If the sum of digits is divisible by 3 | $\displaystyle 921 \rightarrow \frac{9 + 2 + 1}{3} = 4$ |
| 4 | If the number formed by last two digits is divisible by 4 | $\displaystyle 524 \rightarrow \frac{24}{4} = 6$ |
| 5 | If the last digit is 0 or 5 | *C'mon Man!* |
| 6 | If number is divisible by 2 AND number is divisible by 3 | $\displaystyle \frac{468}{2} = 234,\ \frac{468}{3} = 156$ |
| 7 | No "simple" rule exists |  |
| 8 | If number formed by last three digits is divisible by 8 | $\displaystyle 24,296 \rightarrow \frac{296}{8} = 37$ |
| 9 | If the sum of digits is divisible by 9 | $\displaystyle 549 \rightarrow \frac{5+4+9}{9} = 2$ |

:::


### Divisibility Rules for 7

Note the special case of the number 7. No simple divisibility rule (that is, as "simple" as for the other digits) is known. However, there are algorithims for determining whether a number is divisible by 7.


## Even and Odd Numbers

### Even and Odd - More Than Meets The Eye

As it turns out, there is a lot more to even and odd numbers than you may have learned in elementary school. Some of the basic results derived in this section will be necessary to prove some important properties of rational and irrational numbers.

But first, some definitions:

An **even number** is any integer that can be divided exactly by 2. Any even number, $n$, can be expressed as a multiple of 2. That is,

$$
\text{Even Numbers:}\ \ n = 2 k
$$ (eq:even_numbers_1)

where $k$ is some integer.

An **odd number** is is any integer that cannot be divided exactly by two. Dividing an odd number by 2 leaves a remainder of 1. If $n$ is an odd number, and $k$ is any integer, then we can write any odd number as

$$
\text{Odd Numbers:}\ \ n = 2 k + 1
$$ (eq:odd_numbers_1)

Note first that even and odd numbers are always integers by definition. Any number with a fraction cannot be considered even or odd. So even though 3 is an odd number, $3 1/4$ is neither even nor odd.

Odd numbers can also be expressed as

$$
\text{Odd Numbers:}\ \ n = 2 k - 1
$$

This follows straight from our first definition of odd numbers, as we can always write:

$$
\begin{aligned}
n & = 2 k - 1 \\
& = 2 k - 2 + 1 \\
& = 2 (k - 1) + 1
\end{aligned}
$$

Since $k - 1$ is itself an integer, we see that $n$ has the form we expect for an odd number.

Both Eqns.() and () express a fundamental aspect of odd numbers: there is one on either side of an even number. Therefore, if $n = 2k$ is even, we can get an odd number by going one integer greater than or less than $n$.

Our definition of an odd number guarantees that it will not be divisible exactly by 2. That is the $2k$ portion of the odd number is exactly divisible by 2. But you are then left with the remainder of 1.

Furthermore, note that any odd number can be written as the difference of two squares. That is, we can always write $2k + 1$ as

$$
(n+1)^2 - n^2 = n^2 + 2n + 1 - n^2 = 2n + 1
$$

Pick any odd integer and you can see this will hold true:

$$
\begin{aligned}
5 = 2(2) + 1 & \rightarrow \ 3^2 - 2^2 = 9 - 4 = 5 \\
91 = 2(45) + 1 &  \rightarrow \ 46^2 - 45^2 = 2116 - 2025 = 91
\end{aligned}
$$

There is a beautiful visual proof of this property of odd numbers: [https://medium.com/math-simplified/3-visual-mathematical-proofs-663d197af229](https://medium.com/math-simplified/3-visual-mathematical-proofs-663d197af229)


### Even and Odd Numbers - Some Interesting Results

If $n$ is an odd number, then $n^2$ is also odd.

We will do this proof by contradiction. Suppose that $n^2$ is not odd; this means that $n^2$ is even. If $n$ is an odd integer, then $n = 2 k  + 1$ where $k \in \mathbb{Z}$. Therefore, $n^2 = (2 k + 1)^2 = 4 k^2 + 4 k + 1$. We know that $n^2$ is an integer since sums and products of integers are also integers. But since we assumed that $n^2$ is even, by definition, $n^2 = 2 q$ where $q \in \mathbb{Z}$. This means that

$$
2 q = 4 k^2 + 4 k + 1\ \rightarrow\ q = 2 k^2 + 2 k + \frac{1}{2}
$$

Because of the presence of the $1/2$ term on the right-hand side of the above, $q$ cannot be an integer. This leads to a contradiction; our assumption of $n^2$ being even is incorrect.

Therefore if $n$ is odd, then $n^2$ is also odd.


### Is Zero An Even or Odd Number?

Zero is an even number by the quotient-remainder theorem.


### Properties of Even and Odd Numbers

With these definitions in hand, we can look at the addition and multiplication of even and odd numbers.

For addition, we have

$$
\begin{aligned}
\text{Even + Even:} \quad 2 k_1 + 2 k_2 & = 2 (k_1 + k_2) \\
{} & = 2 (k) \ \rightarrow\ \text{Even} \\
\text{\it Example:} \quad 2 + 4 & = 6 \\
\text{Even + Odd:} \quad 2 k_1 + 2 k_2 + 1 & = 2 (k_1 + k_2) + 1 \\
{} & = 2 (k) + 1 \ \rightarrow\ \text{Odd} \\
\text{\it Example:} \quad 2 + 5 & = 7 \\
\text{Odd + Odd:} \quad 2 k_1 + 1 + 2 k_2 + 1 & = 2 (k_1 + k_2) + 2 \\
{} & = 2 (k + 1) \ \rightarrow\ \text{Even} \\
\text{\it Example:} \quad 3 + 5 & = 8 \\
\end{aligned}
$$ (eq:addition_even_odd_numbers)

In the above discussion, $k_1$ and $k_2$ are two different integers; we have simply represented their sum as another integer $k$; i.e., $(k_1 + k_2 = k)$.

For multiplication, we have

$$
\begin{aligned}
\text{Even} \times \text{Even:} \quad 2 k_1 \times 2 k_2 & = 4 k_1 k_2 \\
{} & = 2 (2 k_1 k_2) \\
{} & = 2 (k)\ \rightarrow\ \text{Even} \\
\text{\it Example:} \quad 2 \times 4 & = 8 \\
\text{Even} \times \text{Odd:} \quad 2 k_1 \times (2 k_2 + 1) & = 4 k_1 k_2 + 2 k_1 \\
{} & = 2 (2 k_1 k_2 + k_1) \\
{} & = 2 (k)\ \rightarrow\ \text{Even} \\
\text{\it Example:} \quad 2 \times 5 & = 10 \\
\text{Odd} \times \text{Odd:} \quad (2 k_1 + 1) \times (2 k_2 + 1) & = 4 k_1 k_2 + 2k_1 + 2k_2 + 1 \\
{} & = 2 (2 k_1 k_2 + k_1 + k_2) + 1 \\
{} & = 2 (k) + 1\ \rightarrow\ \text{Odd} \\
\text{\it Example:} \quad 5 \times 7 & = 35 \\
\end{aligned}
$$ (eq:multiplication_even_odd_numbers)

As before, we are simply representing the products and sums of the integers $k_1$ and $k_2$ in the parenthesis as one integer, $k$.


### Squares of Even and Odd Numbers

The squares of even and odd numbers can be determined as follows.

If $n$ is an even number, then using our definition we can write $n = 2 k_1$, where $k_1$ is some integer, even or odd. So the square of this even number is given by:

$$
\begin{aligned}
n & = 2 k_1 \\
n^2 & = \left(2 k_1 \right)^2 \\
& = 4 k_1^2 \\
& = 2 \left( 2 k_1^2 \right) \\
& = 2 (k)
\end{aligned}
$$ (eq:squares_of_even_odd_numbers_1)

Remember that 2 multiplied by integer, even or odd, makes the final number even. So irrespective of whether $k = 2 k_1^2$ is even or odd, since we have $2 k$ in the final step, that number is even (incidentally $k = 2 k_1^2$ is also even). What we have shown is that if $n$ is even, so is its square.

However, if $n$ is an odd number, we get a different result. Using our definition we can write $n = 2 k_1 + 1$, where $k_1$ is some integer. So the square of this odd number is given by:

$$
\begin{aligned}
n^2 & = \left( 2 k_1 + 1 \right)^2 \\
n^2 & = 4 k_1^2 + 4 k_1 + 1 \\
& = 2 \left(2 k_1^2 + 2 k_1 \right) + 1 \\
& = 2 (k) + 1\ \rightarrow\ \text{Odd}
\end{aligned}
$$ (eq:squares_of_even_odd_numbers_2)

So if $n$ is odd, it's square is also odd.

So we can establish two important rules of thumb:

:::{admonition} Rule of Thumb: Squares of Even and Odd Numbers
This is a **tcolorbox**.
:::

This brings up an interesting question: If $n^2$ is even, does it imply that $n$ is also even? This question is important because we'll need it to prove the irrationality of $\sqrt{2}$. The answer to this question is not so straightforward as we assume. In fact, we cannot rely on Eq. {ref}`eq:squares_of_even_odd_numbers_1` to show this.

Let's explore this further using logic. In Eq. {ref}`eq:squares_of_even_odd_numbers_1`, we showed that

$$
\text{If $n$ is an even number} \rightarrow \text{$n^2$ is an even number}
$$

Here we have a statement of the form

$$
\text{Original:} \quad p \rightarrow q
$$

The converse of this statement is

$$
\text{Converse:} \quad q \rightarrow p
$$ (eq:squares_of_even_odd_numbers_3)

Logically, the converse of a statement doesn't always have the same value (True or False) as the original statement. That is, if our original statement is true, the following statement is *not necessarily* true: "If $n^2$ is an even number $\rightarrow$ $n$ is an even number."

An analogy may be helpful here. The statement, "If I live in Paris, then I live in France" is not logically equivalent to its converse: "If I live in France, then I live in Paris". However, the contrapositive of a statement is logically equivalent to the original. Recall that the contrapositive is defined as:

$$
\text{Contrapositive:} \quad \sim q \rightarrow\ \sim p
$$ (eq:squares_of_even_odd_numbers_4)

Going back to our analogy: The statement, "If I live in Paris, then I live in France" is logically equivalent to its converse: "If I don't live in France, then I don't live in Paris".

As it turns out, we cannot directly prove the statement:

$$
\text{Statement:}\ \text{If $n^2$ is an even number} \rightarrow \text{$n$ is an even number}
$$

However, we can write the contrapositive as

$$
\text{Contrapositive:}\ \text{If $n$ is not an even number} \rightarrow \text{$n^2$ is not an even number}
$$

Since "not an even number" is the same as saying "odd number", we may equivalently write the contrapositive to the original statement as

$$
\text{Contrapositive:}\ \text{If $n$ is an odd number} \rightarrow \text{$n^2$ is an odd number}
$$ (eq:squares_of_even_odd_numbers_5)

Well, that's exactly what we did in deriving Eq. {ref}`eq:squares_of_even_odd_numbers_2`! So if the above statement in Eq. {ref}`eq:squares_of_even_odd_numbers_5` is true, then it's contrapositive is true. Therefore, we can state that

$$
\text{\bf If}\ n^2\ \text{\bf is an even number} \rightarrow\ n\ \text{\bf is an even number}
$$ (eq:squares_of_even_odd_numbers_6)

<div style="text-align:right">§</div>


(sec:squares)=
## Squares

$$
\sqrt{25} \times \sqrt{25} = 25
$$

(sec:perfect_squares)=
### Perfect Squares

Perfect squares are integers that are obtained by squaring a whole number or an integer. That is, $36 = 6 \times 6$ and $144 = 12 \times 12$ are perfect squares. The following table below shows the perfect squares of the numbers 1 to 20. Note -- it is a handy thing to have these memorized!

| **Number** | **Perfect Square** |
|---|---|
| 1 | $1^2 = 1$ |
| 2 | $2^2 = 4$ |
| 3 | $3^2 = 9$ |
| 4 | $4^2 = 16$ |
| 5 | $5^2 = 25$ |
| 6 | $6^2 = 36$ |
| 7 | $7^2 = 49$ |
| 8 | $8^2 = 64$ |
| 9 | $9^2 = 81$ |
| 10 | $10^2 = 100$ |
| 11 | $11^2 = 121$ |
| 12 | $12^2 = 144$ |
| 13 | $13^2 = 169$ |
| 14 | $14^2 = 196$ |
| 15 | $15^2 = 225$ |
| 16 | $16^2 = 256$ |
| 17 | $17^2 = 289$ |
| 18 | $18^2 = 324$ |
| 19 | $19^2 = 361$ |
| 20 | $20^2 = 400$ |

: Perfect Square Numbers from 1 to 20

Perfect squares have a few interesting properties that we'll explore. For instance, observe the last digit of the perfect squares in the table above. You will notice that they end with any one of these digits 0, 1, 4, 5, 6, or 9. After trying various perfect square numbers you would have observed an important property of perfect squares. Numbers that have any of the digits 2, 3, 7, or 8 in their units place are non-perfect square numbers, whereas, numbers that have any of the digits 0, 1, 4, 5, 6, or 9 in their units place might be perfect squares.

The difference between two consecutive perfect squares is given by:

$$
n^2 - (n-1)^2 = n^2 - (n^2 - 2 n + 1) = 2 n - 1
$$

We know that a factor is a number that can be multiplied with another number to get a specific product. For most numbers, we can think of factors as coming in pairs. For example, let's look at the factors of 12. The following multiplication facts/pairs can get a product of 12: $1 \times 12$, $2 \times 6$, and $3 \times 4$. Therefore, the factors are 1, 2, 3, 4, 6, 12. This has an even number of factors because each factor has another factor paired with it to get to the desired product.

However, perfect squares are different because for one of the factors, the paired factor is itself. Let's look at the number 36. The following product of pairs yield a value of 36: $1 \times 36$, $2 \times 18$, $3 \times 12$, $4 \times 9$, $6 \times 6$. Note that 6 shows up twice, but when we write the list of factors, 6 need only be mentioned once. Therefore, the factors are 1, 2, 3, 4, 6, 9, 12, 18, and 36. We see that there are an odd number of factors of 66; the square root of the perfect square (in this case 6) does not have a corresponding number that is different.

A formal proof of this neat fact about perfect squares will await until we cover the Fundamental Theorem of Arithmetic in Section {ref}`sec:fundamental_theorem_of_arithmetic`.


(sec:perfect_powers)=
## Perfect Powers

A perfect power is natural number that can be expressed as an integer power of another integer greater than 1. More formally, $n = m^k$ is a perfect power if $m > 1$ is a positive integer and $k \geq 2$.

For example, $27 = 3^3$ and $125 = 5^3$ are perfect powers.

(sec:catalan_conjecture)=
### Mihailescu's Theorem (Catalan's Conjecture)

Catalan's Conjecture, now proven and known as Mihailescu's Theorem, states that the only solution in natural numbers of the equation:

$$
x^a - y^b = 1
$$

for $a, b > 1$ and $x, y > 0$ is $x = 3$, $y = 2$, $a = 2$, and $b = 3$, corresponding to the consecutive integers $8$ and $9$ ($2^3 = 8$, $3^2 = 9$).

This conjecture, proposed by Eugène Charles Catalan in 1844, was proven by Romanian mathematician Preda Mihăilescu in 2002. It resolves a long-standing question in number theory by confirming that the pair $(8, 9)$ is the only pair of consecutive perfect powers among the natural numbers.


## Rational Numbers

The definition of a rational number


## Repeating Fractions

### Repeating Fractions Are Rational


### $0.\bar{9} = 1$

You've probably seen or have been told that 0.9999$\ldots$ repeated infinitely equals one. Expressing this using standard notation, we can write:

$$
0.99999\ldots = 0.\bar{9} = 1
$$

It turns out there are a few ways to prove this. Here is a simple argument. We start with assigning a variable to $\bar{9}$:

$$
x = 0.\bar{9}
$$

If we multiple both sides by 10, we get

$$
10 x = 9.\bar{9}
$$

Now, we can do some straightforward algebra:

$$
\begin{aligned}
10 x & = 9.\bar{9}  \\
10 x & = 9 + 0.\bar{9}  \\
10 x & = 9 + x \\
9 x & = 9 \\
x & = 1
\end{aligned}
$$

Since we had originally defined $x = 0.\bar{9}$, this means:

$$
x = 0.\bar{9} = 1
$$

*Q.E.D.*


(sec:irrational_numbers)=
## Irrational Numbers

An irrational number is a number that cannot be expressed as a fraction $p / q$ for any integers $p$ and $q$. Irrational numbers have decimal expansions that neither terminate nor display any repeatable pattern (i.e, the decimal expansion does not become periodic).

When we first learn about rational and irrational numbers, there is a tendency to confuse things when it comes to numbers with decimals that continue indefinitely. Let's emphasize again that a rational number, such as $1/3$, has a repeating decimal .... choose example from Fermat's book... 13/7


### The Irrationality of $\sqrt{2}$

The standard way to show that $\sqrt{2}$ is irrational is proof by contradiction. Suppose that $\sqrt{2}$ is a rational number. Therefore, we can find two integers, $p$ and $q$, that are relatively prime (i.e., they have no common factors others than 1) such that:

$$
\frac{p}{q} = \sqrt{2}\ \longrightarrow\ \left(\frac{p}{q}\right)^2 = 2
$$ (eq:irrationality_of_2_1)

This means:

$$
p^2 = 2 q^2
$$ (eq:irrationality_of_2_2)

Using the definition of even numbers given in Eq. {ref}`eq:even_numbers_1`, we see that $p^2$ is an even number. We also established in Eq. {ref}`eq:squares_of_even_odd_numbers_6` that if $p^2$ is even, then $p$ itself is even. Using the definition of even numbers again, $p$ can be written as $p = 2 r$ where $r$ is some integer. Inserting this expression for $p$ in the above equation gives us:

$$
\begin{aligned}
(2r)^2 & = 2 q^2 \\
4 r^2 & = 2 q^2 \\
2 r^2 & = q^2
\end{aligned}
$$

Using a similar logic as above, we see that $q^2$ is even, which implies that $q$ itself is even. If $p$ and $q$ are both even, they share a common factor of 2. They may share other factors in common as well, but we know for sure that they share at least a common factor of 2. That contradicts our original assumption that $p$ and $q$ are relatively prime.

Therefore $\sqrt{2}$ cannot be irrational, which means it is irrational.

<div style="text-align:right">§</div>


(sec:square_roots)=
## Square Roots

The **square root** of a number $x$ is symbolically represented as $\sqrt{x}$ or $\displaystyle x^{\frac{1}{2}}$. It is a value that, when multiplied by itself, returns the number $x$.

For example, we want to know the square root of 25. We seek a number such that

$$
\sqrt{25} \times \sqrt{25} = 25
$$

We know that the number 5 meets the criteria for the square root of 25, since:

$$
5 \times 5 = 25
$$

However, 5 is not a unique square root for 25, since we also know that:

$$
-5 \times -5 = 25
$$

So $- 5$ is another possible square root of 25.

To summarize, we may write:

$$
\sqrt{25} = +5, -5
$$

Note that you cannot multiply the two different square roots of a number and expect to return that same number. Taking our current example, even though $+5$ and $-5$ are both square roots of 25, multiplying these two does not return the original number:

$$
5 \times -5 \neq 25
$$

Every non-negative real number $x$ has a unique, non-negative square root. This is sometimes referred to as the **principal square root**, $\sqrt{x}$. Some more terminology: the square root symbol, $\sqrt{\phantom{x}}$, is called the **radical sign** or **radix**. The number (or expression) whose square root is being computed is called the **radicand**; i.e., it is the expression inside the radical sign.

Every positive number $x$ has two square roots:

$$
\text{Square root of}\ x\ \rightarrow\ \sqrt{x}, - \sqrt{x} \rightarrow\ \pm \sqrt{x}
$$

where the $\pm$ notation is simply a shorthand way of expressing the two values. When the question, "find *the* square root of $x$", is asked without any further qualification, the principal (positive) square root is usually being requested.

There are a couple of interesting ways to think about square roots that generalizes them conceptually.

We can think of the principal square root, $\sqrt{\phantom{x}}$, as a function or operator that, when multiplied by itself, equals $x$. Figure {ref}`fig:square_root_mapping`(a) will help us understand this better. Here we have plotted $x$ on the horizontal axis and the $\sqrt{x}$ on the vertical axis. We see that this function maps:

$$
5 = \sqrt{25}\ \rightarrow\ \sqrt{25} \times \sqrt{25} = 25
$$

:::{figure} square_root_mapping_function.pdf
:alt: Square root mapping function
:::

Secondly, we can interpret the principal square root function geometrically. As shown in Figure {ref}`fig:square_root_mapping`(b), we see that this function maps the area of a sqaure to the length of its sides.

While this next discussion may seem overly pedantic, it's important to make the distinction between a) the principal square root function, and b) the solution to $x^2 = y$. In the first case, the principal square root function returns the *positive* square root of the number. For example, the principal square root of 64 is

$$
\text{Principal}\ \sqrt{64} = 8
$$

which is a positive number. In the second case, the solution to the equation is $x = \pm \sqrt{y}$; i.e., the solution contains both the positive and negative square root. For example,

$$
\begin{aligned}
x^2 & = 64  \\
x & = \pm \sqrt{64}\\
x & = \pm 8
\end{aligned}
$$

The principal square root function maps the set of non-negative real numbers onto itself. Let's explore this statement further as it can seem confusing. This statement does not mean that the function maps a particular number onto itself; i.e., it does *not* mean $\sqrt{25} \rightarrow 25$. It means that for for every non-negative real number you input into the function, you get another non-negative real number. Unless the number happens to be 0 or 1, the principal square root function will map a non-negative real input value to some other non-negative real output value. The key word here is *set*, which is a collection of numbers. When thinking about it in terms of sets, the principal square function maps this particular input set (of non-negative real numbers) to the same output set (of non-negative real numbers).

Note that for $0 < x < 1$, we have $\sqrt{x} > x$. This makes sense since a fraction less than one multiplied by itself yields a smaller number. That is, if $0 < x < 1$, we know that

$$
x \cdot x < x
$$

Taking the square root of both sides of the above, we get:

$$
\begin{aligned}
\sqrt{x \cdot x} & < \sqrt{x} \\
\sqrt{x^2} & < \sqrt{x} \\
x & < \sqrt{x}
\end{aligned}
$$

This can be seen in Figure {ref}`fig:square_root_0_to_1`.

:::{figure} square_root_0_to_1.pdf
:alt: Square root for 0 to 1
:::

Square roots of negative numbers is an entire universe of discussion in itself, and will be covered in Chapter {ref}`chap:foundations_complex_numbers_a_gentle_introduction`.

### Square Roots: Basic Properties

In this section, we will cover some basic properties of square roots.

For all non-negative real numbers $x$,

$$
\sqrt{x} = x^{\frac{1}{2}}
$$ (eq:square_root_properties_0)

**Product property of square roots**:

For all non-negative real numbers $x$ and $y$

$$
\sqrt{x y} = \sqrt{x}\ \sqrt{y} \qquad x,y \geq 0
$$ (eq:square_root_properties_1)

**Quotient property of square roots**:

$$
\sqrt{\frac{x}{y}} = \frac{ \sqrt{x}}{\sqrt{y}} \qquad x \geq 0,\  y > 0
$$ (eq:square_root_properties_2)

For all real numbers, $x \in \mathbb{R}$:

$$
\sqrt{x^2} = |x| =  
\left\{
\begin{aligned}
& x \quad \text{if}\ x \geq 0 \\
& - x \quad \text{if}\ x < 0
\end{aligned}
\right.
$$ (eq:square_root_properties_3)


### Square Roots: Basic Examples

:::{admonition} Example
:class: example
Simplify the following:

$$
\sqrt{ 9^{16 x^{2}} }
$$

It's tempting right away to answer $3^{4x}$, but that would be wrong! The best way to solve it would be to write the expression to the power of $\frac{1}{2}$:

$$
\begin{aligned}
\sqrt{ 9^{16 x^{2}} } & = \left( 9^{16 x^2 }\right)^{\frac{1}{2}} \\
& = 9^{\frac{1}{2} \left( 16 x^2 \right)} \\
& = 9^{8 x^2}
\end{aligned}
$$
:::

:::{admonition} Example
:class: example
Every once in a while, I'll see the following on a social media post. Find the error in this set of steps:

$$
\begin{aligned}
1 & = \sqrt{1} \\
1 & = \sqrt{(-1)(-1)} \\
1 & = \sqrt{-1} \sqrt{-1} \\
1 & = i \times i \\
1 & = -1
\end{aligned}
$$

The mistake is in going from the second to the third step. As we saw in Eq. {ref}`eq:square_root_properties_1`, the product property of square roots is only valid when $x$ and $y$ are both positive numbers.
:::


### Rationalizing The Denominator

When the square root is in the denominator of a fraction, it is sometimes useful to remove it in order to simplify an expression. This process is called **rationalizing the denominator**. One common way to rationalize the denominator is by a clever us of the conjugate of the denominator (we will cover conjugates in Section {ref}`sec:binomials`).

The following example will help illustrate this. Let's try and simplify:

$$
\frac{7}{3 - \sqrt{2}}
$$

We don't like the $3 - \sqrt{2}$ in the denominator. We know that we can always multiply by 1 and have the same expression. Let's see what happens when we multiply this expression by a fraction whose numerator and denominator are $3 + \sqrt{2}$ (i.e., the conjugate of are the conjugate of $3 - \sqrt{2}$):

$$
\begin{aligned}
\frac{7}{3 - \sqrt{2}} & = \frac{7}{3 - \sqrt{2}}\ \frac{3 + \sqrt{2}}{3 + \sqrt{2}} \\
& = \frac{7 (3 + \sqrt{2})}{(3 - \sqrt{2})(3 + \sqrt{2})} \\
& = \frac{7 (3 + \sqrt{2})}{9 + 3 \sqrt{2} - 3 \sqrt{2} - \sqrt{2} \sqrt{2} } \\
& =  \frac{7 (3 + \sqrt{2})}{9 - 2} \\
& = 3 + \sqrt{2}
\end{aligned}
$$

We see that by using the conjugate in this manner, we're able to simplify the expression and remove the square root from the denominator.

The basic steps to rationalize the denominator are as follows:

1. Calculate the conjugate of the denominator

1. Create a form of the number 1 by a fraction whose numerator and denominator are conjugate

1. Multiply the original fraction by this form of 1 and simplify.


### Square Roots: A Brief History

Square roots have long fascinated mathematicians and have their historical roots (pun intended!) in geometry.


(sec:zero_power-rule)=
## The Zero Power Rule

Ever wonder why raising any number to the zero power equals 1? Wonder no more! We take a simple example here

$$
\begin{aligned}
\dfrac{2^5}{2^3} & = \dfrac{2 \cdot 2 \cdot 2 \cdot 2 \cdot 2}{2 \cdot 2 \cdot 2} \\
2^{5 - 3} & = 2 \cdot 2 \\
2^2 & = 2 \cdot 2
\end{aligned}
$$

where on the left-hand side of the above equation, we have involved the rule involving division of powers

$$
\dfrac{x^a}{x^b} = x^{a - b}
$$

If we had to calculate the following, we would see that

$$
\begin{aligned}
\dfrac{2^5}{2^5} & = \dfrac{2 \cdot 2 \cdot 2 \cdot 2 \cdot 2}{2 \cdot 2 \cdot 2 \cdot 2 \cdot 2} \\
2^{5 - 5} & = 1 \\
2^0 & = 1 \cdot 2
\end{aligned}
$$

Extrapolating from this, if we have $a = b$, then we can state using the power rule for division

$$
\begin{aligned}
\dfrac{x^a}{x^b} & = x^{a - b} \\
\dfrac{x^a}{x^a} & = x^{a - a} \\
1 & = x^0
\end{aligned}
$$

Note that we have made no assumptions about $x$. It can be a real number or complex number. Raising any number to the zero power quals 1. This is sometimes referred to as the **zero power rule** or **zero exponent rule**.


(sec:dividing_by_zero)=
## Dividing By Zero is Hazardous To Your Health

One rule we've been told never to break is: **"don't divide by zero!"**

How can a basic, everyday number such as 0 combined with a basic mathematical operation such as division cause such problems? Normally, dividing by progressively smaller numbers gives you larger and larger answers. For example:

$$
\begin{aligned}
100 \div 1 & = 100 \\
100 \div 0.1 & = 1000 \\
100 \div 0.01 & = 10,000
\end{aligned}
$$

So as you divide by smaller and smaller numbers, your answer gets larger and larger. You may be tempted to extrapolate and say:

$$
x \div 0 = \infty
$$ (eq:div_by_zero_1)

However, we cannot make that conclusion. Or more precisely, making Eq. {ref}`eq:div_by_zero_1` a definition will cause problems. To see why that is the case, let's take a closer look at what we mean by "division". Say we have a number $x$ such that

$$
x \times y = z
$$

We then ask: "Is there a number we can multiply with $z$ to return our original $x$?" Yes, that number is is $1/y$, which is the **multiplicative inverse** of $y$ or the **reciprocal** of $y$. The product of any number and its multiplicative inverse is 1.

$$
y \times \dfrac{1}{y} = 1
$$

So one argument for why you can't divide b zero is as follows. The multiplicative inverse of zero is a number that satisfies

$$
0 \times \dfrac{1}{0} = 1
$$

However, we know that the product of any number times zero equals zero. Therefore this is an inconsistency and we conclude that zero has no multiplicative inverse.

Believe it or not, this doesn't conclusively demonstrate that you can't divide by zero! Mathematicians have "broken the rules" before. For example, when the square root of negative numbers was causing a problem, we defined $i$. So let's just define some quantity, $\gamma$, that is the multiplicative inverse of zero

$$
\textrm{Proposed definition:}\ \dfrac{1}{0} = \gamma
$$

It is possible that $\gamma$ is infinity or something else -- we don't know yet.

However, since we claim that this $\gamma$ is the multiplicative inverse of zero, it has the following property

$$
0 \times \gamma = 1
$$

But that would mean that

$$
(0 \times \gamma) + (0 \times \gamma) = 2
$$

By the distributive property

$$
\begin{aligned}
(0 \times \gamma) + (0 \times \gamma) & = 2 \\
(0 + 0) \times \gamma = 2 \\
0 \times \gamma = 2
\end{aligned}
$$

However, we have already defined $0 \times \gamma = 1$. Therefore, defining $\gamma$ as the multiplicative inverse of zero leads to a contradiction and we must conclude that zero has no multiplicative inverse.

<div style="text-align:right">§</div>


(sec:zero_to_zero_power)=
## $0^0$: What is It, Exactly?

It is surprising to me that there is still controversy about this. One would think that Euler would have resolved this... did he have something to say about this?

Consensus is that:

$$
0^0 = 1
$$


## Numbers and Scale

| Prefix | Symbol | Multiplying Factor |
|---|---|---|
| Yotta | Y | 1,000,000,000,000,000,000,000,000 = $10^{24}$ |
| Zetta | Z | 1,000,000,000,000,000,000,000 = $10^{21}$ |
| Exa | E | 1,000,000,000,000,000,000 = $10^{18}$ |
| Peta | P | 1,000,000,000,000,000 = $10^{15}$ |
| Tera | T | 1,000,000,000,000 = $10^{12}$ |
| Giga | G | 1,000,000,000 = $10^{9}$ |
| Mega | M | 1,000,000 = $10^{6}$ |
| Kilo | k | 1,000 = $10^{3}$ |
| Hecto | h | 100 = $10^{2}$ |
| Dega | da | 10 = $10^{1}$ |
| Deci | d | 0.1 = $10^{-1}$ |
| Centi | c | 0.01 = $10^{-2}$ |
| Milli | m | 0.001 = $10^{-3}$ |
| Micro | $\mu$ | 0.000001 = $10^{-6}$ |
| Nano | n | 0.000000001 = $10^{-9}$ |
| Piko | p | 0.000000000001 = $10^{-12}$ |
| Femto | f | 0.000000000000001 = $10^{-15}$ |
| Atto | a | 0.000000000000000001 = $10^{-18}$ |
| Zepto | z | 0.000000000000000000001 = $10^{-21}$ |
| Yocto | y | 0.000000000000000000000001 = $10^{-24}$ |

: Metric prefixes and their multiplying factors.


## The Concept of Infinity

:::{figure} No matter how big a number is.jpg
:alt: No matter how big a number is
:::


(sec:simple_things)=
## That's A Neat Trick

Did you know that $x$% of $y$ is equivalent to $y$% of $x$? You may have worked with percents and fractions for years, but never expressed things in this manner. It's straightforward to see if we just work through the math:

$$
\begin{aligned}
\textrm{$x$\% of $y$} & = \dfrac{x}{100} \times y \\
& = \dfrac{x}{100} \times \dfrac{y}{1}  \\
& = \dfrac{x \times y}{100 \times 1} \\
& = \dfrac{y \times x}{100} \\
& = \dfrac{y}{100} \times x \\
& = \textrm{$y$\% of $x$}
\end{aligned}
$$

Happy happy, joy joy!

## Notable Sections

We discuss an approximation of the square root using the Taylor Series expansion in Section XYZ. Easy as ABC. One two three. Testing. This is the most up-to-date version.
