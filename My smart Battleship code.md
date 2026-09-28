```C++
if (memory.mode == SEARCH)
   {
      int i = memory.fireDir;
      while (i <= 4 && checkResult != 0)
      {
         directionChecks(nextRow, nextCol, i, 1, memory);
         checkResult = basicMoveCheck(nextRow, nextCol, memory);
         i++;
      }
      memory.fireDir = i;
   }
```
