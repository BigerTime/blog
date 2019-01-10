> ##### 原文地址：[https://github.com/lianxiaozhuang/blog](https://github.com/lianxiaozhuang/blog)
> ##### 转载请注明出处

### this指向问题
> 1、函数作为一个对象的属性值

```js
this.a = 20;
var test = {
 a: 40,
 init:function(){
    console.log(this.a);
 }
};

// this指向test;  
//40
test.init();

//p调用的;window.p；相当于把函数体拿到外面  this指向window
//20
var p = test.init();
p();

```
> 2.对象属性下函数内的函数
```js
this.a = 20;
var test = {
 a: 40,
 init:function(){
    function go() {
        console.log(this.a);
    }
   go();
 }
};


// 当前init没有宿主环境（详解如下）。this 指向window
//20
test.init()
```
> JS中，可以将对象分为“内部对象”、“宿主对象”和“自定义对象”三种。

> 1，内部对象  js中的内部对象包括Array、Boolean、Date、Function、Global、Math、Number、Object、RegExp、String以及各种错误类对象，包括Error、EvalError、RangeError、ReferenceError、SyntaxError和TypeError。其中Global和Math这两个对象又被称为“内置对象”，这两个对象在脚本程序初始化时被创建，不必实例化这两个对象。

> 2.宿主对象
> 宿主对象就是执行JS脚本的环境提供的对象。对于嵌入到网页中的JS来说，其宿主对象就是浏览器提供的对象，所以又称为浏览器对象，如IE、Firefox等浏览器提供的对象。不同的浏览器提供的宿主对象可能不同，即使提供的对象相同，其实现方式也大相径庭！这会带来浏览器兼容问题，增加开发难度。
>浏览器对象有很多，如Window和Document等等。

> 3.自定义对象
> 顾名思义，就是开发人员自己定义的对象。JS允许使用自定义对象，使JS应用及功能得到扩充



> 3、箭头函数

```js
this.a = 20;
var test = {
 a: 40,
 init:()=>{
  alert(this.a)
 }
};



test.init();
//打印 20
//因为箭头函数绑定其父的运行环境

```
> 4、构造函数
```js
function Ab(){
    this.color='red'
}
Ab.prototype.color = 'blue';
var p = new Ab();
console.log(p.color);// red
//实例中的this先找类；在找原型
```