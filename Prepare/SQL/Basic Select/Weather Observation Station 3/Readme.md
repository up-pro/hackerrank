# Weather Observation Station 3

## Problem
![alt text](image.png)
![alt text](image-1.png)

## Solution
```
SELECT DISTINCT CITY
FROM STATION
WHERE MOD(ID, 2) = 0;
```