### 1.   Object.prototype.hasOwnProperty()
>
* 对象自己的属性(实例属性，非原型属性)
* 用于判断某个值或者对象是否属于某个对象的自己的属性；返回 true 或者 false
``` js
	var obj = {
			a:"123"
		}
	console.log(obj.hasOwnProperty("a")) // true
	console.log(Object.prototype.hasOwnProperty.call(obj,"a"))//true
	console.log(Object.prototype.hasOwnProperty("toString"))//true
	
	console.log(obj.hasOwnProperty("f")) // flase
	console.log(Object.prototype.hasOwnProperty.call(obj,"toString"))//false
	
````
> 另外这个方法有个特例
     对于 自定义的对象名写成hasOwnProperty；在判断的时候会出问题

``` js
var foo = {
    hasOwnProperty: function() {
        return false;
    },
    bar: 'Here be dragons'
};

foo.hasOwnProperty('bar'); // 始终返回 false
```
