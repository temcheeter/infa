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

```python
def func(x, y, A):
    return ((x - 20 < A) and (10 - y < A)) or ((x+4)*y > 45)
for A in range(1, 100):
    if all([func(x, y, A) for x in range(1, 100) for y in range(1, 100)]):
        print(A)
        break
```

# F

```python
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

```python
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


def f(n):
    r = bin(n)[2:]
    r += r[-1]
    r += str(bin(n)[2:].count('1') % 2)
    r += str(r.count('1') % 2)
    return int(r, 2)

res = []

for n in range(8, 1000):
    R = f(n)
    if R > 105:
        res.append(R)

print(min(res))




def f(s):
    while '01' in s or '02' in s or '03' in s:
        s = s.replace('01', '302', 1)
        s = s.replace('02', '3103', 1)
        s = s.replace('03', '20')
    return s.count('1'), s.count('2'), s.count('3')


flag = 0
for a in range(1, 40):
    for b in range(1, 40):
        for c in range(1, 40):
            s = '0' + a * '1' + b * '2' + c * '3'
            x, y, z = f(s)
            if x == 30 and y == 39 and z == 42:
                flag = 1
                print(b)
        if flag:
            break
    if flag:
        break




def f(x, A):
    return (x & 29 != 0) <= ((x & 9 == 0) <= (x & A != 0))

for A in range(1, 1000):
    if all([f(x, A) for x in range(1, 5000)]):
        print(A)
        break





def f(n):
    r = bin(n)[2:]
    if sum([int(x) for x in r]) % 2 == 0:
        r = '10' + r[2:] + '0'
    else:
        r = '11' + r[2:] + '1'
    return int(r, 2)
res = []
for n in range(1000):
    numb = f(n)
    if numb >= 16:
        res.append(n)
print(min(res))





def f(s):
    while '33' in s or '31' in s or '21' in s:
        if '31' in s:
            s = s.replace('31','123',1)
        if '33' in s:
            s = s.replace('33','211',1)
        if '21' in s:
            s = s.replace('21', '1', 1)
    return sum([int(x) for x in s])


for n in range(1, 1000):
    s = '3' * 15 + '2' * 18 + '1' * n
    if f(s) > 24:
        print(n)
        break
