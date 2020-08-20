

https://www.jianshu.com/p/f8a3f7057ea3

这样我们就可以在使用css-module的同时对部分不好进行修改的antd组件的样式进行修改了
即使你使用的是less这些也是一样的处理

```
.normal {
  .select {
    :global .ant-select-selection.ant-select-selection--single {
      background: red;
    }
  }
}
```
