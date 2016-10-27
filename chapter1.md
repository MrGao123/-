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
    
    //1.3 利用混入式继承给**原型对象**添加属性和方法
    function Stu(){}
    Stu.prototype.extend = function (obj) {
        for ( var key in obj ) {
            this[key] = obj[key]; 
        }
    }
    var o1 = {name:'zs',age:10};
    Stu.prototype.extend(o1);
    var stu = new Stu();
    console.log(stu);    
```

* 2.混入式继承（给**对象自身**添加属性的混入式继承方法）

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
* 3. 经典继承:Object.create

```js
    //经典继承的兼容实现
    function create(obj) {
        if (Object.create) {
            return Object.create(obj);
        }
        var F = function(){};
        F.prototype = {};
        return new F();
    }
    
```

