关于flex的重要性，就想告诉你，前端面试的时候肯定会问。不过别担心，flex的常用场景也就那几个（都懂的，就是面试中经常考察的），给大家整理下，方便参考。

flex是什么用来干嘛的就不多说了，在flex的知识点中，我觉得深刻理解了下面两点就能应对很多场景了：

* flex分配的是父元素的`剩余空间`

* flex-grow和flex-shrink对应的分配方式


### 固定宽度
某一侧固定宽度，另一侧自适应。

```
.parent {
  display: flex
}
.child {
  border: 1px solid #000;
  height: 200px
}
.left {
  width: 100px
}
.right {
  flex: 1
}

```
[Demo](http://jsbin.com/siwihileca/edit?html,css,output)

类似的还有左右固定，中间自适应

```
.parent {
  display: flex;
}
.child {
  border: 1px solid #000;
  height: 200px
}
.left,.right{
  width: 50px;
}
.center {
  flex: 1
}
```
[Demo](http://jsbin.com/dovekajuro/edit?html,css,output)

### 子元素等分
这个是flex最常见的考法，还记得当年做三等分时痛苦的33.33%吗？有了flex，只需几行代码就可以搞定

```
.parent {
  display: flex
}
.child {
  flex: 1;
  height: 200px;
  border: 1px solid #000
}
```

[Demo](http://jsbin.com/qekiyisixe/edit?html,css,output)

### 子元素排列
想不出名字，暂且叫这个吧。这招也是我最近新学的，目前还没有见到很多人用哦。想想以前是怎么写slider的，最早用float，后来进化一点用translate，但是都木有这招帅气

```
ul {
  display: flex;
}

li {
  width: 100%;
  flex-shrink: 0;
}
```
这个解法可以这么理解，假设父元素的宽度是100px，每个子元素的宽度也是100px，这时候flex-shrink也就是收缩比率为0，也就是超出父元素的部分不用收缩。这里需要提到另外一个属性 `flex-wrap` ，flex-wrap的默认值是nowrap，也就是不换行，在这种情况下，子元素的宽度之和超过父元素就会乖乖横向排列啦

[Demo](http://jsbin.com/fitupitugi/edit?html,css,output)

理解了flex-shrink和flex-wrap配合使用的妙处之后，上面的例子只要稍作修改，就会有完全不一样的效果

```
ul {
  display: flex;
  flex-wrap: wrap;
}

li {
  width: 100%;
  flex-shrink: 0;
}
```
酱紫就变成纵向排列啦

[Demo](http://jsbin.com/hekiwonuta/edit?html,css,output)

### 子元素对齐
flex会将容器分成水平的主轴（main axis）和垂直的交叉轴(cross axis)，其中`justify-content`用于设置弹性盒子元素在主轴（横轴）方向上的对齐方式，`align-items`属性用来设置子项在flex容器的当前行的侧轴（纵轴）方向上的对齐方式。

那么最经典的问题来了，就是水平居中的问题。这个问题的解法有很多，最优雅的可能就是flex的解法。

```
header {
  display:flex;
  justify-content:center;
  align-items:center;
}
```

[Demo](http://jsbin.com/lojigicefe/edit?html,css,output)

巧用对齐属性，还可以做两端对齐和分散对齐等效果


### 总结
相比于对各个属性值的介绍，这篇文章可能更侧重于应用和实践。当然首先要对基本属性了解，才能应用自如是吧。另外，欢迎补充！




