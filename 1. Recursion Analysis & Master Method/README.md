# Algorithms - Recursion  Analysis & Master Method

### Used Notations 

 - log(b, x) = log x to the base b.
## Recursion  Analysis
Recursive_Function(...):
 - base case 
 - recursive code
 - normal code 
> Running time T(N) =  Time of normal code  + T(recursive code) _also called recurrence relation_
> T(Base) = Time of base case

Steps: 

 1. Calculate Running Time T(N)
 2. Solve T(N) to get the order O(..) or Theta(..)
2.1. Iteration Method
2.2. Master Method 
2.3. Recursion Tree Method

```
Fib(N)
If (N == 1 or N == 2)		# base case
return 1
else						# normal code
return Fib(N-1) + Fib(N-2)	# recursive case
```
* T(N) = theta(1) + T(N – 1) + T(N – 2)
* T(Base) = theta(1)

## Master Method

#### NOTE:  *SUITABLE ONLY FOR RECURRENCES IN THE FOLLOWING FORM*
 - $$T(n) = a T(n/b)  + F(n^d)$$  
 - $$T(Base) = Theta(1)$$
 - $$a > 0$$
 - $$b > 1$$
 - $$d>=0$$
 
 ### Master Theorem 
$$F(n)$$ 
$$VS$$  
$$n^(log(b, a))$$

##### FORMAL CASES:
 - Case 1
 
	 If $$f(n) = O(n^ (log(b, a-ϵ))$$ then $$T(n) = Θ(n^(log(b, a)))$$
- Case 2
	If $$F(n) = Θ(n^(log(b, a)))$$ then $$T(n) = Θ(n^(log(b, a)) * log(b, n))$$
- Case 3
 If $$F(n) = Ω(n^(log (b, a+ϵ)))$$ AND $$a*F( n / b ) < c*F( n )$$ for large n 
then $$T(n) = Θ(F(n))$$

##### EASIER WAY:
- Case 1
 If $$d < log(b, a)$$ AND $$ a*F( n / b ) < c*F( n ), for - large - n$$
  then $$T(n) = Θ(n^(log(b, a))$$

- Case 2
	If $$d = log(b, a)$$ then $$T(n) = Θ(F(n) log(n))$$
- Case 3
 If $$d > log(b, a)$$ then $$T(n) = Θ(F(n))$$


### STEPS	:
 1. Check if the recurrence function T(n) meets the conditions.
 2. Get a, b. and d
 3. Find out which case is it.
 4. Identify the order
 
### Examples 
##### problem 1
- T(n) = 9T(n/3) + n
1. T(n) is in the right form for the master method.
2. Find a, b, and d
a = 9, b = 3, d = 1
3. Which case?
d ? log(b, a)
1 ? log(3, 9)
1 ? 2
1 < 2
Case 1
4.  T(n) = Θ(n^log(3, 9)
	T(n) = Θ(n^2)
	
##### problem 2
- T(n) = 3T(n/4) + n log n
1. T(n) is in the right form for the master method.
2. a = 3, b = 4,  d = 1
3. d ? log(b, a)
	1 ? log(4, 3)
	1 ? 0.7
	1 > 0.7 
 Case 3
 4. Check the condition: a f(n/b) ≤ c f(n) , 0<c<1
a * f(n/b) = 3(n/4) log (n/4) 
c * f(n) =  (3/4) n log n 
a*f(n/b) =  c*f(n) for c = 3/4
 5. T(n) = Θ(F(n))
 T(n) = Θ(n log(n)) 
##### problem 3
 
- T(n) = 4T(n/2) + n^2
1. T(n) is in the right form for the master method.
2. a = 4, b = 2, d = 2
3. d ? log(b, a)
	2 ? log(2, 4)
	2 ? 2
	2 = 2
	Case 2
4. T(n) = F(n) * log(n)
	T(n) = n^2 * log(n)

 
  
 
 
