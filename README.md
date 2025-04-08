# C

```python
def func(x, A):
    return (110 % A == 0) and (((x % 80 == 0) and (x % 75 == 0)) <= (x % A == 0))
for A in range(1000, 1, -1):
    if all([func(x, A) for x in range(1, 5000)]):
        print(A)
        break
```
# E

```
def func(x, y, A):
    return ((x - 20 < A) and (10 - y < A)) or ((x+4)*y > 45)
for A in range(1, 100):
    if all([func(x, y, A) for x in range(1, 100) for y in range(1, 100)]):
        print(A)
        break
```

# F

```
from functools import lru_cache
from sys import setrecursionlimit
setrecursionlimit(99999999)


@lru_cache()
def f(n):
    if n < 3:
        return n + 1
    if n % 2 == 0:
        return n + 2 * f(n + 2)
    return f(n - 2) + n - 2


counter = 0
for n in range(1, 1000, 2):
    if 99 < abs(f(n)) < 1000:
        counter += 1


print(counter)
```

# B (недоделанный)

```
def transfer(n):
    res = []
    while n:
        res.append(n % 7)
        n = n // 7
    return res

number = 103 * 7 ** 103 - 5 * 7 ** 57 + 98
res = transfer(number)
print(sum(res))
```
