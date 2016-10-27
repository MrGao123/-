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
    Person.prototype = o;
    var p = new Person();
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

