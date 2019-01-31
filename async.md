读取文件:

## 1.使用promise读取文件

```js
//promise.js
//引入fs模块
const fs = require('fs');

//简单封装readFile
const readFile = function (fileName) {
    return new Promise((resolve, reject) => {
        fs.readFile(fileName,(err,data)=>{
            if(err)reject(err);
            resolve(data);
        });
    })
};

//promise
readFile("data/a.txt").then(res=>{
    console.log(res.toString());//a.txt中的内容
    return readFile("data/b.txt");
}).then(res=>{
   console.log(res.toString());//b.txt中的内容
   return readFile("data/c.txt");
}).then(res=>{
    console.log(res.toString());//c.txt中的内容
});
//注意：新建data文件夹里面包含三个文件 a.txt b.txt c.txt ；在当前文件中使用node 运行promise.js
```

## 1.使用generator读取文件(略)

## 1.使用async读取文件(推荐使用)

```js
//引入fs模块
const fs = require('fs');

//简单封装readFile
const readFile = function (fileName) {
    return new Promise((resolve, reject) => {
        fs.readFile(fileName,(err,data)=>{
            if(err)reject(err);
            resolve(data);
        });
    })
};

//async 表示异步：这个函数里面有异步的任务；await:表示后面的结果需要等待
async function fn() {
    let f1 = await readFile("data/a.txt");
    console.log(f1.toString());
    let f2 = await readFile("data/b.txt");
    console.log(f2.toString());
    let f3= await readFile("data/c.txt");
    console.log(f3.toString());
}

fn();//调用
```

async特点：

1. await只能放在async函数中
2. 相比generator语义化更强
3. await后面可以是promise对象，也可以是数字、字符串、布尔值等
4. async函数返回的是一个promise对象
5. 只要await语句后面Promise状态变成reject,那么整个async函数就会中断执行

验证async函数返回的是一个promise对象：

```js
async function fn() {
    return "welcome"
}
console.log(fn());//Promise 返回的是一个Promise对象
```

