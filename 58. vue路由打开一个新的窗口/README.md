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







