---
layout:     post
title:      "HTML及小程序学习笔记"
subtitle:   ""
date:       2021-01-11-00:00:00
author:     "Djie"
header-img: "img/ES.jpg"
tags:
  - 前端
  - 开发
---


## HTML

1.html 
<br/>2.html骨架.html 
<br/>\<!DOCTYPE html>------
<br/>\<html lang="en">----根标签
<br/>\<head></head>----------
<br/> \<meta charset="UTF-8">------utf-8能够识别Unicode码中的任意字符Unicode码：计算机领域一种规范,把所有国家的每一个字符制定了统一 
<br/> \<title>\</title>----标题 出现在浏览器的tab
<br/>\<body>\</body>----身体（内容）
<br/>3.html标签
<br/>标签分类：
<br/>双标签：开始。结束标签都有 结束标签前面有斜杠
<br/>单标签：只有开始标签
<br/>行内标签：不会独占一行
<br/>块级标签：
<br/>快捷键：table>tr*7>td*2
<br/>行内标签:不会独占一行
<br/>块级标签：会独占一行
<br/>
<br/>4.html的关系
<br/>父子关系：：嵌套层级为一级的
<br/>后代关系：
<br/>兄弟关系：
<br/>所谓的嵌套
<br/>
<br/>5.html标签的属性
<br/>语法：在开始标签里面通过空格和
<br/>一个标签可以有多个
<br/>
<br/>
<br/>6 路径
<br/>绝对路径：绝对的
<br/>相对路径：
<br/>./当前目录
<br/>../当前目录的上一级
<br/>
<br/>
<br/>7.px
<br/>像素：设备的最小的那个点 图片最小的那个点 设备最小的那个点
<br/>设置的大小是相对于当前
<br/>
<br/>8.标签的公用属性
<br/>id class style
<br/>id:唯一的标识
<br/>class:类名1 类名2
<br/>sstyle:行类样式属性 多个属性值通过：分号隔开
<br/>
<br/>9 form相关标签
<br/>input属性type 属性值有：
<br/>text文本输入框
<br/>password 密码输入框
<br/>radio 单选按钮 但是当前input标签要写一个那name属性 
<br/>checkbox提交按钮
<br/>reset重置按钮
<br/>select 下拉框 里面的选项通过option标签来表示
<br/>textarea文本域
<br/>
<br/> 10 有序列表
<br/> 有序：orderList ol 嵌套的标签 里面的选项是通过li展现的
<br/> 无序：
<br/>1.css是什么
<br/>层叠样式表
<br/>html是网页的内容 
<br/>css 是网页的修饰
<br/>
<br/>2行内样式
<br/>style属性 有多个属性值
<br/>并且属性值是键值
<br/>键值对：width----400px
<br/>3、选择器
<br/>    标签选择器
<br/>        语法：标签名{}{}里面写样式里面的格式和行内格式一样
<br/>        如果当前页面
<br/>    ID选择器
<br/>        语法：写ID选择器之前，首先要给标签加上ID属性
<br/>        #id名{}
<br/>        同权重选择器后面的样式覆盖前面的
<br/>        ID选择器的权重比标签选择器的权重高
<br/>    类选择器
<br/>            语法：写类选择器之前，首先要给标签加上class属性
<br/>            .类名{}
<br/>    后代选择器
<br/>        语法：由多个选择器组成的，越写在前面的是祖先，越写在后面的是后代
<br/>    群组选择器
<br/>        语法：有多个选择器组成，选择器之间通过空格隔开
<br/>    交集选择器：表示的是这个标签由过个选择器组成
<br/>        语法:有多个选择器组成，选择器之间没有间隙，也没有空格隔开
<br/>4、外联样式
<br/>    首先要建立一个css文件后缀名为css
<br/>    在css文件里面写样式
<br/>    在head标签里面通过link标签的href标签引入，写的是css文件的地址
<br/>    background-color: yellow;（背景颜色）
<br/>    border-radius: 8%;（box的圆角可以使百分比也可以是px值）
<br/>5、颜色的表示方式
<br/>    单词 yellow green pink yellowgreen
<br/>    rgb(红绿蓝 值都是0-255) rgb(255,0,0)
<br/>    十六进制#000000
<br/>    数字是（0-9） 字母是（a-f）
<br/>6、盒模型
<br/>    布局的本质就是盒子
<br/>    从外到内由margin(外边距) 
<br/>    规则：上右下左，如果一边没有值他就会从对面取值
<br/>    只有一个值就表示上右下左都是同一个值
<br/>    两个值 上下为一个值
<br/>    三个值 上边为第一个值右边为第二个下边为第三个值
<br/>    border（边框） 
<br/>    padding(内边框) 边框和内容之间的距离 规则和外边距一样
<br/>    content（内容）
<br/>7、标准/IE盒模型
<br/>    标准盒模型：
<br/>        默认 我们写的css宽高度表示的是当前盒子的内容content部分
<br/>        实际的宽度是content的宽度+border（表示的是左边和右边的值）*2+padding（表示的是左边或者右边的值）*2
<br/>        IE盒模型：我们css写的宽高度表示的是当前盒子就是盒子 
<br/>        实际的宽度 content的宽度+border（表示的是左边或者的值）*2+padding（表示的是左边或者右边的值）*2
<br/>    转换：
<br/>    标准--> IE css样式：box-sizing:border-box;
<br/>    IE--> 标准 css的样式：box-sizing:content-box；
<br/>8、flex布局
<br/>    什么是flex
<br/>    flex就是css3的新特性 他增大了盒子的灵活性 让布局更加方便
<br/>
<br/>    容器：设置为flex的那个父容器
<br/>        怎么设置？display：flex
<br/>    项目：设置为flex的那个父盒子的后代
<br/>    主轴：规定垂直或者水平方向为主轴方向 默认是水平方向 项目默认按照主轴方向排列
<br/>    交叉轴：与主轴垂直的方向就是交叉轴的方向
<br/>    容器的属性：
<br/>    justify-content属性值：项目在主轴在方向上的排列方式
<br/>        flex-starrt 主轴的开始位置排列项目
<br/>        flex-end 主轴的结束位置排列项目
<br/>        center主轴方向上居中排列
<br/>        space-around在主轴方向上左边和右边位置相等
<br/>        space-between在主轴方向上项目和项目之间的空隙相等
<br/>    align-items:项目在交叉轴上的排列方式
<br/>    属性值有：  
<br/>    flex-starrt 主轴的上沿位置排列项目
<br/>    flex-end 主轴的下沿位置排列项目
<br/>    center 在中间位置排列
<br/>    stretch 项目没有高度的时候，会吧项目拉申至容器的高度
<br/>        只要项目没有设置高度就拉伸，甚至不用写stretch
<br/>        只要有高度写于不写stretch；都不会拉伸
<br/>    baseline 项目按照文字的基线对其
<br/>    项目的属性：
<br/>    flex-shribnk：项目在容器空间不足是，是否要缩小
<br/>    0不缩。1缩
<br/>    flex-grow：项目在空间很足的时候是否要拉伸
<br/>    0不拉，1拉
<br/>9、定位
<br/>    css样式属性 position：
<br/>    属性值有：
<br/>        static 静态定位 默认值
<br/>        fixed 固定定位
<br/>            要设置偏移量
<br/>            top 0
<br/>            botom 0
<br/>

