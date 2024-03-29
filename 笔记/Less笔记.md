http://learn.fuming.site/front-end/CSS%E9%A2%84%E5%A4%84%E7%90%86%E5%99%A8/

# Less

## 1 less编译器
### 1.1 less.js
```
当页面运行的时候，现场把less编译成 css

运行时编译
```

### 1.2 考拉编译
```
提前把 less 编译成 css
html直接引入 css

写 less 的时候编译
```


### 1.3 node 编译


## 2 less 的变量
### 2.1 变量的定义
```
@变量名：值;
```

### 2.2 变量的使用
```
作为属性值去使用（最常见）
@变量名

作为选择器或者属性名取用
@{变量名}

```


### 2.3 变量的作用域
```
.box {
    li {
        @var:1;
        width: @var;  // 2
        @var:2;
    }
}

先从本作用域找，没有去上层作用域找
统一作用域下，变量定了两次，后面会覆盖前面（提升）
```

### 2.4 哪些东西需要定义成变量
```
1. 网站配色 的 颜色
2. 常见的字体大小
3. 媒体查询的阈值
```


## 3 less 的注释
```less
/* css注释 less也可以用  编译成css后依然存在*/

// less 注释  编译成css后不显示了
```


## 4 混合
### 4.1 普通混合
```less
//跟类选择器是一样的 会在css输出
.my-mixin {

}
```

### 4.2 不会输出的混合
```
// 不会输出在 css 中
.my-mixin() {

}

.my-mixin();
.my-mixin;  //混合没有参数，省略 ()

```

### 4.3 带参数的混合
```less
.my-mixin(@width, @height) {

}
```

### 4.4 参数有默认值  有默认值的参数在后面
```less
.my-mixin(@width, @height:100px, @color:gray) {

}

.my-mixin(100px);  //按照顺序给参数赋值，没有赋值的参数使用默认值，赋值就用赋的值

```


### 4.5 参数有默认值  有默认值的参数在任意位置
```less
.my-mixin(@width:100px, @height,  @color:gray) {

}

// 调用的时候 指定参数名
.my-mixin(@height:10000px);

```


### @arguments  获取所有参数
```css
.my-mixin(@a, @b, @c, @d, @e) {
    property: @arguments;
}
```
```
特殊情况： 调用混合的时候，参数之间可以用逗号隔开，也可用分号隔开
一般用逗号，某个参数的值里面包含了逗号，请使用分号去分隔参数

```


### 使用混合的场景
```
1. 页面中常见的小组件 （按钮，边框，背景）
2. 某些带私有前缀的CSS属性 （后面自动化工具）
```

