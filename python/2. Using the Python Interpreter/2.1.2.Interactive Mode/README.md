# 2.1.2. Interactive Mode
當tty讀取指令的時候直譯器會進入互動模式。在這個模式中，它的下一個指令會來自主要提示通常是`>>>`的符號。連續行的指令的預設提示是`...`。直譯器印出歡迎訊息是它的版本號和版權聲明。
```Python
python
Python 2.7 (#1, Feb 28 2010, 00:02:06)
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

連續行是需要輸入多行構造。下面是一個`if`的程式例子
Continuation lines are needed when entering a multi-line construct. As an example, take a look at this if statement:
```Pyhton
>>> the_world_is_flat = 1
>>> if the_world_is_flat:
...     print "Be careful not to fall off!"
...
Be careful not to fall off!
```
更多的互動模式請參照Interactive Mode的章節。