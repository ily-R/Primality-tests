# Primality-tests
*my_gcd(a, N)* returns the great common divisor of **a** and **N** using the iterative Euclidean Algorithm. *my_inverse(a, N)* returns the modulo **N** inverse of **a** using Extended Euclidean Algorithm such that **a*u0** is congurent to 1 modulo **N**. Theoretically, they have the same complexity **O(bitsize(a) * bitsize(N))**. 

**proof:** the naive Euclidean division algorithm of **a** by **b** performs **O(bitsize (b) * (bitsize (a) - bitsize (b)))**   arithmetic operations. Note that *my_gcd* makes several Euclidean divisions. All bitsizes of divisors are less than the bitsize of **b** and all sizes of dividends are less than the bitsize of **a** 
So the arithmetic complexity of my_gcd is bounded by **O(bitsize (a) * bitsize (b))**.

Using *complexity_test()* we approve this by the following figure. 

![](https://github.com/ilyasAr/Primality-tests/blob/master/gcd_inverse.png)

The pertubations can be explained by the fact that for a certain bitsize, the gcd between **a** and **b** may be too close to **b** and thus the computation time will be small. On the other hand, if it is far from **b** then the computation time will be significant relatively. However, on average, we have always a linearity with respect to **bitsize (a) * bitsize (b)**.

*carmichael_1(N)* and *carmichael_2(N)* generate a list of Carmichael numbers less than an input limit **N**. a charmicael number **n** is a composite number such that for every **a** coprime with **n** **a^n - n** divides **n**. The two functions follow different approaches.

*carmichael_1(N):*
1- pick a number **n** by iterating through all the odd numbers from 3 to N-1.
2- check if **n** is 100% prime by using the naive test implemented in *first_test(n)*.
3- if **n** is prime, go to **1**. if **n** is not prime then we check for all **a** such that **1 < a < n**. We check if **a** is coprime with **n** using *my_gcd(a, n)* then we check if **a^n - n** divides **n**.if not go to **1**. if so, test with next **a**. if it holds for all **a** then **n** is a carmichael number. 

*my_expo_mod(g, n, N):*



*carmichael_3(N, primes):*

*carmichael_complexity():*

*gen_carmichael_1(n):*

*gen_carmichael_2(n):*

*gen_carmichael_complexity():*

*gen_carmichael_p(p):*

*fermat_test(n, k):*

*tester_fermat_test():*

*fermat_test_success_probability(max_number):*

*miller_rabin_test(n, k):*

*tester_millier_test():*

*miller_rabin_test_success_probability(max_number):*

*gen_rsa(t):*
