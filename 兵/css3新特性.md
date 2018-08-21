##### （1）CSS3 边框（Borders）

| 属性          | 说明                                                  | CSS  |
| ------------- | ----------------------------------------------------- | ---- |
| border-image  | 设置所有边框图像的速记属性。  IE10 及更早的版本不支持 | 3    |
| border-radius | 一个用于设置所有四个边框- *-半径属性的速记属性        | 3    |
| box-shadow    | 附加一个或多个下拉框的阴影                            | 3    |

```css
div{
	border:2px solid;
	border-radius:25px;
	box-shadow:10px 10px 5px #888888;
	border-image:url(border.png)30 30 round;
}
```

##### （2）CSS3 背景

 CSS3中包含几个新的背景属性，提供更大背景元素控制。 

| 顺序                                                         | 描述                     | CSS  |
| ------------------------------------------------------------ | ------------------------ | ---- |
| background-clip| 规定背景的绘制区域。     | 3    |
| background-origin | 规定背景图片的定位区域。 | 3    |
| background-size | 规定背景图片的尺寸。     | 3    |

```css
div{
	background:url(img_flwr.gif);
	background-repeat:no-repeat;
	background-size:100% 100%;
	background-origin:content-box;
}
```

多背景：

```css
body{
	background-image:url(img_flwr.gif),url(img_tree.gif);
}
```

##### （3）CSS3 渐变（gradients）

- 线性渐变（Linear Gradients）- 向下/向上/向左/向右/对角方向（IE9以下不支持）

```css
background: linear-gradient(direction, color-stop1, color-stop2, ...);
```

```css
#grad {/*从上到下渐变*/
  background: -webkit-linear-gradient(red, blue); /* Safari 5.1 - 6.0 */
  background: -o-linear-gradient(red, blue); /* Opera 11.1 - 12.0 */
  background: -moz-linear-gradient(red, blue); /* Firefox 3.6 - 15 */
  background: linear-gradient(red, blue); /* 标准的语法 */
}
#grad {/*从左到右渐变*/
  background: -webkit-linear-gradient(left, red , blue); /* Safari 5.1 - 6.0 */
  background: -o-linear-gradient(right, red, blue); /* Opera 11.1 - 12.0 */
  background: -moz-linear-gradient(right, red, blue); /* Firefox 3.6 - 15 */
  background: linear-gradient(to right, red , blue); /* 标准的语法 */
}
#grad {/*从左上角到右下角的线性渐变*/
  background: -webkit-linear-gradient(left top, red , blue); /* Safari 5.1 - 6.0 */
  background: -o-linear-gradient(bottom right, red, blue); /* Opera 11.1 - 12.0 */
  background: -moz-linear-gradient(bottom right, red, blue); /* Firefox 3.6 - 15 */
  background: linear-gradient(to bottom right, red , blue); /* 标准的语法 */
}
```

- 径向渐变（Radial Gradients）- 由它们的中心定义（IE9以下不支持）

```css
background: radial-gradient(center, shape size, start-color,...,last-color);
```

```css
#grad {/*颜色结点均匀分布的径向渐变*/
  background: -webkit-radial-gradient(red, green, blue); /* Safari 5.1 - 6.0 */
  background: -o-radial-gradient(red, green, blue); /* Opera 11.6 - 12.0 */
  background: -moz-radial-gradient(red, green, blue); /* Firefox 3.6 - 15 */
  background: radial-gradient(red, green, blue); /* 标准的语法 */
}
#grad {/*颜色结点不均匀分布的径向渐变*/
  background: -webkit-radial-gradient(red 5%, green 15%, blue 60%); /* Safari 5.1 - 6.0 */
  background: -o-radial-gradient(red 5%, green 15%, blue 60%); /* Opera 11.6 - 12.0 */
  background: -moz-radial-gradient(red 5%, green 15%, blue 60%); /* Firefox 3.6 - 15 */
  background: radial-gradient(red 5%, green 15%, blue 60%); /* 标准的语法 */
}
#grad {/*shape 参数定义了形状。它可以是值 circle 或 ellipse。其中，circle 表示圆形，ellipse 表示椭圆形。默认值是 ellipse。*/
  background: -webkit-radial-gradient(circle, red, yellow, green); /* Safari 5.1 - 6.0 */
  background: -o-radial-gradient(circle, red, yellow, green); /* Opera 11.6 - 12.0 */
  background: -moz-radial-gradient(circle, red, yellow, green); /* Firefox 3.6 - 15 */
  background: radial-gradient(circle, red, yellow, green); /* 标准的语法 */
}
```

##### （4）CSS3 文本效果