## <br/>微信小程序原生

<br/>
<br/>1、app.js
<br/>  写的全局逻辑
<br/>2、app.json
<br/>  全局配置文件
<br/>3、pages放的页面
<br/>  每一个页面都是一个文件夹
<br/>  每一个页面对应4个类型的文件
<br/>  js --- js 行为
<br/>  json --- 页面配置文件 并且页面的配置比全局配置权重高
<br/>  wxml --- html 结构
<br/>  wxss --- css 样式
<br/>
<br/>  配置默认启动首页："entryPagePath": "pages/index/index"
<br/>  如果没有entryPagePath pages数组中的第一项就是默认的启动首页
<br/>4、const声明常量 var 
<br/>5、image标签 有默认的宽高320 240
<br/>6、rpx 其实就相当于px 只不过响应式的
<br/>7、!important 设置样式权重最高
<br/>8、wxml中的单标签组件后边需要斜杠 \<input type="text" />
<br/>9、在js文件中怎么获取data对象中的值
<br/>  this.data.变量名
<br/>10、如何更改data对象中的值
<br/>  this.setData({ 需要改变的变量名：改变的值 })
<br/>11、条件编译
<br/>  \<view wx:if="{{条件1}}">111\</view> 
<br/>  \<view wx:elif={{条件2}}>222 \</view>
<br/>  \<view wx:else>333\</view>
<br/>  当条件1判断成功 显示111
<br/>  条件1判断不成功 111不显示并且进入条件2的判断 条件2判断成功 显示222 
<br/>  条件2也不判断成功 就显示333
<br/>12、max-width：设置当前元素的最大宽度 在超出这个值的时候生效
<br/>13、bindtap 是绑定事件 类型是手指触摸事件
<br/>14、wx.navigateTo({url: ''}) 指的是页面的跳转  url是要跳转的页面路径
<br/>15、wx:if wx:elif wx:else 使用时要保证他们是兄弟关系