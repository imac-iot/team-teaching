# codingstyle

##分號
- 不要用分號作為一行的結束且不要用分號作為兩行之間的分隔。

##換行
- 一行不要超過80個字，除非其中有包含長URL的註解和很長的引入敘述。
- 不要使用反斜線來接續兩行。
- 確保換行被放在括弧(大、中、小)中，如有必要可以在表達式外額外新增括弧。
 
 ```python
 foo_bar(self, width, height, color='black', design=None,
          strName='foo',emphasis=None, highlight=0) 
 ```
 
 ```python
 if(width == 0 and height == 0 and
     color == 'red' and emphasis == 'strong')
 ```
 
- 當字串長度大於一行時，將其分行並使用括弧將整個字串包起來。
  
  ```python
  strLine=('This will build a very long long'
           'long long long long long long string')
 ```
 
- 放在註解中的URL連結盡量避免分行，如有需要，連結可以放在獨立的一行
  
  ```python
  #正確: 
  #See details at
  #https://google.github.io/styleguide/pyguide.html
  ```
  
  ```python
  #錯誤: 
  #See details 
  #http://www.example.com/us/developer/documentation/api/content/\
  #v2.0/csv_file_name_extension_full_specification.html
  ```
  
  注意以上案例的縮排情形。
  
## 括弧
盡量減少括弧的使用。回傳值和判斷式除非包含函式或是隱行否則避免使用。

```python
if foo:
    bar()
while intMonthear:
    intMonth = bar()
if intYear and intMonth:
    bar()
return foo
for (intYear, intMonth) in dict.items():
    print intMonth + intYear
```

##縮排

縮排距離為四格空白。請不用使用tab縮排，可以設定編輯器將tab鍵動作改成輸入四格空白。

```python
# 在括弧或是引號等定界符內，參數第一欄縱向對齊要有數值
foo = long_function_name(intYear,intMonth,
                         intDay, intHour)

# 在dictionary的定界符號內
foo = {
    long_dictionary_key: intYear +
                         intMonth,
}
# 第一行沒有包含參數，第二行要縮排四格空格
foo = long_function_name(
    intYear, intMonth,
    intDay, intHour)
```

##空白行
在開頭重要的Class以及函式宣告和後面的程式之間用兩空白行隔開，寫在程式裡的函式宣告只需要一空白行隔開。
```python
#空白1號
#空白2號
class example:
    def __init__(self):
        self.Year = 123
#空白3號
    def r456():
        return 456
#空白4號
#空白5號
print example.Year
```
##空格
在括弧內的參數不添加任何空格。

```python
spam(ham[1],{eggs: 2},[])
```

在冒號、分號、逗號前不要加空格，加在後面。

```python
if intMonth == 4:
    print intYear, intMonth
```

括弧的第一個參數前後均不加任何空白。

```python
spam(1)
dict['key'] = list[index]
```

運算元或是邏輯符號前後均加空格。當'='在參數表達裡，前後不加空格。

```python
intYearAddMonth = intYear + intMonth
intYear and intMonth
intYear == intMonth
intYear > intMonth
def complex(src=img,dst=frame)
```

不要使用空格對齊'#'後的註解或是'='後面的數值。
```python

intYear = 123 #intYear = 123
intMonth = 456 #intMonth = 123  
```

##Shebang Line(讓作業系統用哪個編譯器)
```python
#for python2.X
#!/usr/bin/env python
#for python3.X
#!/usr/bin/env python3
```

##註解

function的註解要做到看完助解就懂function的用法

```python
"""
function: sum
作用: 做加法
變數
    intValue1: 加數
    intValue2: 被加數
回傳
    intValue1 + intValue2的結果
"""
def sum(intValue1, intValue2):
    return (intValue1 + intValue2)
```

class的註解
```python
"""
class: Arithmetic(四則運算)
作用: 四則運算輸出
變數: intValue1: Int, 
      intValue2: Int
function:
    add
        function解釋
    subtraction
        function解釋
"""
class Arithmetic:
    def __init__(self, intValue1, intValue2):
      self.intValue1 = 0
      self.intValue2 = 0
      
    def add():
        return self.intValue1 + self.intValue2
    
    def subtraction():
        return self.intValue1 - self.intValue2
```
最後要在不明白或是棘手的地方下註解
```python
#a 的結果是多少我不知道
intValue = intValue1 = intValue2 = intValue3
```

##class
如果一個class沒有明確的繼承那就放入object
```python
class example(object):
    pass
    class innerclass(objece):
        pass
 
 
class add(intValue, intYear):
    pass
```

##String
選擇使用最好的方法來做
```python
StringWord1 = "hello"
StringWord2 = "world"
intValue = 9
#正確
StringMixWord = StringWord1 + StringWord2 
#錯誤
StringMixWord = "%s%s"%(StringWord1, StringWord2)
StringMixWord = "%s %s !!"%(StringWord1, StringWord2)
StringMixWord = "%s %s * %d"%((StringWord1, StringWord2, intValue)

```
如果要換行善用 `\n`
```python
print ("This is much nicer.\n"
       "Do it this way.\n")
```

##TODO
標住未完成的地方並且要告知要完成的結果
TODO(誰):未完成事項
final:目標
```python
#TODO(imac):it need some wing
#final:it will fly

```

##import
每一行只import一個
```python
import foo
from foo import bar
from foo.bar import baz
from foo.bar import Quux
from Foob import ar
```

##Statements  敘述
在測試的時候盡量用if else但是只用到if的話最好寫在同一行
```python
#正確
if test: print test

#錯誤
if foo: bar(foo)
else:   baz(foo)

try:               bar(foo)
except ValueError: baz(foo)

try:
    bar(foo)
except ValueError: baz(foo)
```


##Access Control  存取控制
如果有要存取class內的值利用 property 來做存取
在2.6版後才有的功能用來去代get ,set
```python
class Ball(object):
    def __init__(self, radius):
        self._radius = radius
    
    @property
    def isok():
        if self._radius = radius:
            return "OK"
        else
            return "False"
```

##Naming
基本上用大駝峰 ，在函數、模組、物件內前面加 `_`(一個底線)


| Type | Public | Internal |
| ---- | ------ | -------- |
| Packages |	lower_with_under |  	|
| Modules | lower_with_under | _lower_with_under |
| Classes |	CapWords | _CapWords |
| Exceptions | CapWords |
| Functions | lower_with_under() | _lower_with_under() |
| Global/Class Constants | CAPS_WITH_UNDER | _CAPS_WITH_UNDER|
| Global/Class Variables | lower_with_under | _lower_with_under |
| Instance Variables | lower_with_under | _lower_with_under (protected) or _lower_with_under (private) |
| Method Names | lower_with_under() | _lower_with_under() (protected) or _lower_with_under() (private) |
| Function/Method Parameters | lower_with_under |  |
| Local Variables | lower_with_under |

##Main
主要的程式要放在main()裡面
```python
def main():
      ...

if __name__ == '__main__':
    main()
```


