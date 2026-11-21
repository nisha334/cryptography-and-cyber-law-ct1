# cryptography-and-cyber-law-ct1
<WritingBlock id="63821" variant="document"># 📘 Number Theory, Cryptography and Prime Numbers

Student Name: Fatema Islam Nisha
Student ID: IT22033
Course Project: Number Theory and Cryptography
Programming Language: Python 3
Platform: Google Colab

📑 Table of Contents
Introduction to Number Theory

Divisibility, Factors and Multiples

Greatest Common Divisor (GCD)

Naive GCD

Euclidean Algorithm

Extended Euclidean Algorithm

Least Common Multiple (LCM)

Diophantine Equations

Modular Arithmetic

Modular Multiplicative Inverse

Chinese Remainder Theorem

Fast Modular Exponentiation

Fermat's Little Theorem

Euler's Totient Function

Euler's Theorem

Cryptography and RSA

Prime Numbers

Primality Testing

Primitive Roots and Multiplicative Order

Divisor Functions and Antiprimes

Fundamental Theorem of Arithmetic

Practical Exercises

Conclusion

References

1. Introduction to Number Theory
Number Theory is an important branch of mathematics that deals with integers and their mathematical properties. It includes divisibility, prime numbers, GCD, LCM, modular arithmetic and integer equations.

Number theory has many applications in computer science, particularly in cryptography, data security and algorithm design.

Types of Numbers
Number Type

Description

Example

Natural

Counting numbers

1, 2, 3

Integer

Positive, negative and zero

-2, 0, 5

Even

Divisible by 2

2, 4, 8

Odd

Not divisible by 2

1, 3, 7

Prime

Exactly two positive divisors

2, 3, 5

Composite

More than two positive divisors

4, 6, 9

Python Implementation
Output:


text
Number: 29
Even: False
Odd: True
Square: 841
2. Divisibility, Factors and Multiples
An integer a divides another integer b if there exists an integer k such that:

$$b = ak$$

The notation is:

$$a \mid b$$

For example:

$$4 \mid 20$$

Because:

$$20 = 4 \times 5$$

Python Implementation

python
def find_factors(n):
    return [i for i in range(1, n + 1) if n % i == 0]

print(find_factors(24))
Output:


text
[1, 2, 3, 4, 6, 8, 12, 24]
3. Greatest Common Divisor (GCD)
The Greatest Common Divisor is the largest positive integer that divides two integers without leaving a remainder.

It is represented by:

$$d = \gcd(a,b)$$

Example:

$$\gcd(24,16)=8$$

3.1 Naive GCD Algorithm
This approach checks possible divisors until it finds the largest common divisor.


python
def gcd_naive(a, b):
    a, b = abs(a), abs(b)

    if a == 0 and b == 0:
        raise ValueError("GCD is undefined for (0, 0)")

    for i in range(min(a, b), 0, -1):
        if a % i == 0 and b % i == 0:
            return i

    return max(a, b)

print(gcd_naive(24, 16))
Output:


text
8
3.2 Euclidean Algorithm
Euclid's algorithm calculates GCD by repeatedly replacing two numbers with the smaller number and their remainder.

$$\gcd(a,b)=\gcd(b,a \bmod b)$$


python
def gcd_euclid(a, b):
    a, b = abs(a), abs(b)

    if a == 0 and b == 0:
        raise ValueError("GCD is undefined for (0, 0)")

    while b != 0:
        a, b = b, a % b

    return a

print(gcd_euclid(24, 16))
print(gcd_euclid(10, 6))
Output:


text
8
2
3.3 Extended Euclidean Algorithm
The Extended Euclidean Algorithm calculates the GCD and also finds two integer coefficients x and y.

Bézout's Identity:

$$ax+by=\gcd(a,b)$$


python
def extended_gcd(a, b):
    if b == 0:
        return abs(a), (1 if a >= 0 else -1), 0

    d, x1, y1 = extended_gcd(b, a % b)

    x = y1
    y = x1 - (a // b) * y1

    return d, x, y

d, x, y = extended_gcd(10, 6)

print("GCD:", d)
print("x:", x)
print("y:", y)
print("Verification:", 10*x + 6*y)
Output:


text
GCD: 2
x: -1
y: 2
Verification: 2
4. Least Common Multiple (LCM)
The Least Common Multiple is the smallest positive integer divisible by both given integers.

The mathematical relationship is:

$$LCM(a,b)=\frac
