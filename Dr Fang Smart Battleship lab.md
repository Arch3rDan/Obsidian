```C++
string move = “”;
move = move + (char)(‘A’ + row);
if (col < 9)
	Move = move + (char)(‘1’ + col)
else
	Move = move + “10”
return move;
```

If else not if chain
	If hunt, else if, search, else random

USE == not =!!!!

Check using debug what the current output is

If mode == SEARCH && memry.far

Keep the number of fired distances!

find:
	isAMiss
	isAHit
	hitShip
	computerPlayRost = playMove

Beginning search pattern! 

10 x 10 heatmap matrix weight

STAGES
	Random
	Random + destroy
	Search algorithm
	Heatmapping

/home/faculty/knoerr/cs1210/public/HW10
/home/students/2029/comito/HW10

``` C++
if memry.mode == RANDOM && ISAHIT(result){
    memry.mode = SEARCH;
    memry.hitRow = row;
    memry.hitCol = col;
	memry.hitShip = ???(result);
}
```

0 - 30H
1 - 31H
2 - 32H