## 字符串和正则表达式

#### 1、编码支持：

在函数作用域或全局作用域中通过关键词var声明的变量，无论实际上是在哪里声明的，都会被当成在当前作用域顶部声明的变量。

```javascript
function getValue(condition){
    if(condition){

        var result="blue";

        return result;

    }else{

        //此处可以访问到变量result  其值为undefined

        return null;

    }

    //此处也可以访问到变量result 其值为undefined

}
```

上述代码其实经过浏览器解析后，会存在变量提升的状况，真正的解析为：

```javascript
function getValue(condition){
    var result;
    if(condition){
        result="blue";
        return result;        
    }else{
        return null;
    }
}
```

#### 2、块级声明：

块级声明用于声明在指定块的作用域之外无法访问的变量。块级作用域存在于：

- 函数内部：

- 块中（字符{和}之间的区域）：

#### 3、`let`声明：

`let`声明的用法和`var`相同，用`let`代替`var`来声明变量，就可以把变量的作用域限制在当前代码块中。

`let`声明只能声明一次，禁止重复声明。

```javascript
var count=30;
let count=40;
// Uncaught SyntaxError: Identifier 'count' has already been declared
```

#### 4、`const`声明：

使用`const`声明的是常量，其值一旦被设定后不能被再次修改，而且每一个通过`const`声明的变量必须进行初始化。

```javascript
const pi=3.14;
pi=314;
// Uncaught TypeError: Assignment to constant variable.
```

必须进行初始化：

```javascript
const pi;
pi=3.14;
// Uncaught SyntaxError: Missing initializer in const declaration
```

`const`不允许修改绑定，但是允许修改值，这就意味着可以修改`const`定义的对象的属性值。

#### 5、循环中的块作用域：

在循环函数中使用`var`定义变量，循环结束后，仍然能访问到该变量。

```javascript
for(var i=0;i<10;i++){
    console.log(i);// 0 ... 9    
}
console.log(i);//10
```

#### 6、全局块作用域：

`let`和`const`与`var`的另外一个区别是它们在全局作用域中的行为。当`var` 被用于全局作用域时，它会创建一个新的全局变量作为全局对象（浏览器中的`window`对象）的属性。这就意味着`var`很有可能会无意中覆盖一个已经存在的全局属性。

```javascript
var _name1="cowen";
let _name2="zheng";

window._name1;//cowen

window._name2;//undefined
```
