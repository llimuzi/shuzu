

# 		cookie

​	[1.cookie]()本质上一个字符串,里面包含浏览器和服务器沟通的信息,存储形式key-value.

##### [2.分类]():

​	**`会话`**cookie(浏览器关闭时候,会话cookic会自动消失,会话cookie存储在浏览器运行的那块内存上).

​	**`持久`**化cookie	(看过期时间,过期时间到了,就自动销毁,存储在用户的硬盘上,备注:如果没有到过期时间,同时用户清理了缓冲,持久化cookie也会消失)

[3.工作原理]():

​		当浏览器第一次请求服务器的时候,服务器会返回一个或者多个cookie给浏览器.

​	[浏览器判断cookie种类:]()

​				会话cookie,存储在浏览器运行那块内存上.

​				持久化coolie,存储在用户的硬盘上

​	*`以后请求该网站的时候,自己携带上该网站所有cookie`*

​	`服务器拿到之前自己"种"下cookie,分析里面内容,检验cookie的合法性,根据cookie里保存的内容,进行具体业务逻辑.`	

[4.应用:]()

​	解决http无状态的问题.(列如:7天免登录,不会单独使用cookie,和session存储使用)

[5,]()不同的语言,不同的后端架构coolkie具体语法是不一样的,但是cookie原理和过程是一样的.		

- [ ] ​	cookie不一定只有服务器生成,前端同样可以生成cookie,但是前端上生成cookie几乎没有意义.

- [ ] 在express中读取cookie,要借助一个中间件:cookie-parse

- [ ] 删除cookie有二种方式:

  ​		1.response.clearCookie('demo')

  ​		2.response.cookie('demo','',{maxAge:0})

  ​

  # session

  ​	[1.是什么:]()

  ​			session这个单词指定是会话,但是后端人员叫:服务器session会话存储.

  ​	[2.特点:]()

  - [ ] ​	存储在服务器

  	 [ ] ​	存储是浏览器和服务器沟通信息

    `3.默认session的存储在服务器的内存中,每当一个新客户端发来请求,服务器都会开辟出一块空间,供session会话存储使用`

		4.工作流程:

- `第一次浏览器请求服务器的时候,服务器会开辟一块空间,供session会话使用.`


- [ ] - [ ] ​	**返回响应是时候,会自动返回一个cookie(有时候会返回多个,为了安全),cookie里面包含上一次产生会话存储''编号''.	,以后请求的时候,会自动携带cookie给服务器.**
		[ ] ​	服务器从cookie中拿到对应session的id,去和服务器匹配,服务器会根据匹配决定.		

 5. 一般来说cookie一定配合session使用.

 6. 服务端一般会做session的持久化,防止由于服务器重启,造成session丢失.

    ​


# react

##### 		`react` :用于动态构建用户界面js库(只关注View),是由Facebook开源.

​			**特点**:声明式编码,组件化.高效,单向数据流

- React高效的原因:

  ​			虚拟DOM,不总是直接操作DOM

  ​			DOM Diff算法, 最小化页面重绘

  ​					

  1. 虚拟DOM有二种创建方式:

       1.使用原生js创建借助React身上的一个方法，即：不使用jsx）

       			2.使用jsx语法

       **组件**:用来实现特定界面功能效果的代码集合(html/css/js/imge)


       let:里面只能写构造器,赋值语句,定义函数

#### 组件间通信:

​		方式一:通过props传递,

​			1.共同的数据放在父组件上,特有的放在自己组件内部

​			2.可以传递一般属性和特有属性

​			3.一般属性-->父组件传递数据给子组件间-->子组件读取数据

​			4.函数组件-->子组件传递数据给父组件-->子组件调用函数

​	2.组件有二种创建方式:

​				1.	工厂函数,简单(无状态)			

​				2.es6类方式,复杂(有状态),用类

​	3.组件传参方式:

​				第一种方式,:props,适用于父-->子

​				第二种方式:使用消息订阅发布机制(pubsub)

​							1.安装:yarn add pubsub-js 







# 	Promise



​		1.函数对象与实例对象:

