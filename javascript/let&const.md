# let 重点知识

### 循环中的let
当let用于`for`循环时，每一次循环，变量都会重新声明，JavaScript引擎内部会记住上一轮循环的值用来初始化本轮的变量
```javascript
var a = [];
for (var i = 0; i < 10; i++) {
  a[i] = function () {
    console.log(i);
  };
}
a[6](); // 10
```
另外，for循环还有一个特别之处，就是设置循环变量的那部分是一个父作用域，而循环体内部是一个单独的子作用域
```javascript
for (let i = 0; i < 3; i++) {
  let i = 'abc';
  console.log(i);
}
```
