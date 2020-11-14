
# Algorithms - Recursion Trees


### Used Notations 

 - log(b, x) = log x to the base b 
 - sum(a, b, f) = summation from a to b on function f
## Recursion trees 
 - Why use recursive trees? 
	1. Not all the problems are solvable using the easy method (master method) , so trees against the iterative method the recursive trees is easier.
	2. Visual Representation.
	3. Easy to trace.
	4. Can be used to solve <b>ANY</b> recurrence equation.
	5. Suitable for recurrences with <b>MANY</b> recursive terms.
	
## Steps 
 - Draw the tree for at least three levels.
 - Calculate number of levels.
	  - Find the pattern.
	  - When will the tree stop branching ? at the base case.
	  - solve the equation to find L as function of N _usually_.
 - Calculate complexity of each level.
	 - The complexity of one the first level is usually the F(N) _the non recursive part_.
	 - Find the complexity pattern for all the levels.
	 - Is the pattern related to N? Does it change in each level? 
 - Calculate complexity of LAST level.
	 - Complexity/Last_level = number of nodes in the last level * base case complexity
	 - Balanced or not? if Not Balanced then #nodes = 1, because if it ended somewhere there will be no other branches at the same level.
	 - Balanced or not? if Balanced then how many node will be at level L? _Usually #last_nodes = #second level nodes ^ L_.
 - Total = sum of all levels.

### Examples
#### problem 1
- T(N) = 2 T(N / 2) + Log(N!) , 	T(1) = c
	Note: Log(N!) = Θ(N Log(N))
1. Draw at least three levels of the tree
at level T(i) beside the recursive call how many operations are performed?
so after ignoring the recursive call "2 T(N / 2)" what is left over? Log(N!).

       Recursive calls 						   			Tree									Row sum

	   T(n)												N log(N)								N log N
	   T(n/2)							N log(N)/2						N log(N)/2	    	    N log N/2
	   T(n/4)				N log(N)/4		   N log(N)/4		N log(N)/4		N logN/4        N log N/4
	   T(n/2^i)		N log(N)/ 2 ^i		......													N log (N/2^i)
										
2. Calculate number of levels 
Balanced or not? Balanced.
- Find a general formula 
* N, N/2, N/4, N/8, .... ((1/2)^L )* N  , where L is number of levels
* the code stops at the base case which is at n = 1
* (1/2)^L * N = 1  
   N = 2^L
>  L = Log(2, N)
3.  Calculate complexity of each level
 N Log(2, N/2^i)
= N Log(2, N) - N Log(2, 2^i) 
= N Log(2, N) - N x i
>  complexity/level = N ( Log(2, N) - i )
4. Calculate complexity of LAST level
 Balanced or not ? Balanced, then the last level will have 2^L leaves.
why ? let's trace the tree
at level 0 there was 2^0 = 1 nodes.
at level 1 there were 2^1 = 2 nodes.
 at level 2 there were 2^2 = 4 nodes.
 therefore 
 at level L there will be 2^L nodes.
 from step 2: L = Log(2, N)
Complexity/last level = 2^L
 = 2 ^ Log(2, N)
> Complexity/last level = N

5. Calculate the total 
total = sum of all levels
Total = complexity/last level  + sum(complexity/level) for L - 1
-- why L-1 ? because we took out the last level complexity.
Total = N + sum(0, L-1, N Log N - N * i) 
 = N + sum(0, L-1, N Log N)  - sum(0, L-1,  N * i)
 = N + N Log N * (L-1)  - N * sum(0, L-1,   i)
= N + (Log N - 1) N Log N - N  * sum(0,Log(2, N)-1, i)
=   N + (Log N - 1) N Log N - N ((log(2, N) -1 ) Log(2, N)) / 2)
= N + N * (log(2, N) -1 ) Log(2, N)) / 2
> Total = 	Θ(N (Log(2, N)^2))			

#### problem 2

- T(n) = 2 T(n / 2) + c n
1. Draw three levels tree

	   Recursive calls 						   			Tree					    	  Row sum

	   T(n)												cn							    	cn
	   T(n/2)							cn/2								cn/2			cn
	   T(n/4)					cn/4		   cn/4				cn/4				cn/4	cn
	   T(n/2^i)		cn		......													    	cn

2.  Calculate number of levels 
2^L = n 
> L =log n

3. Calculate Complexity/level
> Complexity/level = cn
4. Complexity/last level = 2^L
 = 2 ^ Log(2, n)
> Complexity/last level = n
5. Total
Total = sum of all levels
= last level + rest of the levels
= n + sum(0, L, n)
= n + sum(0, log(2, n), n)
= n + n*log(2, n)
> Total =  Θ(n log(2, n))