| 属性                                                         | 描述                                                    | CSS  |
| ------------------------------------------------------------ | ------------------------------------------------------- | ---- |
| hanging-punctuation | 规定标点字符是否位于线框之外。                          | 3    |
| punctuation-trim]| 规定是否对标点字符进行修剪。                            | 3    |
| text-align-last                                              | 设置如何对齐最后一行或紧挨着强制换行符之前的行。        | 3    |
| text-emphasis                                                | 向元素的文本应用重点标记以及重点标记的前景色。          | 3    |
| text-justify | 规定当 text-align 设置为 "justify" 时所使用的对齐方法。 | 3    |
| text-outline| 规定文本的轮廓。                                        | 3    |
| text-overflow| 规定当文本溢出包含元素时发生的事情。                    | 3    |
| text-shadow | 向文本添加阴影。                                        | 3    |
| text-wrap | 规定文本的换行规则。                                    | 3    |
| word-break | 规定非中日韩文本的换行规则。                            | 3    |
| word-wrap | 允许对长的不可分割的单词进行分割并换行到下一行。        | 3    |

##### （5）CSS3 字体

 	以前CSS3的版本，网页设计师不得不使用用户计算机上已经安装的字体。使用CSS3，网页设计师可以使用他/她喜欢的任何字体。当你发现您要使用的字体文件时，只需简单的将字体文件包含在网站中，它会自动下载给需要的用户。您所选择的字体在新的CSS3版本有关于@font-face规则描述。您"自己的"的字体是在 CSS3 @font-face 规则中定义的。 

```css
@font-face{
	font-family: myFirstFont;
	src: url(sansation_light.woff);
}
div{
	font-family:myFirstFont;
}
```

##### （6）CSS3 媒体查询

```css
@media not|only mediatype and (expressions) {
    CSS 代码...;
}
```

```css
/*大屏幕*/
@media screen and (min-width: 1200px) {
    body {
        background-color: brown;
    }
}
/*平板电脑与小屏电脑之间的分辨率*/
@media screen and (min-width: 768px) and (max-width:979px) {
    body {
        background-color: blue;
    }
}
/*横向放置的手机和竖向放置的平板之间的分辨率*/
@media screen and (max-width:767px) {
    body {
        background-color: blueviolet;
    }
}
/*竖向放置的手机以及分别率*/
@media screen and (max-width: 480px) {
    body {
        background-color: black;
    }
}
```

##### （7）CSS3 动画 
 @keyframes规则 

| 属性                                                         | 描述                                                     | CSS  |
| ------------------------------------------------------------ | -------------------------------------------------------- | ---- |
| @keyframes | 规定动画。                                               | 3    |
| animation | 所有动画属性的简写属性，除了 animation-play-state 属性。 | 3    |
| animation-name | 规定 @keyframes 动画的名称。                             | 3    |
| animation-duration | 规定动画完成一个周期所花费的秒或毫秒。默认是 0。         | 3    |
| animation-timing-function | 规定动画的速度曲线。默认是 "ease"。                      | 3    |
| animation-delay | 规定动画何时开始。默认是 0。                             | 3    |
| animation-iteration-count | 规定动画被播放的次数。默认是 1。                         | 3    |
| animation-direction | 规定动画是否在下一周期逆向地播放。默认是 "normal"。      | 3    |
| animation-play-state | 规定动画是否正在运行或暂停。默认是 "running"。           | 3    |

```css
@keyframes myfirst{
    0%{background: red;}
    25%{background: yellow;}
    50%{background: blue;}
    100%{background: green;}
}
div{
    animation-name: myfirst;
    animation-duration:5s;
    animation-timing-function: linear;
    animation-delay:2s;
    animation-iteration-count: infinite;
    animation-direction: alternate;
    animation-play-state: running;
    /* Safari and Chrome: */
    -webkit-animation-name: myfirst;
    -webkit-animation-duration:5s;
    -webkit-animation-timing-function: linear;
    -webkit-animation-delay:2s;
    -webkit-animation-iteration-count: infinite;
    -webkit-animation-direction: alternate;
    -webkit-animation-play-state: running;
}
```

##### （8）CSS3 过渡

| 属性                                                         | 描述                                         | CSS  |
| ------------------------------------------------------------ | -------------------------------------------- | ---- |
| transition | 简写属性，用于在一个属性中设置四个过渡属性。 | 3    |
| transition-property | 规定应用过渡的 CSS 属性的名称。              | 3    |
| transition-duration | 定义过渡效果花费的时间。默认是 0。           | 3    |
| transition-timing-function | 规定过渡效果的时间曲线。默认是 "ease"。      | 3    |
| transition-delay | 规定过渡效果何时开始。默认是 0。             | 3    |

```css
div {
    transition-property: width;
    transition-duration:1s;
    transition-timing-function: linear;
    transition-delay:2s;
    /* Safari */
    -webkit-transition-property:width;
    -webkit-transition-duration:1s;
    -webkit-transition-timing-function:linear;
    -webkit-transition-delay:2s;
}
```

