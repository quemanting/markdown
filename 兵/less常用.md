- 嵌套

```less
.myclass{
    .content{
        ul{
            li{

            }
        }
    }
}
```

- 变量和运算

```less
@width:200px;
@height:500px;
@mycolor:#ccc;
.box{
　　width:@width;
　　height:@height-50;
　　background:@mycolor;
}
//意思就height是450px,这里的计算加减乘除皆可，单位可加可不加。
```

- 混合（Mixins）

```less
.circle{
    background-color: #4CAF50;
    border-radius: 100%;
}
.small-circle{
    width: 50px;
    height: 50px;
    .circle
}
.big-circle{
    width: 100px;
    height: 100px;
    .circle
}
```

```less
//混合还支持传参
.circle(@size: 25px){
    background-color: #4CAF50;
    border-radius: 100%;

    width: @size;
    height: @size;
}
.small-circle{
    .circle
}

.big-circle{
   .circle(100px)
}
```

- **&选择器** （&引用父级）

```less
.content{
  width: 100px;
  height: 100px;
}
div {
  .content;
  &:hover {
    background-color: black;
  }
  &::after {
    content: '';
    display: block;
    visibility: hidden;
    height: 0;
    line-height: 0;
    clear: both;
  }
}
```

