
# Canvas 画布
课件地址： http://learn.fuming.site/front-end/Canvas/
```
应用场景：
1. 把canvas当做动态背景图
2. 小游戏 （代替flash）
3. 统计图表，数据分析结果

```



## 1 canvas 元素
HTML5新增了的一个画布标签
```
canvas.width
canvas.height
canvas.getContext();  //获取绘图上下文
```


## 2. 使用步骤
```js
// ① 获取canvas 元素
// ② 设置 canvas 大小
// ③ 获取绘图上下文
// ④ 画
```


## 3 Canvas 路径

### 3.1 绘制路径
#### 线段
```
ctx.moveTo(x, y)
ctx.lineTo(x, y)
```

#### 矩形
```
ctx.rect(x, y, width, height);
```

#### 绘制圆
```js
ctx.arc(x, y, r, startAngle, endAngle, 是否逆时针)  // true 逆时针， false顺时针(默认)
```

#### 圆弧路径
```js
ctx.arcTo(x1, y1, x2, y2, radius);  

```


### 3.2 路径描边
```js
ctx.lineWidth = 10;  // 设置描边的宽度
ctx.strokeStyle = 'red';  // 设置描边颜色
ctx.stroke()  // 对路径描边
```



### 3.3 路径填充 
```js
ctx.fillStyle = 'red'; // 设置填充颜色
ctx.fill(); //填充
```
```
(了解) 复杂路径的填充
如何判断一块区域是否填充
从该区域任意画一条无限长的直线，判断经过了几条线
如果经过了奇数条线，肯定会填充
如果经过了偶数条线，判断线的方向 （两个方向的线的数量相等，不填充）

```

### 3.4 路径开启
```js

ctx.beginPath(); //开启新的路径，并且结束上一次路径

// 每绘制一个图形，都开启一个路径
```


### 3.5 路径闭合
```js
ctx.closePath();  // 把最后一个点 和 起点连接

```


### 3.6 设置路径两端的样式
```js
ctx.lineCap = '';  
// butt  默认值
// round 
// square

```

### 3.7 设置路径连接点的样式
```js
ctx.lineJoin = '';
// miter  默认值
// round
// bevel
```








## 4 快速矩形工具
```js
// 无需考虑路径

ctx.fillRect(x, y, width, height); //快速填充矩形
ctx.strokeRect(x, y, width, height); //快速描边矩形
ctx.clearRect(x, y, width, height); //快速清空矩形矩形
```


## 5 变换
### 5.1 三种变换效果
```js
ctx.translate(width, height)
ctx.scale(x, y)
ctx.rotate(弧度)

```
```
变换变换整个坐标体系，引起坐标体系变化
只有在变换之后绘制的图形会受到响应
一般各种变换配合，translate和其他配合
```


### 5.2 绘图环境的保存和恢复
```js
ctx.save()  // 保存当前环境
ctx.restore()  // 绘图上一次保存的环境
```
```
在变换之前，先 save()
变换之后，（一系列绘制） restore()

```


## 6 加载图片
```js
ctx.drawImage(imgEle, x, y, width, height)
```
```
使用步骤：
    ① 创建 img 元素
    ② 指定 img 元素 src 属性
    ③ 监听 load 事件
    ④ load 事件触发，等图片完全加载完毕，再向画布绘制图片
```


## 7 渐变
### 7.1 线性渐变
```js
linearG = ctx.createLinearGradient(x1, y1, x2, y2);

linearG.addColorStop(0~1, color)
```
```
渐变对象相当于一种颜色值，赋值给 strokeStyle 或 fillStyle
渐变色作用在了画布上，一个图像是什么颜色，取决于在画布的位置

```

### 7.2 径向渐变
```js
var radialG = ctx.createRadialGradient(x1, y1, r1, x2, y2, r2);

radialG.addColorStop(0~1， color)
```


## 8 文字
```js
ctx.font = '';   // 设置文字的 大小 类型 粗细  值 同 css font属性的值
ctx.textAlign = '';  // 水平对齐方式 start / end / center
ctx.textBaseline = '';  // 垂直对齐方式 常用 middel / top / bottom
ctx.fillText(text, x, y);  // 填充文字  
ctx.strokeText(text, x, y);  // 描边文字 镂空字

```


## 9 阴影
```js
ctx.shadowOffsetX = 10; 
ctx.shadowOffsetY = 10;
ctx.shadowColor = 'red'; 
ctx.shadowBlur = 5;
```


## 10 图像合成
```js
ctx.globalCompositeOperation = '';
```


## 11 像素操作
```js
ctx.getImageData(x, y, width, height);  //从画布中选取一块矩形区域作为 iamgeData对象
ctx.putImageData(imageData, x, y);   // 把iamgeData对象 写入到 canvas 指定的位置
ctx.createImageData(width, height);  // 创建一个imageData对象，默认颜色是 0,0,0,0

```
```
imageData对象：
    width
    height
    data   数组 描述每个像素点的颜色信息，每4个元素描述一个像素，  r、g、b、a； 没个值的范围 0~255

```