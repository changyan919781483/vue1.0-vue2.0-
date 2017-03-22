1. 引入路由文件vue-router  
```import VueRouter from "vue-router"```
2. 使用路由
```Vue.use(VueRouter)```
3. 定义（路由）组件
```
//可以用import引入进来
const Foo = { template: '<div>foo</div>' }
const Bar = { template: '<div>bar</div>' }
```
4. 定义路由
```
const routes = [
{ path: '/', redirect: '/foo' },//路由重定向
  { path: '/foo', component: Foo },
  { path: '/bar', component: Bar }
]
```
5. 创建 router 实例，然后传 `routes` 配置
```
const router = new VueRouter({
  routes // （缩写）相当于 routes: routes
})
```
6. 创建和挂载根实例
```
const app = new Vue({
  router:router,
  render: h=>h(App)
}).$mount("#app")
```
#### 路由嵌套
```
const User = {
  template: `
    <div class="user">
      <h2>User {{ $route.params.id }}</h2>
      <router-view></router-view>
    </div>
  `
}

const router = new VueRouter({
  routes: [
    { path: '/user/:id', component: User,
      children: [
        {
          // 当 /user/:id/profile 匹配成功，
          // UserProfile 会被渲染在 User 的 <router-view> 中
          path: 'profile',
          component: UserProfile
        },
        {
          // 当 /user/:id/posts 匹配成功
          // UserPosts 会被渲染在 User 的 <router-view> 中
          path: 'posts',
          component: UserPosts
        }
      ]
    }
  ]
})
```