​				函数对象:将函数作为对象使用时, 简称为函数对象

​				实例对象:new 函数产生对象,

​		2.回调函数分类:

​				1,同步回调:立即执行完才结束,不会放在回调队列中

​				`列子`: 数组遍历相关的回调函数.

​						 Promise的excutor函数

​				2.异步回调:不会立即执行,回放到回调队列来执行.

​					`列子`:定时器回调,promise的成功,失败回调

纯回调函数:是在启动异步任务前指定的



###### 			promise不管是成功还是失败都是异步执行





​	1.	**判断错误类型:**

​			error:所有错误父类型

​			referenceError:引用变量不存在

​			TypeError:数据类型不正确

​			RangeErr:数据值不在允许范围

​			SyntaxError: 语法错误

​		2.	[处理错误:]()

​					捕获错误:try...catch

​					抛出错误:throw error



​		3.Promise是什么:

​				1.是js异步编程,promise是一个构造函数,

​				用来封装一个异步操作并获得结果



​			`状态:` pending初始化变成resolved(成功)

​					pending初始化变成rejected(失败)

​			[一个promise对象只能改变一次,不管是成功还是失败,都会有调用,可以解决一个结果]()

​			成功的数据称:value,失败的数据:reason

#### 			`为什么要用promise:`

​				1.指定回调函数的方式更灵活

​					2.支持链式,可以解决回调地狱问题

#### 	`什么是回调地狱:`回调函数嵌套调用,外部回调函数异步执行的结果是嵌套调用函数	执行条件.

​	**缺点:**不便于阅读,不便于异常处理.

​	解决方法:promise链式调用

​	终极解决方案:async/await

#### 	promise语法:

​			excutor函数:同步执行

​			resolve函数: 内部定义成功时我们调用的函数,value

​			reject函数: 内部定义失败时我们调用的函数,reason

​			Promise.prototype`.then`有二个方法:onResolved,onRejected,一个是成功回调函数(value),一个是失败回调函数(reason),这两个返回都是Promise对象



###### 			  promise.`then()`返回的新promise的结果状态由什么决定?

​						1.是由then()指定的回调函数执行结果决定.

​						 (2)详细表达:one:如果抛异常,新的promise变为rejected,reason为抛出异常.

​						3如果返回的是非promise的任意值,新porimse变为resolved,value为返回值.

​						 4如果返回的是另一个新promise, 此promise的结果就会成为新promise的结果 

​			 Promise.prototype`.catch`有一个方法:(onRejected)

> ​			  *说明: then()的语法糖, 相当于: then(undefined, onRejected)*		

​			promise[.`all`]()方法:包含多个n个promise的数组,因为:返回一个新的promise,只有所有promise都成功才成功,只要有一个失败就直接失败.

​			promise.`race`方法:包含n个promise数组

​				返回一个新的promise,第一个完成promise结果状态就最终状态

###### 		    3.   改变promise状态和指定回调函数谁先谁后?

​				1.都有可能,正常情况先指定回调再改变状态,但是也可以先改状态在执行.

​			如何先改状态再指定回调?

​				1.在执行器中直接调用resolve()/reject()

​				2延迟更长时间才调用then()

​		什么时候才能得到数据?

​				如果先指定回调的函数,当状态改变时,回调函数就会调用,得到数据.

​				如果先改状态,那当指定的回调函数,回调函数就会调用,得到数据



###### 	4.promise如何串连多个操作任务?

​			(1)promise的then()返回一个新的promise, 可以开成then()的链式调用

​      (2)通过then的链式调用串连多个同步/异步任务

**[5.promise异常传/穿透?](**)

​		1.当时用promise的then链式调用时,可以在最后指定失败回调

​		2.前面任何操作出了异常,都会穿到最后失败的回调中处理****

- [ ] **`6.中断promise链?`**

  ​		1.当使用promise的the链式调用时,在中间中断,不在调用后面回调函数.

  ​		解决:在回调函数中返回一个pending在状态的promise对象

  ​

####  XHR理解:

​	使用xhr对象可以与服务器交互 ,也就是发送ajax请求

​	前端可以获取到数据，而无需让整个的页面刷新。

