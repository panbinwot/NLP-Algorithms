# Algorithm used in NLP
Natural Language Processing|Dan Jurafsky, Christopher Manning


|#| Subject | Method | Code  | Complexity (Time, Space) |
|---|---|---|---|---|
|1|Find min Edit distance (Levenshtein) with Backtrace | DP   |[MinEditDistance.py](./MinEditDistance.py)  | O(nm), O(nm) |
|2|The Overlap Gene Dection | DP |edits from [MinEditDistance.py](./MinEditDistance.py)  |  O(nm), O(nm)  |
|3|Local Alignment Problem   | DP   |   |  O(nm), O(nm)   |

# Algorithms
1. Find Minimal Edit Distance (Leveshtein)
Problem: Given two string ```str1``` and ```str2```, find the min number of changes (insert, delete, substitute) needed for transferrin ```str1``` to ```str2``` 
Solution: Bottom Up. Find the result of sub-problem, that is finding minimal changes for a small part of ```str1``` and ```str2```.
<br>

```
def EditMinDistance(str1,str2):
    Init:
    D(i,0), D(0,j) = i, j
    for each i = 0...m
        for each j = 0...n
            a = 0 if str1[i] == str2[i] else 2
           # Delete, Insert, Substitute from str1 pov
            D(i,j) = min(D(i-1, j)+1, 
                        D(i, j-1)+1, 
                        D(i-1, j-1) +a)
            if insertion:
                prt(i,j) = LEFT
            elif deletion:
                prt(i,j) = DOWN
            else:
                prt(i,j) = DIAG 
    return D(m,n)
```
Followup: Weighted Min Edit Distance
Add cost term when computing the distance in the subproblems
See more about Needleman-Wunsch Algorithm

2. The Overlap Gene Detection
Problem: Find the overlap 
```
For all i, j
    F(i,0), F(0,j) = 0, 0

F_opt = max(max_i F(i,N)
            max_j F(M, j)) 
```

3.  Local Alignment Problem
Find tow substring whose similarity is maximum.
```
def SmithWaterman(str1, str2):
    F(i,0) = 0
    F(0,j) = 0

    F(i,j) =  max(0,
                F(i-1, j) - d,
                F(i, j-1) - d,
                F(i - 1, j - 1) + s(x_i, y_j)
                )
    return F_opt = max_ij F(i,j)
```

4.  

