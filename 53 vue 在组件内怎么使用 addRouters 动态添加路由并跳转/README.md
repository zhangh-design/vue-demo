53 vue 在组件内怎么使用 addRouters 动态添加路由并跳转

组件内添加路由：

```
<template>
  <div>个人中心<el-button size="small" @click="onOpenUserPage">路由跳转</el-button></div>
</template>

<script>
export default {
  methods: {
    onOpenUserPage() {
      console.info(this.$route)
      this.$router.addRoutes([{ path: '/ioio', name: 'ioio', component: () => import('../needs/index.vue') }])
      this.$router.push('ioio')
    }
  }
}
</script>

<style>

</style>
```


路由钩子中添加路由：

```
// beforeEach
const routerBeforeEachFunc = function (to, from, next) {
  NProgress.start()
  if ('title' in to.meta && WINDOW_TITLE_UPDATE) {
    document.title = to.meta.title
  }
  console.info(to)
  // 白名单直接跳转
  if (ROUTER_WHITE_LIST.includes(to.name)) {
    NProgress.done()
    return next()
  }
  console.info('abc', router);
  if (router.$rootRouter.children.length === 0) {
    router.$rootRouter.children.push(personal)
    // console.info(personal)
    router.addRoutes(router.options.routes)
    /* router.addRoutes([
      {
        path: 'personal',
        name: 'personal',
        meta: { title: '个人中心' },
        component: () => import('../../views/personal/index.vue')
      }
    ]) */
    console.info('111');
    // router.push('/personal') 不要在钩子函数中使用push就行跳转，不然跳到那个路由页面在点击浏览器回退箭头是不会回退到上一个路由页面的
    next({ path: 'personal' }) // 必须要使用 next 就行跳转，其实这样等用于网页刷新就行这个判断，加载动态路由，会立马再次next 也就是在进一次 beforeEach 钩子
    return
  }
  console.info('111 ', router.options.routes, to, from)

  // 加载菜单，生成路由
  // store.dispatch('platform/getRoleMenus')
  next()
}
```







