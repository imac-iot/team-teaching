#2.1. Invoking the Interpreter

Python的直譯器大多會裝在/usr/local/bin/python。如果放在/usr/local/bin/在你的Unix shell’s 會尋找讓它可以藉由命令去啟動。
```Bash
$ python
```

自從可以選擇直譯器的安裝位置，別的位置也是有可能的。檢查你的Python guru 或 system administrator。(E.g., /usr/local/python 是另一個可能的地方。)

在Windows中Python通常被安裝在C:\Python27或是你所選擇的地方。為了讓windows可以直接執行Python輸入指令在命令提示字元中
```Bash
$ set path=%path%;C:\python27
```
輸入結束字元(`Control-D`on Unix,`Control-Z` on Windows)在直譯器的主要提示中會離開並用`zero exit`的狀態，如過沒用試著輸入：`quit()`。

在直譯器中逐行編寫是非常複雜的。然而在Unix中直譯器安裝了 GNU readline 的函式庫，增加了更多精巧的交互編輯和歷史記錄功能。也許最快確認終端機使否能夠編輯的方法是輸入`Control-P`觀看第一個Python提示。如果它beeps，那終端機使是能夠編輯請查看附錄的 Interactive Input Editing and History Substitution for an introduction to the keys 如果甚麼是都沒發生或是顯示`^P`終端機編輯是不行的，你只能來刪除不對的字元。

在直譯器中操作就像在Unix shell：當呼叫標準輸入`tty`連接裝置它，讀取命令並直接執行你所呼叫的檔案參數或是標準輸入檔案。它讀取檔案並執行腳本。

第二種方法去執行是
```bash
$ python -c command [arg] 
```
這是執行命令的語句類似shell的`-c`操作，自從Python語句包含` `（空白）或是其他shell的特別字元，通常建議引用整體的命令在單引號內。

一些Python模組也是有用的script，這些可以用
```bash
$ python -m module [arg]
```
來調用。如果你有敘述他的完整名稱在檔案內那你就可以呼叫模組
 
當`script file`是使用的有時候進入 interactive mode是很有用的。它可以在我執行完script之前結束。

全部的指令操作在 Command line and environment 中。
