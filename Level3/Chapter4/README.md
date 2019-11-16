## 扩展对象的功能性

#### 1、对象字面量语法扩展：

在ES6中，通过几种新的定义方法，让对象字面量变的更强大、更简洁。

- 属性初始值的简写：

  当一个对象的属性与本地变量同名时，不必再写冒号和值，简单地只写属性名即可。

```javascript
function Person(name,age){
    return {name,age};
}
let xiaoMing=Person("小名",23);
xiaoMing;// {name:"小名",age:23}
```

- 对象方法的简写：

  ES6也改进了为对象字面量定义方法的语法。

```javascript
//ES5 定义方法
var person={
    name:"Nicolas",
    sayName:function(){
       //....
    }
}
//ES6 定义方法
var person={
    name:"Nicolas",
    sayName(){
        //....
    }
}
```

> **Note**：简写方法可以使用super关键字。

- 可计算属性名：

  ES6中，可在对象字面量中使用可计算属性名称，其语法和引用对象实例的可计算属性名称相同，也是使用方括号。

```javascript
function Obj(property,value){
    return {
        [property]:value
    }
}
```

#### 2、新增方法：

ECMAScript其中的一个目标就是不在创建新的全局函数，也就是不在`Object.prototype`上创建新的方法，因此全局上的对象就会收到越来越多的对象方法。

- `Object.is()`：

  ES6引入`Object.is()`方法中如果两者参数类型相同且具有相同的值，则返回`true`。

```javascript
Object.is(5,5);//true
Object.is(5,"5");//false
```

- `Object.assign()`：

  混合（Mixin）是JavaScript中实现对象组合最流行的一种模式，在一个mixin方法中，一个对象接收来自另一个对象的属性和方法，这种操作其实是浅复制。

  `Object.assign()`方法可以接受任意数量的源对象，并按指定的顺序将属性复制到接收对象中。

```javascript
var receiver={};
Object.assign(receiver,{
    type:"js",
    name:"file.js"
},{
    create:"cowen"
});
receiver;//{create: "cowen",file: "main.js",type: "js"}
```

- `Object.setPrototypeOf()`：

  一直以来，JavaScript严重限制了原型的使用，其原型是在对象被创建时指定的，对象原型在实例化之后保持不变。直到ES5中增加了`Object.getPrototypeOf()`方法来返回任意指定对象的原型，但是仍然缺少对象在实例化后改变原型的标准方法。

  在ECMAScript6中增加了`Object.setPropertyOf()`方法来改变这一现状，通过这个方法可以改变任意指定对象的原型。

```javascript
let person={
    getGreeting(){
        return "Hello";
    }
}
let dog={
    getGreeting(){
        return "Woof";
    }
}
let xiaoming=Object.create(person);
Object.getProperty(xiaoming)===person;//true
xiaoming.getGreeting();//Hello

//将原型设置为dog
Object.setProperty(xiaoming,dog);
Object.getProperty(xiaoming)===dog;//true
xiaoming.getGreeting();//woof;
```


