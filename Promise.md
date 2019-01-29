Promise:承诺、许诺；

主要用于解决：异步回调问题。

传统方式：大量使用回调函数或者事件驱动解决异步问题。比如

```js
ajax(url,()=>{//获取token
    ajax(url,()=>{//获取用户信息
        ajax(url,()=>{//获取与用户相关的新闻

        });
    });
});
```

语法：

```js
//使用Promise，需先创建Promise对象
new Promise(function(resolve,reject){
    //resolve 成功时调用
    //reject 失败时调用
});
```

测试成功还是失败：

> promise.then(res=>{
>
> },err=>{
>
> });

```js
//如何使用，测试成功还是失败
let a = 10;
let promise = new Promise(function(resolve,reject){
    //resolve 成功时调用
    //reject 失败时调用
    if(a==10){
        resolve("成功了");
    }else{
        reject("失败了");
    }
});

//promise.then(success,faile);
promise.then(res=>{
    console.log(res);
},err=>{
    console.log(err);
});
```

使用promise.catch();来捕获错误。promise.catch(err=>{});

```js
//使用promise.catch()方法捕获错误
let a = 140;
let promise = new Promise(function(resolve,reject){
    //resolve 成功时调用
    //reject 失败时调用
    if(a==10){
        resolve("成功了");
    }else{
        reject("失败了");
    }
});

//    Promise.then(success,faile);
promise.then(res=>{
    console.log(res);
},err=>{
    console.log(err);//失败了
});

promise.catch(err=>{//相当于 then中的err项
    console.log(err);//失败了
}); 
```

promise方法连写形式（常用形式）。通常不写err方法，而是直接使用catch来捕获错误。

```js
//promise连写形式
let a = 140;
let promise = new Promise(function(resolve,reject){
    //resolve 成功时调用
    //reject 失败时调用
    if(a==10){
        resolve("成功了");
    }else{
        reject("失败了");
    }
});

//    Promise.then(success,faile);
promise.then(res=>{
    console.log(res);
}).catch(err=>{//通常直接使用catch捕获错误，而不是用err
    console.log(err);//失败了
}); 
```

------

promise.resolve();方法将现有的东西，转换成一个promise对象，resolve状态，成功状态。

promise.reject();方法将现有的东西，转换成一个promise对象，reject状态，失败状态。

```js
// let p1 = Promise.resolve("aaa");
// p1.then(res=>{
//     console.log(res);//aaa
// });

// 等价于
let p1 = new Promise(resolve=>{
    resolve("aaa");
});
p1.then(res=>{
    console.log(res);//aaa
});
```

------

Promise.all([p1,p2,p3]);批量处理promise对象。把promise打包，扔到一个数组里面，打包完还是以一个promise对象。具备promise所有的属性和方法。

```js
//可用于同时请求三个接口，然后得到返回值后统一处理
let p1 = Promise.resolve("aaa");
let p2 = Promise.resolve("bbb");
let p3 = Promise.resolve("ccc");
Promise.all([p1,p2,p3]).then(res=>{
    console.log(res);//["aaa", "bbb", "ccc"]
    let [res1,res2,res3] = res;
    console.log(res1,res2,res3);//aaa bbb ccc
});
```

> Promise.all();必须确保所有的promise对象为resolve状态，都是成功状态。否则报错

------

Promise.race([p1,p2,p3]);方法同all，与all不同的是，只要有一个promise对象是resolve状态就可以返回

```js
let p1 = Promise.resolve("aaa");
let p2 = Promise.reject("bbb");
let p3 = Promise.reject("ccc");
Promise.race([p1,p2,p3]).then(res=>{
	console.log(res);//aaa
});
```











