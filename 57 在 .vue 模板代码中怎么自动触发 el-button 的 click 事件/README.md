```
<el-button ref="bbb">click 触发</el-button>
```

nativeOn 的形式：

如果是 el-button ，那么自动触发 click 事件 `this.$refs.bbb.$el.click();`

on的实行：

`this.$refs.bbb.$emit('click');`