API

1. XMLHttpRequest(): 创建XHR对象的构造函数

2. .staus:响应状态码,

3. statusText:响应状态文本

4. readyState:标识请求状态的只读属性

5. 0:  初始

  1:  open()之后

  2:  send()之后

  3:  请求中

  4:  请求完成

6. onreadystatchange:绑定readyState改变监听

7. onerror:绑定监听请求网络错误监听

8. open():初始化一个请求,参数(method (字符串),url(字符串),布尔值,(async))

9. send(data):发请求

10. abort():中断请求

11. getResponseHeader(name):获取指定名称响应头值

12. getAllResponseHeades()获取所有响应头组成字符串

13. setRequestHeader(name vale):设置请求头


什么样的对象是config(配置对象):

​		1.对象名是固定.2.每个属性是固定的




​	Http:

​		不同类型请求及其作用:

​			GET:从服务器读取数据

​			POST:向服务器端添加新数据

​			PUT:更新服务器已有数据

​			DELETE:删除服务器端数据

​	API的分类(前后端接口)

​	REST API:  (restful):

​		1.同一个请求方式路径可以进行多个操作

​		2.请求方式会用到GET/POST/PUT/DELETE

​	非REST API : restless

​		1.请求方式不决定请求CRUD操作

​		2.一个请求路径只对一个操作

​		3.一般只有GET/POST



##### 区别一般http请求和ajax请求

​	1.ajax请求是一种特别的http请求, 发请求是:客户端和浏览器端,

​		浏览器做二件事: 1,发请求,接收响应数据进行处理

​		ajax引擎是什么:是帮我们发请求的程序代码

​	2.对服务器端没有任何区别,区别在浏览器

​	3.浏览器发请求:只有xhr或fetch发出的才是ajax请求,其他的都不是ajax请求

​	4.浏览器端接收响应

​		1.一般请求:浏览器一般会直接显示响应数据,也就是常说的刷新/跳转页面.

​		2.ajax请求:浏览器不会对界面进行任何更新操作,只是调用监视的回调函数并传(更新      )入响应相关数据



  #### async和awiait

  ​	1.async函数返回值是一个promise对象,async函数返回的pomise结果是有函数执行结果决定.

  ​	2.awiait右侧表达式为promise, 得到结果就是promise成功的value

  		.awiait右侧表达式不是promise,得到结果就是它本身

  	要是得到失败结果是:try...catch





#### 	axios:

​		1.最流行ajax请求 库

​	特点:	1.基于promise的异步ajax请求库,

​			2.支持请求/响应拦截器

​			3支持请求取消

​			4.请求/响应数据转换

​			5.批量发送多个请求

​	语法:	axios(config):通用/最本质的发任意类型请求的方式

​			axios(url,config):可以指定url发get请求

​			axios.defaults.xx:请求默认全局配置

​			axios.interceptors.request.use():添加请求拦截器

​			axios.interceptors.response.use():添加响应拦截器

​			axios.create([config]):创建一个新的axios



​			axios.Cancel():用于创建取消错误对象

​			axios.CancelToken():用于创建取消请求token对象

​			axios.isCancel():是否是一个取消请求错误

​			axios.all(poromis):用于批量执行多个异步请求

​			params:quest参数

特点:

​	函数返回值promise,成功结果response,异常结果error

​	能处理多种类型请求:GET/POST/PUT/DELETE

​	

​		





  1. post请求----json格式必须有请求头

     put ---  

     ##### 拦截器:1.请求栏截器真正发请求前 2.请求拦截器是后添加先执行 3.先执行响应拦截器,在执行回调 4.请求拦截器必须返回config,如果不传就undefined










#### react项目:

​	如何知道数据库连接成功:

​			安装. 启动,查看任务管理器

项目采用:模块化,组件化,工程化



​	项目提到git三步:

​			版本控制:

​			1.创建本地仓库,2.创建远程仓库 3. 本地推到远程,4.更新(如果本地更新推的远程,)(远程更新拉取本地).5克隆



class Login exends Compent()

const LoginWrap =Form.creat()(Login) Form.creat()(包含<From>的组件),返回一个新组件

