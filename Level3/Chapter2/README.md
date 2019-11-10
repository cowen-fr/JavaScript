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

#### 2、正则补充：

块级声明用于声明在指定块的作用域之外无法访问的变量。块级作用域存在于：

- 函数内部：

- 块中（字符{和}之间的区域）：

#### 3、模板字面量：

`ES6`通过模板字面量的方式补充了`ES5`中字符串缺少的许多特性：

- 多行字符串：

- 基本的字符串格式化：

- HTML转义：

模板字面量使用``符号进行包裹定义。

```javascript
let str=`hello world`;
typeof str;//string
```

在模板字面量中，占位符是由一个左侧的${}符号组成的，中间包括任何类型的JavaScript表达式。

```javascript
let content="cowen",
    desc=`I am ${content}`;
```


