不用var，let 定义变量，const 定义常量

普通输出：

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">{{print}}</div>
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
            const app = new Vue({
                el:'#app',
                data:{
                    print:'城院小爱'
                }
            })
        </script>
    </body>
</html>
```

输出列表：

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">
            <ul>
                <li v-for="item in list">{{item}}</li>//v-for 遍历列表
            </ul>
        </div>
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
            const app = new Vue({
                el:'#app',
                data:{
                    list:['1','2','3']
                }
            })
        </script>
    </body>
</html>
```

计数器：

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">
        <h2>当前计数：{{counter}}</h2>
        <button v-on:click="add">+</button>
        <button v-on:click="sub">-</button>
        </div>
        
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
            const app = new Vue({
                el:'#app',
                data:{
                    counter: 0
                },
                methods:{
                    add:function(){
                        this.counter++
                    },
                    sub:function(){
                        this.counter--
                    }
                }
            })
        </script>
    </body>
</html>
```

```html
v-once：不随后面messa的改变而改变
<div id="app">
    <h2 v-once> {{message}} </h2>
</div>
```

```html
v-html：超链接
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">
            <h2 v-html="URL"></h2>
         </div>
        
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
            const app = new Vue({
                el:'#app',
                data:{
                    URL：'<a href="http://www.baidu.com">百度一下</a>'
                }
            })
        </script>
    </body>
</html>
```

```html
v-text：就和{{}}一样，但是不方便拼接，若<h2 v-text="message">123</h2>，123会直接覆盖message的内容
<h2> {{message}}+123 </h2>，可以直接拼接
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">
            <h2 v-text="message"></h2>
         </div>
        
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
            const app = new Vue({
                el:'#app',
                data:{
                    message:'城院小爱'
                }
            })
        </script>
    </body>
</html>
```



```html
v-pre:直接输出{{message}}，不解析
<h2 v-pre> {{message}} </h2>
```

```html
v-cloak:加载时延迟不会出现未解析的{{message}}，也可以设置出现其他的东西
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
        <style>
            [v-cloak]{
                display:none;
            }
        </style>
    </head>
    <body>
            <div id="app" v-cloak>{{message}}</div>
        
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
            const app = new Vue({
                el:'#app',
                data:{
                    message:'城院小爱'
                }
            })
        </script>
    </body>
</html>
```

```html
v-bind:动态绑定。简写是直接写个冒号：
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">
            <img v-bind:src="imgURL" alt="">
            <a v-bind:href="URL">百度一下</a>
        </div>
        
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
            const app = new Vue({
                el:'#app',
                data:{
                    imgURL:'https://vuejs.org/images/logo.svg',
                    URL:'http://www.baidu.com'
                }
            })
        </script>
    </body>
</html>
```

```html
v-bind 动态绑定class
<h2 v-bind:class="{类名1：boolean，类名2：boolean}">{{message}}</h2>
<h2 v-bind:class="{active：true，line：false}">{{message}}</h2>

true 和 false 可以放在data里面，例如： isactive:true,isline:true,
<h2 v-bind:class="{active：isactive，line：isline}">{{message}}</h2>
class 的 active 定义在style里面： .active{color:red;}
前面还可以直接加上不用变化的class
<h2 class="test" v-bind:class="{active：isactive，line：isline}">{{message}}</h2>
```

```html
v-bind动态绑定style
<h2 :style="{css属性名：'属性值'}">
    {{message}}
</h2>
不要忘了单位，单位若要写在methods里面，是需要单引号的
<h2 :style="{fronsize：finalsize + 'px'}">{{message}}</h2>
```

```html
computed:{} 计算属性，引用时不用加（）,不是函数，不要去动作名称。有缓存，计算速度会更高。
computed:{
    fullname:function(){
    return this.firstname +" "+ this.lastname
}
},
```

```html
getter , setter 方法: 计算属性一般是没有set方法的，是只读属性
computed:{
    fullname:{
        set: function(){
            
        },
        get: function(){
            return this.firstname +" "+ this.lastname
        }
    }
}
```

```html
函数增强写法：
const name="123";
const sno="456";
const cno="789"

