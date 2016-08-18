# 2.2.1. Source Code Encoding

有可能使用`ASCII`在Pyton的檔案中。最好放行一個特別的指令在`#!`的右邊去定義檔案的編碼：

```Python
# -*- coding: encoding -*-
```
在宣言後文件中的所有字符將被視為具有編碼的編碼，它會直接用 Uniconde 編寫成你所選的編碼。編碼列表可以在`Python Library`找到。

舉例:寫Unicode文字用ISO-8859-15編碼因為包含歐元符號的編碼所以可以用。當用ISO-8859-15的編碼來儲存後印出來的值是8364(對應於歐元符號的Unicode代碼)然後離開。
```Python
# -*- coding: iso-8859-15 -*-

currency = u"€"
print ord(currency)
```
如果你的編輯器支援UTF-8和UTF-8的順序標記(aka BOM)你可以用來代替宣告編碼方式。也可讓IDLE預設編碼UTF-8，注意這個方法不支援2.2版前的Python還有`#!`這行的指令它也看不懂(只能用在Unix)。

使用UTF-8(不論是直接用#!或是編譯器)是最多文字且常見的。使用非ASCII的文字在定義裡是不支援的，為了顯示所有的文字你的編輯器要是UTF-8而且要支援所有的文件內文字。
