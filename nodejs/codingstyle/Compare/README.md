# 流程控制
- 比較

```javascript
//一律採用3個等號做嚴謹比較
if (i === 20){
  console.log('相等');
}
```
- if判斷式

```javascript
/**
 * 1.如果是判斷同一個值 不可在做巢狀if
 * 2.在if後面都必須加上空格
 */

//正確
if (val < 0){
  //...
}else if (val > 0){
  //...
}else {
  //...
}
```
