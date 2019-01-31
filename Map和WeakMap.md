类似于json，但是json的键（key）只能是字符串，而Map的键可以是任意类型

使用方式：

```js
let map = new Map();
map.set(key,val);
```

示例：

```js
let map = new Map();
map.set("a","aaa");
console.log(map);//Map(1) {"a" => "aaa"}
```

把json做为key

```js
let map = new Map();
let json = {
    a:1,
    b:2
}
map.set(json,"aaa");
console.log(map);//Map(1) {{…} => "aaa"}
```

也可以json作为values

```js
let map = new Map();
let json = {
    a:1,
    b:2
}
map.set("a",json);
console.log(map);//Map(1) {"a" => {…}}
```

获取Map中的值map.get()：

```js
let map = new Map();
let json = {
    a:1,
    b:2
}
map.set(json,"aaa");
console.log(map.get(json));//aaa

let map = new Map();
let json = {
    a:1,
    b:2
}
map.set("a",json);
console.log(map.get("a"));//{a: 1, b: 2}
```

删除map.delete(key);

```js
let map = new Map();
let json = {
    a:1,
    b:2
}
map.set("a",json);
map.delete("a");
console.log(map.get("a"));//undefined
```

判断里面有没有 map.has(key);

```js
let map = new Map();
let json = {
    a:1,
    b:2
}
map.set("a",json);

console.log(map.has("a"));//true
```

清空 map.clear();

```js
let map = new Map();
let json = {
    a:1,
    b:2
}
map.set("a",json);
map.clear("a")
console.log(map);//Map(0) {}
```

循环：

```js
for(let [key,val] of map){//默认是entries()
    
}
for(let key of map.keys()){
    
}
for(let val of map.values()){
    
}
for(let [k,v] of map.entries()){
    
}
```

使用forEach()

```js
let map = new Map();
let json = {
    a:1,
    b:2
};
map.set("a",json);
map.forEach((val,key)=>{
    console.log(val,key);
});//{a: 1, b: 2} "a"
```