高阶函数:

​	如何函数接收的参数是函数或者返回是函数

​	例子:promis()/the()/定时器/数组遍历相关方法()/bind()/$.get()

高阶组件:

本质是一个高阶函数

​	参数为组件,返回为新组件的函数

​	例子:From.creat()(组件)/withRouter(组件) /connect()(组件)

与高阶函数什么关系:高阶组件是一个特别的高阶函数 ,接收是组件函数.同时返回新新组件函数

作用:

​	react中用于复用组件逻辑的一种高级技巧

组件和组件标签什么关系:

​	组件标签是组件实例



js是面向对象:封装一些功能和方法,一些对象

[订阅与发布](https://github.com/zxfjd3g/190620_utils.git)

​	token=PubSub.subscribe(name,callback):订阅消息 相当于绑定事件监听

​	PubSub.publish(name,data):发布消息(异步) 相当于(dispath)事件

​	PubSub.publishSync(name,data):发布消息(同步)

​	PubSub.unsubscribe(flag):取消订阅







#### redux是什么:

​		是一个独立专门用于做状态管理js库(不是react插件库)

​		作用:集中式管理react应用对多个组件共享的状态

​		

​	`组件状态是可变的数据`

**[API]()**:

​	creatstore() 创建包含指定的reduer的store对象

​	store对象 :作用,redux最核心的管理对象,它内部维护state reducer

[核心方法]():

​		getState() store.dispath({type:'INCREMENT', number})

​		store.subscribe(render)

###  applyMiddleware():应用基于redux的中间件

##  redux的三个核心概念:

​		1.actio:标识要执行行为对象

​		2.reducer:根据老的state和actoin,产生新的state的纯函数 

​		3.store:将state,action与reducer联系在一起的对象

同步action是对象:{typen:'add',data:'3'}

异步action是函数:dispath=>{

​		1.执行异步操作,2.有结果后,dispatch(同步action对象)



}









#### reacr-redux(将所有组件分成两大类):

​				UI组件(通过props接收数据(一般是数据和函数 )  容器组件

[API:]()

​	Provider:让所有组件都可以得到state数据

​	connent():用于包裹UI组件生成容器组件

​	mapStateToprops():将外部的数据(state对象)转化UI组件标签属性

​	mapDispatchToProps():将分成action函数转为UI组件标签属性



​			

#### Vue:

​	动态构建用户界面,发请求从后端获取数据,用vue构建显示

特点:

​	1.遵循MVVM模式,2.编码简单,体积小,运行效率高,适合与移动端/pc端,3.本身只关注UI,可以轻松引入vue插件或其他第三方开发项目

token组成:前缀[_]()消息名[_]()唯一的ID值

[模板](): 动态的h   tml页面,包含js语法代码,

vue的模板是以什么js写的:

[指令]():v-model='"msg" vue自定义标签属性,自动收集数据

**插值/大号表达式:{{msg}}** :动态显示数据

有两个语法:

​	插值:{{exp}}或{{{exp}}},功能:向页面输入数据

​	{}:只能写在标签里,作为标签一部分

​	指令一:强制数据绑定, 功能:指定变化属性值

​	[数据绑定:]()1.对象数据:通过给对象内部加set方法

​			2.数组数据:重写,更新数组中的方法

​		完整写法:v-bind:xxx简写:xxx='yyy'

​	指令二:绑定事件监听,绑定指定事件名的回调函数

​			完整写法:v-on:click='xxx'`

​			简写:@click='xxx'



[模板和html区别]():模板是动态;html是静态

声明式=命令式

​	MVVM:只要改data数据,页面就会自动更新

object.defineProperty(obj,prop,{属性描述符

​	*1*.数据描述符

​	2.存取描述符:getter(get):读取属性值自动调用,用来返回属性值,this是包含属性的对象

​				setter(set):属性值发生改变时自动调用,监视属性变化的,this是包含属性的对象

})

[[计算属性和监视:]()]()

​	get():只能些同步代码,立即返回调用 ,可以监视所有依赖数据,编码简单,但是只能同步计算产生一个需要的结果

​	watch:先执行异步代码,长时间处理后更新结果

[`计算属性`]的方法什么时候执行:

​		1.初始显示一次

​		2.依赖数据发生变化

如果改this.的回调函数:

this.是内置变量

​	bind()  =>函数

[定时器]()的回调函数[this]()是window

[过滤器]():

JS方法:

​	indexOf:返回某个指定的字符串值在字符串首次出现位置

​	sort:对数组元素进行排序

[class和style]():

​		动态class字符串: 类名不确定

​		动态class的对象: 类名确定, 但不确定有没有

[Vue生命周期]():

​		1.初始化显示

​		beforeCreate()

​		created() 这俩者之间做初始化操作:数据代理和数据绑定

​		beforeMount()

​		mounted()

​		2.更新状态(n次)

​			beforeUpdate()

​			Updated()

​		3.销毁vue实例:vm.$destory()

​			beforeDestory()

​			destoryed

​			4.activated() 配合keep-alive组件用来缓存组件,避免多次加载相应组件,少性能消耗

​			deactivated()

​			

[常用的生命周期方]()法:

​		mounted():发送ajax请求,启动定时器等异步操作

​		beforeDestory():做收尾工作,如:清除定时器

babel有俩个包:插件包,预设包

​	预设包里面有许多插件包,每次配置插件太麻烦,只要配置预设包就可以



面试题:mouseout和mouseover-----mouseenter和mouseleave区别:

组件编程项目:

​	1.拆组件,2.实现静态组件,3.实现动态组件2.动态显示 

[vue组件通信方式]():

​	1.props 通过标签属性传递数据 --->父子之间通信

​		一般属性 : 属性值不同,传递方向不同,如果传递是个函数通信的是子----->父

​		兄弟通信借助父组件

​		子孙传递:一层一层传递

​	2.vue自定义事件:给子组件标签绑定 事件监听,子组件向父组件通信,不适于隔层组件和兄弟组件通信

​	3.全局事件总线:(1)利用vm对象的$on()

​	$emit/-------->$off()    

​	(2)利用vm对象是组件对象的原型对象,(3)创建vm对象作为全局事件总线对象保存点Vue的原型对象上,所有的组件对象都可以直接可见

​		Vue.prototype.$bus=new Vue()

​		任意组件A可以通过this.$bus.$on()绑定监听接收数据

​		任意组件B可以通过this.$bus.$emit()分发事件,传递数据

​	4.slot(插槽):通信的不是简单数据,而是向子组件传递带数据标签,标签是在父组件  ---->

 	5.vuex

组件的关系:父子,子孙,兄弟



​	

​	自定义几个问题:

​		1.在哪绑定监听---->父组件

​		2.给谁绑定---->子组件

​		3.在哪分发事件---->子组件

​		4.数据从子组件转父组件,,子向父通信

实现vue总线:

​	vue提供了3个方法----> 你

​				$on

​				$emit

​				$off	

​	组件对象原型对象是一个vm对象,把事件总线放在vue原型对象上,所有的组件都可见

 

​	[vuex]()

​	srort对象:

​		得到:this.$store

​		使用:	读数据:this.$store.state.xxx

​						this.$store.getters.yyy

​				写数据:	this.$store.dispatch('actionName')

​						this.$store.commit('mutationName')

​	vue源码分析:

  

  [token携带的方式:]()

​	1.cookie  2. 请求参数  3.放在请求头

  	Vue项目问题:

​		在vue项目做了什么性能优化:

​			1.我们对ui库进行样式的按需加载,用的库[babel-plugin-component]()

​	











[小程序项目]()"

​	在小程序是单项数据流:Model流向View

​	异步和同步区别:阻塞和非阻塞

​	在开发的时候不要在定时器后面放特别大的代码

​	修改状态:this.setData() 同步修改

[小程序特点:]()

​	1.小程序没有Dom,一切基于组件化

​	2.体积小,压缩包的体积不能大于2m

​	3.小程序适配方案:iphone6: 1rpx=1物理像素=0.5px



[小程序事件:()

​	冒泡事件和非冒泡事件 

