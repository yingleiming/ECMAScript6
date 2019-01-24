**函数参数的扩展**

默认参数和基本用法

```javascript
function fn(name,age=17){
    console.log(name+","+age);
}    
fn("tomy",18);//tomy,18
fn("jack");//jack,17 使用默认参数
fn("hanmm","");//hanmm,  空字符串也是有效的值传递
fn("liu",undefined);//liu,17 使用默认参数
fn("zhu",null);//zhu,null null值被认为是有效的值传递
```

注意：使用函数默认参数时，不允许有同名参数。

```javascript
//不报错
function fn(name,name){
    console.log(name,name);
}    
fn("tomy","tomy");//tomy tomy

//Uncaught SyntaxError: Duplicate parameter name not allowed in this context
function fn(name,name,age="17"){
    console.log(name+","+age);
}    
fn("tomy");//参数名称不允许重复
```

只有在未传递参数，或者参数为undefined时，才会使用默认参数。

```js
function fn(name,age=17){
    console.log(name+","+age);
}    
fn("jack");//jack,17 使用默认参数
fn("liu",undefined);//liu,17 使用默认参数
```

null值被认为是有效的值传递

```js
function fn(name,age=17){
    console.log(name+","+age);
}    
fn("zhu",null);//zhu,null null值被认为是有效的值传递
```

函数参数默认值存在暂时性死区，在函数默认值表达式中，还未初始化赋值的参数值无法作为其他参数的默认值。

```js
function fn(x,y=x){
    console.log(x,y);
}
fn(2);//2 2 
function fn(x=y){
    console.log(x);
}
fn();//Uncaught ReferenceError: y is not defined 此时y并未初始化和赋值
```


