## 4.3. range() 函数
* 如果你需要一串序列，内置函數`range()`會很方便:
```python
>>> range(10)
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```
* `range(10)`依據索引生成了一個有 10 個值的List，所生成的List不包括范围中的结束值。也可以讓`range`從另一個植開始，或者可以指定一個不同的等差數(甚至是負數，有時這也被稱為 “step”):
```python
>>> range(5, 10)
[5, 6, 7, 8, 9]
>>> range(0, 10, 3)
[0, 3, 6, 9]
>>> range(-10, -100, -30)
[-10, -40, -70]
```
* 需要重複List的索引可以如下所示结合使用`range()`和`len()`:
```python
>>> a = ['Mary', 'had', 'a', 'little', 'lamb']
>>> for i in range(len(a)):
... print i, a[i]
...
0 Mary
1 had
2 a
3 little
4 lamb
```
* 在這種情形下用`enumerate()`會更方便，請參考  Looping Techniques。

