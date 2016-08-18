##3.1.3. 關於 Unicode

####從 Python2.0 起，程序員們有了一個新的用來存儲文本數據的類型：Unicode 對象。它可以用於存儲和維護 Unicode 數據 (參見 http://www.unicode.org/)，並且與現有的字串對像有良好的集成，必要時提供自動轉換。

####Unicode 的先進之處在於為每一種現代或古代使用的文字系統中出現的每一個字都提供了統一的序列號。之前，文字系統中的字只能有 256 種可能的順序。通過代碼頁分界映射。文本綁定到映射文字系統的代碼頁。這在軟件國際化的時候尤其麻煩(通常寫作 i18n —— 'i' + 18 個字符 + 'n')。 Unicode 解決了為所有的文字系統設置一個獨立代碼頁的難題。
####在 Python 中創建 Unicode 字串和創建普通的字串一樣簡單:
```Python
>>> u'Hello World !'
u'Hello World !'
```

####引號前的 'u' 表示這會創建一個 Unicode 字串。如果想要在字串中包含特殊字，可以使用 Python 的 Unicode-Escape。請看下面的例子:
```Python
>>> u'Hello\u0020World !'
u'Hello World !'
```

####轉碼序列 \u0020 表示在指定位置插入編碼為 0x0020 的 Unicode 字符(空格)。

####其他字就像 Unicode 編碼一樣被直接解釋為對應的編碼值。如果你有在許多西方國家使用的標準 Latin-1 編碼的字符串，你會發現編碼小於 256 的 Unicode 字和在 Latin-1 編碼中的一樣。

####特別的，和普通字串一樣，Unicode 字串也有原始模式。可以在引號前加 “ur”，Python 會採用 Raw-Unicode-Escape 編碼(譯者：原始 Unicode 轉義)。如果有前綴為 ‘u’ 的數值，它也只會顯示為 uXXXX:
```Python
>>> ur'Hello\u0020World !'
u'Hello World !'
>>> ur'Hello\\u0020World !'
u'Hello\\\\u0020World !'
```

####如果你需要大量輸入反斜線，原始模式非常有用，這在正則表達式中幾乎是必須的。

####作為這些編碼標準的一部分，Python 提供了基於已知編碼來創建 Unicode 字符串的整套方法。

####內置函數 unicode() 可以使用所有註冊的 Unicode 編碼(COders 和 DECoders)。眾所周知，Latin-1 ，ASCII ，UTF-8 和UTF-16 之類的編碼可以互相轉換(譯者：Latin-1 表示一個很小的拉丁語言符號集，與ASCII 基本一致，其實不能用來表示龐大的東方語言字符集)。後兩個是變長編碼，將每一個 Unicode 字存儲為一到多個字節。通常默認編碼為 ASCII，此編碼接受 0 到 127 這個範圍的編碼，否則報錯。將一個 Unicode 字串打印或寫入到文件中，或者使用 str() 轉換時，轉換操作以此為默認編碼:

```Python
>>> u"abc"
u'abc'
>>> str(u"abc")
'abc'
>>> u"盲枚眉"
u'\xe4\xf6\xfc'
>>> str(u"盲枚眉")
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
UnicodeEncodeError: 'ascii' codec can't encode characters in position 0-2: ordinal not in range(128)
```

####為了將一個 Unicode 字串轉換為一個使用特定編碼的 8 位字串，Unicode 對象提供一個 encode() 方法，它接受編碼名作為參數。編碼名應該小寫。 :
```Python
>>> u"盲枚眉".encode('utf-8')
'\xc3\xa4\xc3\xb6\xc3\xbc'
```

####如果有一個其他編碼的數據,希望可以從中生成一個 Unicode 字串,你可以使用 unicode 函數,它接受編碼名作為第二參數:
```Python
>>> unicode('\xc3\xa4\xc3\xb6\xc3\xbc', 'utf-8')
u'\xe4\xf6\xfc'
```
