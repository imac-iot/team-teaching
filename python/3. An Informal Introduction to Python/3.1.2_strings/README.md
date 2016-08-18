##3.1.2. String字串
####相比數值，Python也提供了可以通過幾種不同的方式表示的字串。
####它們可以用單引號('...')或雙引號("...")去標示。
####而在字串中有單引號('...')或雙引號("...")在前面加上\

```Python
>>> 'spam eggs'  # single quotes
'spam eggs'

>>> 'doesn\'t'  # use \' to escape the single quote...
"doesn't"

>>> "doesn't"  # ...or use double quotes instead
"doesn't"

>>> '"Yes," he said.'
'"Yes," he said.'

>>> "\"Yes,\" he said."
'"Yes," he said.'

>>> '"Isn\'t," she said.'
'"Isn\'t," she said.'
```
####在交互式解釋器(interactive interpreter)中，輸出的字串會用引號引起來，特殊字符會用反斜杠 (\) 轉義。雖然可能和輸入看上去不太一樣，但是兩個字符串是相等的。如果字符串中只有單引號而沒有雙引號，就用雙引號引用，否則用單引號引用。再強調一下，print 語句可以生成可讀性更好的輸出:

```Python
>>> '"Isn\'t," she said.'
'"Isn\'t," she said.'

>>> print '"Isn\'t," she said.'
"Isn't," she said.

>>> s = 'First line.\nSecond line.'  # \n means newline
>>> s  # without print, \n is included in the output
'First line.\nSecond line.'

>>> print s  # with print, \n produces a new line
First line.
Second line.
```
####如果你前面带有 \ 的字符被當作特殊字符，你可以使用 原始字串，方法是在第一个引号前面加上一个 r:
```Python
>>> print 'C:\som

e\name'  # here \n means newline!
C:\some
ame

>>> print r'C:\some\name'  # note the r before the quote
C:\some\name
```
####字符串文本能夠分成多行。一種方法是使用三引號："""...""" 或者 '''...'''。行尾換行符會被自動包含到字符串中，但是可以在行尾加上 \ 來避免這個行為。下面的示例： 可以使用反斜杠為行結尾的連續字符串，它表示下一行在邏輯上是本行的後續內容:

```Python
print """\
Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to
"""
```
####将生成以下输出（注意，没有開始的第一行）:
```Python
Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to
```

####字串可以由+操作符連接(黏到一起)，可以由*表示重複:
```Python
>>> # 3 times 'un', followed by 'ium'
>>> 3 * 'un' + 'ium'
'unununium'
```

####相鄰的兩個字串文本自動連接在一起。:
```Python
>>> 'Py' 'thon'
'Python'
```

####它只用於兩個字串文本，不能用於字串表達式:
```Python
>>> prefix = 'Py'
>>> prefix 'thon'  # can't concatenate a variable and a string literal
  ...
SyntaxError: invalid syntax
>>> ('un' * 3) 'ium'
  ...
SyntaxError: invalid syntax
```

####如果你想連接多個變量或者連接一个變量和一个字串文本，使用 +:
```Python
>>> prefix + 'thon'
'Python'
```

####這個功能在你想切分很長的字串的时候特别有用:
```Python
>>> text = ('Put several strings within parentheses '
            'to have them joined together.')
>>> text
'Put several strings within parentheses to have them joined together.'
```

####字串也可以被截取(檢索)。類似於 C ，字串的第一个字索引为 0 。Python没有單獨的字類型；一个字就是一个簡單的長度為1的字串。:
```Python
>>> word = 'Python'
>>> word[0]  # character in position 0
'P'
>>> word[5]  # character in position 5
'n'
```

####索引也可以是負数，這將導致從右邊開始計算。例如:
```Python
>>> word[-1]  # last character
'n'
>>> word[-2]  # second-last character
'o'
>>> word[-6]
'P'

```

####請注意 -0 實際上就是 0，所以它不會導致從右邊開始計算。

####除了索引，還支持 切片。索引用於獲得單個字，切片 讓你獲得一个子字串:
```Python
>>> word[0:2]  # characters from position 0 (included) to 2 (excluded)
'Py'
>>> word[2:5]  # characters from position 2 (included) to 5 (excluded)
'tho'
```

####注意，包含起始的字，不包含末尾的字。這使得 s[:i] + s[i:] 永遠等於 s:
```Python
>>> word[:2] + word[2:]
'Python'
>>> word[:4] + word[4:]
'Python'
```

####切片的索引有非常有用的默認值；省略的第一个索引默認為零，省略的第二个索引默認為切片的字符串的大小。:
```Python
>>> word[:2]  # character from the beginning to position 2 (excluded)
'Py'
>>> word[4:]  # characters from position 4 (included) to the end
'on'
>>> word[-2:] # characters from the second-last (included) to the end
'on'
```

####有個辦法可以很容易地記住切片的工作方式：切片时的索引是在两个字之間 。左邊第一个字的索引為 0，而長度為 n 的字串其最后一个字的右界索引为 n。例如:
```Python
+---+---+---+---+---+---+
 | P | y | t | h | o | n |
 +---+---+---+---+---+---+
 0   1   2   3   4   5   6
-6  -5  -4  -3  -2  -1   無

```

####文本中的第一行數字给出字符串中的索引點 0...6。第二行给出相應的負索引。切片是從 i 到 j 两個數值標示的邊界之間的所有字。

####對於非負索引，如果上下都在邊界内，切片長度就是两个索引之差。例如，word[1:3] 是 2 。

####試圖使用太大的索引會導致錯誤:
```Python
>>> word[42]  # the word only has 6 characters
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: string index out of range
```

####Python 能够優雅地處理那些没有意義的切片索引：一个過大的索引值(即下標值大於字串實際度)將被字串實際長度所代替，當上邊界比下邊界大时(即切片左值大於右值)就返回空字串:
```Python
>>> word[4:42]
'on'
>>> word[42:]
''
```

####Python字串不可以被更改 — 它们是 不可變 的。因此，赋值给字串索引的位置会會導致錯誤:
```Python
>>> word[0] = 'J'
  ...
TypeError: 'str' object does not support item assignment
>>> word[2:] = 'py'
  ...
TypeError: 'str' object does not support item assignment
```

####如果你需要一个不同的字串，你應該創建一个新的:
```Python
>>> 'J' + word[1:]
'Jython'
>>> word[:2] + 'py'
'Pypy'
```

####内置函數 len() 返回字串長度:
```Python
>>> s = 'supercalifragilisticexpialidocious'
>>> len(s)
34
```
