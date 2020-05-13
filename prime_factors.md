# Sieve of Eratosthenes
* Complexity: O(n loglogn)
Code:
```c++
vector<bool> primes(n); //primes[k] stores if k is NOT prime. defaults to false

for (int i = 2; i < n; i++) {
	if (primes[i] == false) { //Encountered a prime
		//Mark all multiples as true
		for (int j = 2 * i, j < n; j += i) primes[j] = true;
	}
}
```

# Prime Factorization
* Complexity O(n loglogn logn) (I think)
Code:
```c++
//Modified Sieve of Eratosthenes
//factors[i] stores a vector containing prime factors (and their powers) of i.
//factors[40] = {{2, 3}, {5, 1}};
vector<vector<pair<ll, ll>>> factors(n); 

for (int i = 2; i < n; i++) {
	if (primes[i].empty()) { //Encountered a prime
		for (int j = i; j < n; j += i) { //Note we start from j = i instead of j = 2i
			int q = j;

			int power = 0;

			//Find the power of i in q
			while (q % i == 0) {
				q /= i;
				power++;
			}

			//Add the prime factor to the list of j
			factors[j].push_back(make_pair(i, power));
		} 
	}
}

```
