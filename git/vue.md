### vue-component(组件)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<!--view层 模板-->
<div id="app">
<!--组件：传值给组件中的值：props-->
<caohao v-for="item in items" v-bind:ch="item"></caohao> 3.
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>

<script>
    //定义一个Vue组件component
    Vue.component("caohao",{                 
        props: ['ch'],
        template: '<li>{{ch}}</li>'				
    });
  new Vue({
      el: '#app',
      data: {
          items: ['数学','语文','英语']        
      }
  });
</script>
</body>
</html>
```

## axios

~~~html
<div id="app">
    <div>{{info.name}}</div>
    <div>{{info.scripts.dev}}</div>
</div>
<!--引入js文件-->
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
<script>
var vm=new Vue({
    el: '#app',
    //data: 属性：vm
    data(){
        return{
            //请求返回参数合适，必须和json字符串一样
            info:{
                name: null,
                vsersion: null,
                scripts: {
                    dev: null,
                    start: null
                },
            }
        }
    },
    mounted(){//钩子函数 链式编程 es6新特性
        axios.get('./package.json').then(response=>(this.info=response.data));
    }
});
</script>
</body>
</html>
///package.json的文件
{
  "name": "hello-vue",
  "version": "1.0.0",
  "description": "A Vue.js project",
  "author": "richard_glb <richard_glb.he@gmail.com>",
  "private": true,
  "scripts": {
    "dev": "webpack-dev-server --inline --progress --config build/webpack.dev.conf.js",
    "start": "npm run dev",
    "build": "node build/build.js"
  },
~~~

