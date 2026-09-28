Like an [[array]] in [[C]] but better.

They provide [[contiguous storage]] with a collection of like objects, which can be accessed randomly (see [[random access]]), passed as a parameter to a function, and returned from a function as well. 

``` C++
int m = 10;
vector<int> V1[m] = {1,2,3,4,5,6,7,8,9,10};
```
	initiallizes the vector V1 to the list of integer variables to the length of 10
``` C++
vector<int> V2;
```
	initiallizes the vector V2 but it isn't set to a size
``` C++
int V3[] = {1,2,3,4,5,6,7,8,9,10}
```
	initiallizes the array V3 and the size is 10
```C++
vector<int> V4[10];
```
	initiallizes the vector V4, at the size of 10, with unknown data elements within

VECTORS ARE AWESOME!
	They can be dynamically resized
		V2 = V1; assigns V2 with V1 but it RESIZES V2 to the length of V1