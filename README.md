# figure-out-DOM-event-for-33
## 用到的部分JQ的APT——get()
* [.get()](https://www.jquery123.com/get/)通过检索匹配jQuery对象**得到对应的DOM元素**。

## 用到的flex-box知识MDN链接
### [Flexbox典型用例
* [Flexbox典型用例](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout/%E5%85%B8%E5%9E%8B_%E7%94%A8%E4%BE%8B_%E7%9A%84_Flexbox)
### 使用flexbox来布局web应用
* [使用flexbox来布局web应用](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_flexbox_to_lay_out_web_applications)
### flex-flow
* [flex-flow](https://developer.mozilla.org/zh-CN/docs/Web/CSS/flex-flow),CSS flex-flow 属性是 flex-direction(定义了主轴的方向(正方向或反方向)) 和 flex-wrap(指定 flex 元素单行显示还是多行显示 。如果允许换行，这个属性允许你控制行的堆叠方向) 的简写。
> flex-wrap下面这些值是可以接受的:

* nowrap
flex 的元素被摆放到到一行，这可能导致溢出 flex 容器。 cross-start  会根据 flex-direction 的值 相当于 start 或 before。
* wrap
flex 元素 被打断到多个行中。cross-start 会根据 flex-direction 的值选择等于start 或before。cross-end 为确定的 cross-start 的另一端。
* wrap-reverse
和 wrap 的行为一样，但是 cross-start 和 cross-end 互换。

### flex
* [flex](https://developer.mozilla.org/zh-CN/docs/Web/CSS/flex)，CSS属性 flex 规定了弹性元素如何伸长或缩短以适应flex容器中的可用空间。这是一个简写属性，用来设置 flex-grow(拉伸因子), flex-shrink(收缩规则) 与 flex-basis(主轴方向上的初始大小尺寸)。  
flex 属性可以指定1个，2个或3个值。  

> 单值语法: 值必须为以下其中之一:  

* 一个无单位数(<number>): 它会被当作<flex-grow>的值。  
* 一个有效的宽度(width)值: 它会被当作 <flex-basis>的值。  
* 关键字none，auto或initial.  
> 双值语法: 第一个值必须为一个无单位数，并且它会被当作 <flex-grow> 的值。第二个值必须为以下之一：  

* 一个无单位数：它会被当作 <flex-shrink> 的值。  
* 一个有效的宽度值: 它会被当作 <flex-basis> 的值。  
> 三值语法:  

* 第一个值必须为一个无单位数，并且它会被当作 <flex-grow> 的值。  
* 第二个值必须为一个无单位数，并且它会被当作  <flex-shrink> 的值。  
* 第三个值必须为一个有效的宽度值， 并且它会被当作 <flex-basis> 的值。  
> 取值
* initial
元素会根据自身宽高设置尺寸。它会缩短自身以适应 flex 容器，但不会伸长并吸收 flex 容器中的额外自由空间来适应 flex 容器 。相当于将属性设置为"flex: 0 1 auto"。
* auto
元素会根据自身的宽度与高度来确定尺寸，但是会伸长并吸收 flex 容器中额外的自由空间，也会缩短自身来适应 flex 容器。这相当于将属性设置为 "flex: 1 1 auto".
* none
元素会根据自身宽高来设置尺寸。它是完全非弹性的：既不会缩短，也不会伸长来适应 flex 容器。相当于将属性设置为"flex: 0 0 auto"。
* <'flex-grow'>
定义 flex 元素的 flex-grow 属性，详见 <number>。默认值为 0，负值无效。
* <'flex-shrink'>
定义 flex 元素的 flex-shrink 属性，详见 <number>。默认值为1，负值无效。
* <'flex-basis'>
定义 flex 元素的 flex-basis 属性。若值为0，则必须加上单位，以免被视作伸缩性。 默认值为 auto。
### flex-direction
* [flex-direction](https://developer.mozilla.org/zh-CN/docs/Web/CSS/flex-direction)
### 使用 CSS 弹性盒子
* [使用 CSS 弹性盒子](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes)
### 弹性盒子
* [弹性盒子](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Flexbox)
### CSS 流式布局
* [CSS 流式布局](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flow_Layout)

### 这里用到的主要是
  1. display: flex;
  2. flex:1;

## 代码相同部分的说明
增加类(add('active'))的代码在移除类(remove('active'))的前面，并且各自里面都有延迟函数(延迟函数(setTimeout))。

## 当都设置为true的时候
* 增加类和移除类在延迟函数(setTimeout)里面**都只有捕获阶段执行**。也就是都是**true**。说明从**外层逐步到内层，从父元素到子元素**。
* **同时在同一个DIV绑定两个事件**，增加类和移除类，并且**增加类的代码在移除类的前面**，那么就从**外**部该层**先变色**，然后**移除该层的颜色**，逐步到**内层**。
* jsbin代码[链接](http://js.jirengu.com/nobihoduzi/1/edit?html,css,js,output)

## 当都设置为false的时候
* 增加类和移除类在延迟函数(setTimeout)里面**都只有冒泡阶段执行**。也就是都是**false**。说明从**内层逐步到外层，从子元素到父元素**。
* 同时在同一个DIV绑定两个事件，增加类和移除类，并且增加类的代码在移除类的前面，那么就从**内**部该层**先变色**，然后**移除该层的颜色**，逐步到**外层**。
* jsbin代码[链接](http://js.jirengu.com/sucuxebare/1/edit?html,css,js,output)

## 当前面的增加类为false，后面的移除类为true的时候
* 增加类在延迟函数(setTimeout)里面是**冒泡阶段执行**,移除类在延迟函数(setTimeout)里面**捕获阶段执行**。DOM事件模型都是**先捕获在冒泡**。
* **除了最内层外，其他DIV没有在同一个DIV绑定两个事件**，跟**代码顺序没有关系**，但是**最内层DIV**在同一个DIV**绑定两个事件**，此时就跟代码**顺序相关**，代码在前面的就先执行，就是**队列模型**，所以**最外层**会移除类，也就是最开始没有颜色，然后到**最内层**的时候增加类，会**先变色**，然后**移除该层颜色**，然后从**内部第二层**开始从内向外部，也就是冒泡阶段增加类来添加颜色。
* jsbin代码[链接](http://js.jirengu.com/lakazurasu/1/edit?html,css,js,output)

## 当前面的增加类为true，后面的移除类为false的时候
* 增加类在延迟函数(setTimeout)里面是**捕获阶段执行**,移除类在延迟函数(setTimeout)里面**冒泡阶段执行**。DOM事件模型都是**先捕获在冒泡**。
* **除了最内层外，其他DIV没有在同一个DIV绑定两个事件**，跟**代码顺序没有关系**，但是**最内层**DIV在同一个DIV**绑定两个事件**，此时就跟**代码顺序相关**，代码在前面的就先执行，就是**队列模型**，所以**最外层**会先增加类，也就是最开始从外层到内侧依次增加颜色，到**最内层**的时候，由于事件绑定了同一个DIV，那么就是按照**代码先后顺序执行**，也就是先增加最内层的类，然后最内层移除类，也就是到**最内层**的时候会**先变色**，然后**移除该层颜色**，然后从**内部第二层**开始从内向外部，也就是冒泡阶段增加类来添加颜色。
* jsbin代码[链接](http://js.jirengu.com/zecojimibu/1/edit?html,css,js,output)








