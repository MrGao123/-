## 继承
* 1. 原型链继承

```js
    aaaa
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
```

