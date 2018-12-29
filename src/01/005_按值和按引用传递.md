### this指向问题
> 1、谁调用，this指向谁，没调用就指向window。

```js
this.a = 20;
var test = {
 a: 40,
 init:()=> {
    console.log(this.a);
    function go() {
        // this.a = 60;
        console.log(this.a);
    }
    go.prototype.a = 50;
    return go;
 }
};
//var p = test.init();
//p();
new(test.init())();

```