1.10.3
```java
bool isMultiple(long n, long m)
{
	return n%m == 0;
}
```
1.10.4
```java
bool isEven(int i)
{
	bool isEven = true;
	while (i > 0)
	{
		isEven = !isEven;
		i--;
	}
	return isEven;
}
```
1.10.6
```java
int oddFactorial(int n)
{
	int val = 0;
	for (int i = n%2; i > 0; i--)
	{
		val += i*2;
	}
	return val;
}
```
2.7.9
```java
Read it.
Ship it.
Buy it.
Read it.
Box it.
Read it.
```
2.7.11
```java
//No, this assignment doesn't work
//Racer IsA Horse, and Equestrian IsA Horse, but Racer is not a Equestrian nor is the inverse true. 
//Technically speaking you could try and cast it but the result would fail at least at compile time
```
4.5.2
```java
8nlogn
2n^2

I don't think it ever is :/
n^2 > nlogn
and when n=0 
A = 0
and B = 0
and when n=1
A = 0
B = 2
and so like- the slope of A never allows it to beat B
this feels less extensive than a proof per-se though
```
4.5.8
```java
In "increasing" order:

2^10 is constant

2^logn goes here, I think it's technically logarithmic dispite looking weird but idk

4n is linear
as is 3n + 100 logn

4nlogn + 2n is nlogn
as is nlogn

n^2 + 10n is quadratic

n^3 is cubic

2^n is exponential
```
4.5.21
Tired of writing word problems in java format lol

Anywho, if you foil it out (but the 5th power yk)
you end up with basically:

n^5 + # n^4 + # n^3...
and everything but the n^5 is inconsequential to asymptotic analysis, thus the +1 in there doesn't really matter because n^5 is the greatest factor of the only significant element that being n because as n goes to infinity (n+1) == (n) and (n+1)^5 == (n)^5 as a property of working with infinity

Referencing the in-class definition:
$$
f(n) = (n+1)^5
$$
$$
= O(n)
$$
$$
(n+1)^5 \le cn
$$ let c = the sum of all the coefficients in the polynomial
so 32 if I'm not mistaken
$$
(n+1)^5 \le 32(n) = 32n
$$



4.5.22
so basically
$$
2^{n+1} = 2^n \cdot 2
$$
and 2 is a constant, and so then we have
$$
f(n) = 2^n is O(n)
$$
so O(n) is 2^n