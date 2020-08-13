Question: https://stackoverflow.com/questions/63387019/merge-two-lists-alternatively-n-elements/63387244

```python
list_1 = [1,2,3,4,5,6]
list_2 = ['a','b','c','d','e','f']
```

and `n`is given.

merge then based on `n` as below:

- if n = 1: `result = [1,'a',2,'b',3,'c',4,'d',5,'e',6,'f']`
- if n = 2: `result = [1,2,'a','b',3,4,'c','d',5,6,'e','f']`
- if n = 3: `result = [1,2,3,'a','b','c',4,5,6,'d','e','f']`
- if n = 4: `result = [1,2,3,4,'a','b','c','d',5,6,'e','f']`

....

Possible solution with `itertools`:

```python
import itertools

def merge(l1, l2, n):
    return [j for i in zip(itertools.zip_longest(*[iter(l1)]*n), itertools.zip_longest(*[iter(l2)]*n)) for j in itertools.chain.from_iterable(i) if j]

list_1 = [1, 2, 3, 4, 5, 6]

list_2 = ["a", "b", "c", "d", "e", "f"]

print(merge(list_1, list_2, 2))
# [1, 2, 'a', 'b', 3, 4, 'c', 'd', 5, 6, 'e', 'f']
print(merge(list_1, list_2, 3))
# [1, 2, 3, 'a', 'b', 'c', 4, 5, 6, 'd', 'e', 'f']
print(merge(list_1, list_2, 4))
# [1, 2, 3, 4, 'a', 'b', 'c', 'd', 5, 6, 'e', 'f']
```

