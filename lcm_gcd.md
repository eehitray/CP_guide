# LCM

* Lowest common multiple of a set of numbers.
* lcm(a, b) = ab/GCD(a, b) [two numbers only]
* lcm(a_1, a_2, ..., a_n) = lcm(lcm(a_1, a_2, ..., a_p), lcm(a_[p + 1], a_[p + 2], ... a_n)) for some 1 < p < n. In other words, the lcm of a set of many numebrs can be split into the lcm of smaller subsets of numbers.
* When looking at the prime factorization of numbers, each unique prime is raised to the maximum power present among all the numbers. For example:

```
40 = 2^3 x 5
50 = 2 x 5^2
33 = 11 x 3
```

The LCM is thus: ```2^3 x 3 x 5^2 x 11```.

# GCD
* Greatest common denominator of a set of numbers.
* gcd(a, b) = ab/LCM(a, b) [two numbers only]
* gcd(a_1, a_2, ..., a_n) = gcd(gcd(a_1, a_2, ..., a_p), gcd(a_[p + 1], a_[p + 2], ... a_n)) for some 1 < p < n. In other words, the gcd of a set of many numebrs can be split into the gcd of smaller subsets of numbers.
* When looking at the prime factorization of numbers, each unique prime is raised to the minimum power present among all the numbers. For example:

```
40 = 2^3 x 5
50 = 2 x 5^2
66 = 11 x 3 x 2
```

The GCD is thus: ```2^1 x 3^0 x 5^0 x 11^0```.
* Bezout's lemma: all linear combinations of x and y are divisible by GCD(x, y). In other words, ax + by = k * GCD(x, y).

# Euclidean Algorithm (basic)
* Finds the GCD of two numbers.

```c++
ll gcd(ll a, ll b) {
	if (a == 0) return b;
	return gcd(b % a, a);
}```

# Extended Euclidean Algorithm
* Finds the GCD of two numbers a and b, as well as Bezout coefficients x and y such that ax + by = GCD(a, b).

```c++
ll gcd(ll a, ll b, ll& x, ll& y) {
	if (a == 0) {
		x = 0;
		y = 1;
		return b;
	}

	ll x1, y1;
	ll gcd_ab = gcd(b % a, a, x1, y1);

	x = y1 - (b/a) * x1;
	y = x1;

	return gcd_ab;
}

//Call as:
ll gcd_nums, x, y;

gcd_nums = gcd(a, b, x, y);

//gcd_nums = GCD(a, b)
//x, y are such that ax + by = GCD(a, b)
```
