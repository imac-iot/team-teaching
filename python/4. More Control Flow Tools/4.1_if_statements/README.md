##4.1. if 语句
if也許是最有名的語句。例如:
```python
>>> x = int(raw_input("Please enter an integer: "))
Please enter an integer: 42
>>> if x < 0:
... x = 0
... print 'Negative changed to zero'
... elif x == 0:
... print 'Zero'
... elif x == 1:
... print 'Single'
... else:
... print 'More'
...
More
```
可能會有零到多个`elif`部分，`else` 是可選的。`elif` 是 “else if” 的縮寫，這個可以有效避免過深的缩進。`if` ... `elif` ... `else` ... 這樣的寫法用來代替`switch` 或 `case` 語句。

