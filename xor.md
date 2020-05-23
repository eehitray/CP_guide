# XOR
---

* Commutative: x ^ y = y ^ x
* Associative: x ^ (y ^ z) = (x ^ y) ^ z
* 0 is the identity: x ^ 0 = 0 ^ X = X
* x is the inverse: x ^ x = 0
* x ^ y can exceed x and y, but there is an upper limit: 2^(ceil(lb(z))) - 1, where ceil is the ceiling function, lb is the base 2 logarithm, z is max(x, y). In other words, the maximum number that can be formed is the number formed by all ones in the larger number. Eg: max value of 5 ^ k where k < 5 is 7 = (111 in binary) as 5 = (101 in binary).

# XOR of a subarray
---
* How do we efficiently find the XOR of a subarray?
```
ar = [2, 3, 1, 7, 3, 5]
Find XOR of all elements from left index l = 1 to right index r = 4. (0 based indices)
```
* Solution: ```XOR(l ... r) inclusive = pref(r) ^ pref(l - 1)```, where ```pref``` is the prefix XOR array (in pseudocode), where ```pref(0) = ar[0]```, ```pref(-1) = 0```.
* You can easily prove this using the commutativity and associativity of the XOR operation.
* In actual code, ```pref``` is an array of length ```n + 1```, and ```pref[0] = 0```. ```XOR(l ... r) = pref[r + 1] ^ pref[l]```, where ```l``` and ```r``` are 0 indexed, and ```r <= n - 1```.
```
vector<ll> pref(n + 1);
pref[0] = 0;

for (int i = 1; i <= n; i++) {
    pref[i] = pref[i - 1] ^ ar[i - 1];
}

cout << "Value of XOR of all elements in ar from index 1 to 3 is " << pref[4] ^ pref[1] << endl;
```