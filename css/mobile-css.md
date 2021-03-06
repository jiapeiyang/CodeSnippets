
### 移动设备禁止缩放
在html的head中加入以下代码即可
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
```

### 禁止邮箱及电话号码自动检测
在html的head中加入以下代码即可
```html
<meta name="format-detection" content="telephone=no">

<meta name="format-detection" content="email=no">
```
[更多meta属性](http://www.qianduan.net/meta-tags-list.html)

### 图片自适应
将以下class应用于img标签上即可
```css
.image {
  display: block;
  margin: 0 auto;
  max-width: 100%;
  height: auto; /*高度会根据屏幕尺寸变化， 也可以赋予固定高度*/
}
```

### iOS Safari浏览器样式问题
* input 宽度问题
这个问题还是盒式模型的问题，添加以下css即可
```css
input[type="text"]{
   -moz-box-sizing:    border-box;
   -webkit-box-sizing: border-box;
    box-sizing:        border-box;
}
```
* button样式问题
button样式很难自定义，使用以下css代码即可禁用浏览器默认样式
```css
/*禁止webkit浏览器的默认样式*/
-webkit-appearance:none
```
```css
.btn {
  -webkit-appearance: button;
  -moz-box-sizing:    border-box;
  -webkit-box-sizing: border-box;
   box-sizing:        border-box;
}
```

### 移动设备上，给body设置`overflow:hidden;`无效
给body内的容器设置`overflow`属性则可以生效，可以使用如下代码
```css
body {
  margin: 0;
}
#container {
  overflow-x: hidden; /*禁止container横向滚动*/
}
```

### 元素在屏幕垂直居中居中
由于Android暂时不支持`display:table;`及`display:table-cell`属性，故不能适用此技巧使元素垂直居中

### 简单的离线缓存
缓存文件的格式一定要规范，如下`cache.manifest`文件内容:
```
CACHE MANIFEST
# v33 (使用更改注释的方法来更新cache)
CACHE:
  css/main.css
  css/carousel.css
  js/carousel.js
  js/album.js
  http://cdnjs.cloudflare.com/ajax/libs/zepto/1.1.3/zepto.min.js
NETWORK:
    *
```
最后两行不能丢，否则未缓存的文件可能无法正常请求。



### 禁用移动设备上按钮或者链接点击的高亮效果
使用以下css即可
```css
* {
  -webkit-tap-highlight-color: transparent;
}
```

### Retina屏幕图片优化方法

#### 使用css query media
```css
.section {
    background-image:url(http://assets.tangcha.tc/assets/v2/hero_iphone@1x-4e457d8ff22380a15d2dc53af0a84668.png);
    width: 200px;
    height: 100px;
    -webkit-background-size: 100%;
    background-size: 100%;
}

@media
(-webkit-min-device-pixel-ratio: 1.3), 
(   min--moz-device-pixel-ratio: 1.3), 
(     -o-min-device-pixel-ratio: 2.6 / 2), 
(        min-device-pixel-ratio: 1.3), 
(                min-resolution: 1.3dppx) {
    .section {
        background-image:url(http://assets.tangcha.tc/assets/v2/hero_iphone@2x-4e457d8ff22380a15d2dc53af0a84668.png);
    }
}

/* 更常见写法 */
@media
only screen and (-webkit-min-device-pixel-ratio: 2),
only screen and (   min--moz-device-pixel-ratio: 2),
only screen and (     -o-min-device-pixel-ratio: 2/1),
only screen and (        min-device-pixel-ratio: 2),
only screen and (                min-resolution: 192dpi),
only screen and (                min-resolution: 2dppx) { 
  
  /* Retina-specific stuff here */

}
```

#### 使用webkit-image-set
.section {
  background-image: -webkit-image-set(url('./bg.png') 1x, url('./bg@2x.png') 2x);
  background-position: center;
  background-repeat: no-repeat;
  height: 600px;
}


## Android browser bug
1. 低版本Android的dom.classList.remove只接受一个参数, 多个参数会被忽略