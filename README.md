# Primality-tests
*my_gcd(a, N)* returns the great common divisor of **a** and **N** using the iterative Euclidean Algorithm. *my_inverse(a, N)* returns the modulo **N** inverse of **a** using Extended Euclidean Algorithm such that **a*u0** is congurent to 1 modulo **N**. Theoretically, they have the same complexity **O(bitsize(a) * bitsize(N))**. 
**proof:** the naive Euclidean division algorithm of **a** by **b** performs **O(bitsize (b) * (bitsize (a) - bitsize (b)))**   arithmetic operations. Note that *my_gcd* makes several Euclidean divisions. All bitsizes of divisors are less than the bitsize of **b** and all sizes of dividends are less than the bitsize of **a** 
So the arithmetic complexity of my_gcd is bounded by **O(bitsize (a) * bitsize (b))**.
Using *complexity_test()* we approve this by the following figure. 

![](https://github.com/ilyasAr/Primality-tests/blob/master/gcd_inverse.png)

The pertubations can be explained by the fact that for a certain bitsize, the gcd between **a** and **b** may be too close to **b** and thus the computation time will be small. On the other hand, if it is far from **b** then the computation time will be significant relatively. However, on average, we have always a linearity with respect to bitsize (a) * bitsize (b).


*my_expo_mod(g, n, N):*

*first_test(n):*

*carmichael_1(N):*

*carmichael_2(N):*

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
