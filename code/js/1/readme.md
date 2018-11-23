### 函数提升
> 当函数名和变量名一样的时候，变量没有赋值，函数优先级高

```js
function a(){}
var a;
console.log(a)//function a(){}

````

```js

function a(){}
var a=1;
console.log(a)//1

````