const people:{
    name,
    sno,
    cno
}
```

```html
v-on:
@click.stop="btnclick"  //阻止冒泡
@click.prevent="btnclick"  //阻止提交
<input type = "text" @keyup.enter> //监听键盘某个键的抬起：回车
```

```html
v-if: 类似于C语言的else，if
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">
					<h2 v-if="score>=90">优秀</h2>
					<h2 v-else-if="score>=80">良好</h2>
					<h2 v-else-if="score>=60">及格</h2>
					<h2 v-else>不及格</h2>
				</div>
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
            const app = new Vue({
                el:'#app',
                data:{
                    score:100
                }
            })
        </script>
    </body>
</html>
```

```html
v-show:当条件为false时，指令元素还是会保留在dom中，只是把display置为null；而v-if会直接从dom中删除，true和false来回切换就是创建和删除。
切换频率高时用v-show，当只有一次切换时用v-if。
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">
					<h2 v-show="true">{{message}}</h2>
				</div>
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
            const app = new Vue({
                el:'#app',
                data:{
                    message:'go'
                }
            })
        </script>
    </body>
</html>
```

```html
v-for：

遍历过程中没有使用到下标值：
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">
            <ul>
                <li v-for="item in list">{{item}}</li>//v-for 遍历列表
            </ul>
        </div>
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
            const app = new Vue({
                el:'#app',
                data:{
                    list:['1','2','3']
                }
            })
        </script>
    </body>
</html>

在遍历过程中获取下标值：
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">
            <ul>
                <li v-for="（item，index） in list">{{index+1}}.{{item}}</li>
            </ul>
        </div>
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
            const app = new Vue({
                el:'#app',
                data:{
                    list:['1','2','3']
                }
            })
        </script>
    </body>
</html>

遍历对象：
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">
            <ul>
                <li v-for="(value,key) in info">{{value}}-{{key}}</li>
            </ul>
        </div>
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
            const app = new Vue({
                el:'#app',
                data:{
									info:{
										name:'luchengjie',
										age:20,
										school:'ZUCC'
									}
                }
            })
        </script>
    </body>
</html>

使用v-for时最好加上key，加上后能够更好地复用！！！
中间插入操作时不会一直做位移操作
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">
            <ul>
                <li v-for="（item，index） in list :key="item"">{{item}}</li>
            </ul>
        </div>
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
            const app = new Vue({
                el:'#app',
                data:{
                    list:['1','2','3']
                }
            })
        </script>
    </body>
</html>
```

```html
响应式：使用响应式的才会重新改变dom，界面才会改变
push()在最后加东西  
pop()从最后一位删除  
shift()从最前面的第一个元素开始删除  
unshift()在数组最前面添加元素  
splice(a,b)从a开始删除b个元素  
splice(a,0,'c')在第a位加一个元素'c'  
splice(1,3,'m','n','l')替换，替换的加在最后面，就是删除后在后面添加
sort()排序  
reverse()反转
```

```html
filters：过滤器，是个函数。改变显示方式。
filters:{
  showPrice(price){
    return '￥'+price.toFixed(2)
  }
}
```

```html
加了disabled按钮就不能按了。
<button disabled>按钮</button>
```

```html
v-model:双向绑定
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">
            <input type="text" v-model="print">
            {{print}}</div>
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
            const app = new Vue({
                el:'#app',
                data:{
                    print:'城院小爱'
                }
            })
        </script>
    </body>
</html>
```

```html
v-model:radio 单选框。可以提交数据库传数据，保存用户数据
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">
            <label>
			<input type="radio" id="male" value="男" v-model="sex">男
			</label>
			<label>
			<input type="radio" id="female" value="女" v-model="sex">女
			</label>
        </div>
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
           const app = new Vue({
                el:'#app',
                data:{
                    sex:'男'
                }
            })
        </script>
    </body>
</html>
```

```html
v-model:checkbox 
checkbox单选框：
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">
        <label>
		  <input type="checkbox" id="agree" v-model="isAgree">同意协议
		</label>
		<button :disabled="!isAgree">下一步</button>
        </div>
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
           const app = new Vue({
                el:'#app',
                data:{
                    isAgree:false
                }
            })
        </script>
    </body>
</html>

checkbox多选框：
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
        <div id="app">
		  <input type="checkbox" value="basketball" v-model="hobbies">basketball
		  <input type="checkbox" value="football" v-model="hobbies">football
		  <input type="checkbox" value="basetball" v-model="hobbies">basetball
		  <h2>您的爱好是：{{hobbies}}</h2>
        </div>
        <script src="//unpkg.com/vue/dist/vue.js"></script>
        <script>
           const app = new Vue({
                el:'#app',
                data:{
                    hobbies: []
                }
            })
        </script>
    </body>
</html>
```

