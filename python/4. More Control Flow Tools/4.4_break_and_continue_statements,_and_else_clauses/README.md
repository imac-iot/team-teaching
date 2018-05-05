## 4.4. break and continue Statements, and else Clauses on Loops

* break 語句和 C 中的類似，用於跳出最近的一级`for`或`while`循环。

* Loop可以有一个`else`子句；在Loop終止之後執行(對於 for) 后或执行条件为 false (对于 while) 时执行，但循环被 break 中止的情况下不会执行。以下搜索素数的示例程序演示了这个子句:
```python
>>> for n in range(2, 10):
... for x in range(2, n):
... if n % x == 0:
... print n, 'equals', x, '*', n/x
... break
... else:
... # loop fell through without finding a factor
... print n, 'is a prime number'
...
2 is a prime number
3 is a prime number
4 equals 2 * 2
5 is a prime number
6 equals 2 * 3
7 is a prime number
8 equals 2 * 4
9 equals 3 * 3
```


* 與循环一起使用時，else 子句與 try 语句的 else 子句比与 if 语句的具有更多的共同点：try 语句的 else 子句在未出現異常時運行，循環的 else 子句在未出現 break 時運行。

* continue 语句是从 C 中借鉴来的，它表示循环继续执行下一次迭代:
```bash
>>> for num in range(2, 10):
... if num % 2 == 0:
... print "Found an even number", num
... continue
... print "Found a number", num
Found an even number 2
Found a number 3
Found an even number 4
Found a number 5
Found an even number 6
Found a number 7
Found an even number 8
Found a number 9
```
