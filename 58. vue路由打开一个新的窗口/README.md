vue2.0以后router.go和router.push就不支持新窗口打开的属性了，现在用一种新的方式router.resolve：


```
let routeData = this.$router.resolve({
  path: "/about",
  query: {
    name:'lei',
    age: 18,
    phoneNum:12345678901 
  }
});
window.open(routeData.href, '_blank');
```


解析指定的路由

会返回这个路由的信息，和在路由钩子函数中的 to 是一样的，但是我可以通过 `resolve` 来获取而不用去跳转才能获取到 to 的信息

```
let routeData = this.$router.resolve({
  path: "/about"
});

console.info(routeData);

```

