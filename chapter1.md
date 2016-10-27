## 继承
* 1. 原型式链继承

```js
    var o = {
        name: 'zs',
        age: 10,
        sayHi: function(){
              console.log(this.name+"----"+this.age)
        }
    }
    function Person() {}
    //1.1 利用覆盖原型对象
    Person.prototype = o;
    Person.prototype.constructor = Person;
    var p = new Person();    
    //1.2 利用对象的动态特性
    p.name = "lisi";
    //这一句是给p对象自身添加了一个name属性，不会修改原型中的name属性
    console.log(p);
```

* 2.混入式继承

```js
    var o1 = {
        name: 'zs',
        age: 10
    }   
    var o2 = {
        sayHi: function() {
            console.log('hello world')
        }
    }
    function extend(obj) {
        for (var key in obj) {
            this[key] = obj[key];
        }
    }
    var o3 = {};
    o3.extend = extend;
    o3.extend(o1);
    o3.extend(o2);
    console.log(o3);
```

