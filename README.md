# Primality-tests
- *my_gcd(a, N)* returns the great common divisor of **a** and **N** using the iterative Euclidean Algorithm. *my_inverse(a, N)* returns the modulo **N** inverse of **a** using Extended Euclidean Algorithm such that **a*u0** is congurent to 1 modulo **N**. Theoretically, they have the same complexity **O(bitsize(a) * bitsize(N))**. 

**proof:** the naive Euclidean division algorithm of **a** by **b** performs **O(bitsize (b) * (bitsize (a) - bitsize (b)))**   arithmetic operations. Note that *my_gcd* makes several Euclidean divisions. All bitsizes of divisors are less than the bitsize of **b** and all sizes of dividends are less than the bitsize of **a** 
So the arithmetic complexity of my_gcd is bounded by **O(bitsize (a) * bitsize (b))**.

Using *complexity_test()* we approve this by the following figure. 

<p align="center">
  <img src="https://github.com/ily-R/Primality-tests/blob/master/gcd_inverse.png?raw=true" alt="capture reconstruction"/>
</p>

- The pertubations can be explained by the fact that for a certain bitsize, the gcd between **a** and **b** may be too close to **b** and thus the computation time will be small. On the other hand, if it is far from **b** then the computation time will be significant relatively. However, on average, we have always a linearity with respect to **bitsize (a) * bitsize (b)**.

- *carmichael_1(N)* and *carmichael_2(N)* generate a list of Carmichael numbers less than an input limit **N**. a charmicael number **n** is a composite number such that for every **a** coprime with **n** **a^n - n** divides **n**. The two functions follow different approaches.

**note:** we implement **a^n mod n** using the function *my_expo_mod()*

- *carmichael_1(N):*
1- pick a number **n** by iterating through all the odd numbers from 3 to N-1.
2- check if **n** is a 100% prime number by using the naive test implemented in *first_test(n)*.
3- if **n** is prime, go to **1**. if **n** is not prime then for all **a** such that **1 < a < n** and **a** is coprime with **n** we check if **a^n - n** divides **n**.if not, go to **1**. if so, test with the next **a**. if it holds for all **a** then **n** is a carmichael number. 

- *carmichael_2(N):*
1- pick a number **n** by iterating through all the odd numbers from 3 to N-1.
2- for all **a** such that **1 < a < n** and **a** is coprime with **n** we check if **a^n - n** divides **n**.if not, go to **1**. if so, test with the next **a**. if it holds for all **a** go to **3**
3- check if **n** is a 100% prime number by using the naive test implemented in *first_test(n)*. if so, go to **1**. Else,then **n** is a carmichael number.

Using *carmichael_complexity()* We see in the figure below that *carmichael_1* is way faster than *carmichael_2*. For instance, within 4 seconds *carmichael_1* can process about 10^5 numbers compared with 3000 using *carmichael_2*

<p align="center">
  <img src="https://github.com/ily-R/Primality-tests/blob/master/pt1.png?raw=true" alt="capture reconstruction"/>
</p>

Here's a clear version of the red graph.

<p align="center">
  <img src="https://github.com/ily-R/Primality-tests/blob/master/pt2.png?raw=true" alt="capture reconstruction"/>
</p>

- *gen_carmichael_1(n):* generates all the carmichael numbers less than **n** with 3 prime factors.

- Suppose we have a carmichael number **n** with 3 prime factors **pqr** with **p < q < r**, then if we fix **p** the list of the corresponding carmichaels is finite.

**proof:** We just need to find an upper bound for **r**. Using Korselt Theoreme we know that **(r-1)** divides **(n - 1)** So:

r - 1 | pqr - 1 = pq (r – 1 + 1) - 1 = pq (r - 1) + pq - 1 which means that  r - 1 | pq - 1.

Similarly: q - 1 | pr - 1. whcih means there exist h and k such that: pq - 1 = h (r - 1) and k (q - 1) = pr - 1. 

Developing the above we can prove that: (hk- p²) (q-1) = (p+h) (p-1)

as h < p we see that q < 2p(p-1) + 1

and from r - 1 | pq - 1 we know that r < pq . So using the above upper bound of q we find r < p (2p (p – 1) + 1).

- *gen_carmichael_p(p):* get as input the prime factor **p** and generate all the carmichael **n** such that **n = pqr** and                r < p (2p (p – 1) + 1).

- *fermat_test_success_probability(max_number)* tests the Failure probability of the fermat test implemented in *fermat_test(n, k)* by increasing the value of *k* .
<p align="center">
  <img src="https://github.com/ily-R/Primality-tests/blob/master/pt3.png.png?raw=true" alt="capture reconstruction"/>
</p>

- *miller_rabin_test_success_probability(max_number)* tests the Failure probability of the miller_rabin_test implemented in *miller_rabin_test(n, k)* by increasing the value of *k* .
 
<p align="center">
  <img src="https://github.com/ily-R/Primality-tests/blob/master/pt5.png?raw=true" alt="capture reconstruction"/>
</p>

In both tests the more we increase *k* the more we indorse the correctness of the test's result. 
