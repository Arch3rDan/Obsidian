Pointers are a memory like any other variables, but they store in memory the location of another variable.

Most of the time we don't care too much about the pointer, we care what it's pointing to. 
	d reference operator

intPtr should point to something on the stack within [[Memory]]. Some address smaller than 0xbffffffff 

Segments of code are stored in the Code/Text Programs. 
Static segment is for global variables! 
	data + BSS
		data is init globals
		BSS is uninit globals

[[strcpy]] --strings are crummy -Dr Shomper
[[strcpy_s]] --not portable :(

In this class we use unsafe things so that we can learn how to use them and how to fix the issues
	like strcpy

All caps = [[constant]] --typical

[[Heap]]:
	The section of memory that is designated for unnamed variables
``` c++
new char[22]("Cedarville University")
```
puts the added bit into the heap. Using new to allocate to the heap. Vectors allocate to the heap. 

sizeof() works for creating strings of per bytes of the 
	vector is size, then a pointer

null pointers are expressed as x