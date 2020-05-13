# Kadane's Algorithm

* Goal: find the maximum subarray sum.

`[5, 7, -2, 1] -> 12`

`[-1, -2, -3, -4] -> -1`

* O(n^2) - loop through all n^2 subarrays and sum them
* O(n) - Kadane's algorithm

* Idea:

Maintain variables mc (maximum current) and mg (maximum global). mc stores the maximum subarray sum such that the current element in iteration is the last element in the subarray. mg stores the maximum subarray sum so far. It can be shown that mc at any index i is either the element at i, or the element at i + mc at the previous iteration. Then, just update mg if mc > mg.

* Code:

```c++
ll mc = ar[0], mg = ar[0]; //Initially, the maximum current subarray sum and the maximum global subarray sum = the first element.

//Loop through every element after the first
for (int i = 1; i < n; i++) {
	mc = max(ar[i], mc + ar[i]); //mc at this iteration is either the current element, or the current element + mc at the previous stage
	mg = max(mg, mc); //Update mg if mc > mg
}

//mg now stores the maximum subarray sum.
```
