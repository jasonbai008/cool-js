# useful-cool-js

a collection of cool js tools

## Plugins

1. [Circle Follower 鼠标跟随插件](#鼠标跟随插件)
2. [Smooth Scroller 平滑滚动插件](#平滑滚动插件)
3. [Dynamic Counter 数字动画插件](#数字动画插件)
4. [Dynamic Counter Vue 数字动画插件 Vue 版](#数字动画插件Vue版)
5. [Div Scroller 双向跑马灯插件](#双向跑马灯插件)

## 鼠标跟随插件

一个简单优雅的鼠标跟随效果插件。

### 使用方式

#### 方式一：通过 script 标签直接引入

```html
<script src="https://unpkg.com/circle-follower@latest/index.js"></script>
<script>
  // 创建实例
  const follower = new Follower({
    size: 30,
    borderColor: "#00c569",
    borderWidth: 2,
  });
</script>
```

### 配置选项

创建实例时可以传入配置对象，所有配置项都是可选的：

```javascript
const follower = new Follower({
  // 以下是默认值
  size: 30, // 圆环默认大小
  bgColor: "transparent", // 背景色
  borderColor: "#00c569", // 边框颜色
  borderWidth: 2, // 边框宽度
  backdropFilter: "", // 背景滤镜效果，例如：'blur(5px)'
  hoverSize: 60, // hover时圆环大小
  hoverBgColor: "rgba(0, 255, 0, 0.3)", // hover时背景色
  hoverBackdropFilter: "", // hover时的背景滤镜效果
  speed: 0.15, // 跟随速度(0-1之间)
});
```

### 配置项说明

| 参数                | 说明                             | 类型   | 默认值                 |
| ------------------- | -------------------------------- | ------ | ---------------------- |
| size                | 圆环默认大小（像素）             | Number | 30                     |
| bgColor             | 背景色                           | String | 'transparent'          |
| borderColor         | 边框颜色                         | String | '#00c569'              |
| borderWidth         | 边框宽度（像素）                 | Number | 2                      |
| backdropFilter      | 背景滤镜效果                     | String | ''                     |
| hoverSize           | 鼠标悬停时圆环大小（像素）       | Number | 60                     |
| hoverBgColor        | 鼠标悬停时背景色                 | String | 'rgba(0, 255, 0, 0.3)' |
| hoverBackdropFilter | hover 时的背景滤镜效果           | String | ''                     |
| speed               | 跟随速度，范围 0-1，越大跟随越快 | Number | 0.15                   |

### 实例方法

#### destroy()

销毁实例，移除事件监听和 DOM 元素：

```javascript
const follower = new Follower();
// ... 使用一段时间后
follower.destroy(); // 销毁实例
```

## 平滑滚动插件

### 使用方式

```html
<script src="https://unpkg.com/circle-follower@latest/smoothScroller.js"></script>
<script>
  // 实例化平滑滚动插件
  new SmoothScroller({
    friction: 0.9, // 可选，速度衰减系数，值越小衰减越快（惯性小），建议范围：0.85-0.95
    sensitivity: 0.12, // 可选，滚动灵敏度，值越小滚动越慢，建议范围：0.08-0.15
  });
</script>
```

### Demo

- [demo](https://jasonbai008.github.io/circle-follower/test.html)

## 数字动画插件

一个轻量级的数字递增/递减动画插件，支持千分符格式化，可自定义动画时间。

### 特性

- 支持正数和负数的动画效果
- 支持千分符格式化
- 可配置动画持续时间
- 平滑的动画效果（60fps）
- 无依赖，原生 JavaScript 实现

### 安装

直接在 HTML 中引入 `dynamic-counter.js` 文件：

```html
<script src="https://unpkg.com/useful-cool-js@latest/dynamic-counter.js"></script>
```

### 使用方法

#### HTML 结构

在 HTML 中添加带有 `counter` 类名的元素，使用 `data-target` 属性设置目标数值，可选使用 `data-precision` 属性设置小数点精度：

```html
<!-- 基础用法 -->
<span class="counter" data-target="876"></span>

<!-- 带货币符号和2位小数 -->
<div class="counter-item">
  <span class="currency">$</span>
  <span class="counter" data-target="876.50" data-precision="2"></span>
</div>

<!-- 百分比格式 -->
<div class="counter-item"><span class="counter" data-target="-64.82" data-precision="2"></span><span>%</span></div>
```

#### 初始化

```javascript
new DynamicCounter({
  duration: 2, // 可选，动画持续时间（秒），默认2秒
  formatThousands: true, // 可选，是否使用千分符，默认true
});
```

### 配置选项

| 参数            | 类型    | 默认值 | 说明                   |
| --------------- | ------- | ------ | ---------------------- |
| duration        | Number  | 2      | 动画持续时间，单位：秒 |
| formatThousands | Boolean | true   | 是否启用千分符格式化   |

## 数字动画插件 Vue 版

一个基于 Vue 的数字动画插件，支持千分符格式化，可自定义动画时间。

### 使用方法

1. 引入并注册插件:

```js
import Vue from "vue";
import DynamicCounterVue from "useful-cool-js/dynamic-counter-vue";

Vue.use(DynamicCounterVue, {
  duration: 2, // 可选，动画持续时间（秒），默认2秒
  formatThousands: true, // 可选，是否使用千分符，默认true
});
```

2. 在组件中使用:

```html
<!-- 不带小数点  -->
<span v-counter="number"></span>
<!-- 保留2位小数 -->
<span v-counter:2="price"></span>
```

## 双向跑马灯插件

一个轻量级的双向滚动走马灯插件，支持鼠标滚轮控制方向，自动无缝滚动，鼠标悬停暂停等功能。

### 特性

- 自动无缝循环滚动
- 支持鼠标滚轮控制滚动方向
- 鼠标悬停自动暂停
- 自动填充容器宽度
- 可自定义滚动速度
- 无依赖，原生JavaScript实现

### 安装

直接在HTML中引入 `div-scroller.js` 文件：

```html
<script src="https://unpkg.com/useful-cool-js@latest/div-scroller.js"></script>
```

### 使用方法

#### HTML结构

```html
<div class="scroll-container">
    <div class="scroll-item">内容1</div>
    <div class="scroll-item">内容2</div>
    <div class="scroll-item">内容3</div>
</div>
```

#### 初始化

```javascript
const scroller = new DivScroller({
    container: document.querySelector('.scroll-container'), // 容器元素
    speed: 1,  // 可选，滚动速度，默认1
    direction: 'right'  // 可选，初始滚动方向，默认right
});

// 开始滚动
scroller.start();
```

### 配置选项

| 参数      | 类型     | 默认值  | 说明                           |
|-----------|----------|---------|--------------------------------|
| container | Element  | -       | 容器元素（必填）               |
| speed     | Number   | 1       | 滚动速度                       |
| direction | String   | 'right' | 初始滚动方向，可选 'left'/'right' |

### 实例方法

| 方法名         | 说明                     |
|---------------|--------------------------|
| start()       | 开始滚动                 |
| stop()        | 停止滚动                 |
| setDirection(direction) | 设置滚动方向('left'/'right') |

### 交互说明

- 向上滚动鼠标滚轮：内容向左滚动
- 向下滚动鼠标滚轮：内容向右滚动
- 鼠标悬停在内容上：暂停滚动
- 鼠标移出内容：继续滚动

### 注意事项

1. 容器元素需要设置固定宽度或100%宽度
2. 内容元素会被自动克隆以实现无缝滚动效果
3. 插件不会干预容器和内容的样式，开发者可以自由设置样式