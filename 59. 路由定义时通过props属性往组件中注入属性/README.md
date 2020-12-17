
路由定义：

```
import { LOGIN_PAGE_NAME, ROOT_PAGE_NAME } from '@config/index.js';
import { BasicLayout, Basic4Layout } from '@packages/views/index.js';

{
	path: '/',
    name: ROOT_PAGE_NAME,
    component: BasicLayout,
    // 控制布局组件的展示
    props: {
      renderNavMenu: false,
      renderDropColumnDown: false,
      renderDropDown: false
    },
    children: [
	
	]
}
```

BasicLayout 组件接收 props 参数

```
<script>
  export default {
  
   props: {
		// 渲染 top-view.vue
		renderTopView: {
		  type: Boolean,
		  default: true
		},
		// 渲染 base-nav-menu 菜单组件
		renderNavMenu: {
		  type: Boolean,
		  default: true
		},
		// 是否渲染 消息 图标和下拉面板
		renderDropDown: {
		  type: Boolean,
		  default: true
		}
   }

  }
</script>
```


路由定时时通过 props 属性往组件的 props 对象中注入数据。











