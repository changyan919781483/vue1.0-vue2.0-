```
//vue 1.0 路由配置



1.模板配置
<router-view></router-view>



2.js配置路由


//1. 准备一个根组件

        var App=Vue.extend();

//2. 写自己需要的组件 Home News组件都准备
		var Home=Vue.extend({
			template:'<h3>我是主页</h3>'
		});

		var News=Vue.extend({
			template:'<h3>我是新闻</h3>'
		});

        var NewsContent=Vue.extend({

            template:'#news_content'
        })

//3. 准备路由
        var  router=new VueRouter();

//4. 关联
        router.map({
            'home':{
                component:Home
            },
            'news':{
                component:News
            },
            'news_content/:id':{

                component:NewsContent
            }
        })
//5.默认跳转路由
	router.redirect({
		'*':'/home'
	})
//6. 启动路由
router.start(App,'#box');
```