# Algorithms - Recursion Trees


### Used Notations 

 - log(b, x) = log x to the base b 
 - sum(a, b, f) = summation from a to b on function f
## Recursion trees 
 - Why use recursive trees? 
	1. Not all the problems are solvable using the easy method (master method) , so trees against the iterative method the recursive trees is easier.
	2. Visual Representation.
	3. Easy to trace.
	4. Can be used to solve <b>ANY</b> recurrence equation.
	5. Suitable for recurrences with <b>MANY</b> recursive terms.
	
## Steps 
 - Draw the tree for at least three levels.
 - Calculate number of levels.
	  - Find the pattern.
	  - When will the tree stop branching ? at the base case.
	  - solve the equation to find L as function of N _usually_.
 - Calculate complexity of each level.
	 - The complexity of one the first level is usually the F(N) _the non recursive part_.
	 - Find the complexity pattern for all the levels.
	 - Is the pattern related to N? Does it change in each level? 
 - Calculate complexity of LAST level.
	 - Complexity/Last_level = number of nodes in the last level * base case complexity
	 - Balanced or not? if Not Balanced then #nodes = 1, because if it ended somewhere there will be no other branches at the same level.
	 - Balanced or not? if Balanced then how many node will be at level L? _Usually #last_nodes = #second level nodes ^ L_.
 - Total = sum of all levels.

### Examples
#### problem 1
- T(N) = 2 T(N / 2) + Log(N!) , 	T(1) = c
	Note: Log(N!) = Θ(N Log(N))
1. Draw at least three levels of the tree
at level T(i) beside the recursive call how many operations are performed?
so after ignoring the recursive call "2 T(N / 2)" what is left over? Log(N!).

       Recursive calls 						   			Tree									Row sum

	   T(n)												N log(N)								N log N
	   T(n/2)							N log(N)/2						N log(N)/2	    	    N log N/2
	   T(n/4)				N log(N)/4		   N log(N)/4		N log(N)/4		N logN/4        N log N/4
	   T(n/2^i)		N log(N)/ 2 ^i		......													N log (N/2^i)
										
2. Calculate number of levels 
Balanced or not? Balanced.
- Find a general formula 
* N, N/2, N/4, N/8, .... ((1/2)^L )* N  , where L is number of levels
* the code stops at the base case which is at n = 1
* (1/2)^L * N = 1  
   N = 2^L
>  L = Log(2, N)
3.  Calculate complexity of each level
 N Log(2, N/2^i)
= N Log(2, N) - N Log(2, 2^i) 
= N Log(2, N) - N x i
>  complexity/level = N ( Log(2, N) - i )
4. Calculate complexity of LAST level
 Balanced or not ? Balanced, then the last level will have 2^L leaves.
why ? let's trace the tree
at level 0 there was 2^0 = 1 nodes.
at level 1 there were 2^1 = 2 nodes.
 at level 2 there were 2^2 = 4 nodes.
 therefore 
 at level L there will be 2^L nodes.
 from step 2: L = Log(2, N)
Complexity/last level = 2^L
 = 2 ^ Log(2, N)
> Complexity/last level = N

5. Calculate the total 
total = sum of all levels
Total = complexity/last level  + sum(complexity/level) for L - 1
-- why L-1 ? because we took out the last level complexity.
Total = N + sum(0, L-1, N Log N - N * i) 
 = N + sum(0, L-1, N Log N)  - sum(0, L-1,  N * i)
 = N + N Log N * (L-1)  - N * sum(0, L-1,   i)
= N + (Log N - 1) N Log N - N  * sum(0,Log(2, N)-1, i)
=   N + (Log N - 1) N Log N - N ((log(2, N) -1 ) Log(2, N)) / 2)
= N + N * (log(2, N) -1 ) Log(2, N)) / 2
> Total = 	Θ(N (Log(2, N)^2))			

#### problem 2

- T(n) = 2 T(n / 2) + c n
1. Draw three levels tree

	   Recursive calls 						   			Tree					    	  Row sum

	   T(n)												cn							    	cn
	   T(n/2)							cn/2								cn/2			cn
	   T(n/4)					cn/4		   cn/4				cn/4				cn/4	cn
	   T(n/2^i)		cn		......													    	cn

2.  Calculate number of levels 
2^L = n 
> L =log n

3. Calculate Complexity/level
> Complexity/level = cn
4. Complexity/last level = 2^L
 = 2 ^ Log(2, n)
> Complexity/last level = n
5. Total
Total = sum of all levels
= last level + rest of the levels
= n + sum(0, L, n)
= n + sum(0, log(2, n), n)
= n + n*log(2, n)
> Total =  Θ(n log(2, n))
