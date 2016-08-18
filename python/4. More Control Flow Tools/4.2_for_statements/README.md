##4.2. for 语句
Python 中的 for 跟 C 或 Pascal 有些不同。通常的循環可能会依據一个等差數值步進過程(如 Pascal)，或由用戶来ˇ定一的重複步骤和中止條件(如 C )，Python 的 for 語句依據任意序列(list 或 String )中的子項，按它们在序列中的顺序来進行重複。例如(沒有雙關語意):
```python
>>> # Measure some strings:
... words = ['cat', 'window', 'defenestrate']
>>> for w in words:
... print w, len(w)
...
cat 3
window 6
defenestrate 12
```
如果你需要在迴圈內修改排序(例如：複製選擇的項目)，建議你複製一份再修改因為它不會製作副本。使用分割就可以很方便地做到:
```python
>>> for w in words[:]: # Loop over a slice copy of the entire list.
... if len(w) > 6:
... words.insert(0, w)
...
>>> words
['defenestrate', 'cat', 'window', 'defenestrate']
```
