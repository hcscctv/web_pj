# web基础pj1开发文档 

> 19302010004黄呈松

## github地址与github Pages地址
github地址：
`https://github.com/hcscctv/web_pj/`
github Pages地址
`https://hcscctv.github.io/web_pj/`

### 项目完成情况
#### - 基本要求

  1.能完美兼容chrome和Firefox浏览器

  2.支持中英文输入

  3.未使用框架

  4.完成所有要求得分点

  
#### - 要求外的完成
  1.首页图片有轮播效果（纯css）

  2.首页图片刷新键可刷新图片

  3.browser页任何搜索键可刷新搜索结果

  4.Search页选择输入方式处，选择标题搜索，会使内容搜索文
  本框失效，反之亦然
  
#### -bonus完成情况
  三点均尽量完成
##   额外完成与bonus实现方法
>将依次展示出美观以外的实现方法

#### - 首页图片轮播（html+css）
>>通过radio绑定切换图片的动画，label绑定radio，再将radio隐藏

html代码部分
```
<div class="slidershow middle">
     <div class="slides">
                <input type="radio" name="r" id="r1" checked />
                <input type="radio" name="r" id="r2" />
                <input type="radio" name="r" id="r3" />
                <input type="radio" name="r" id="r4" />

                <div class="slide s1">
                    <img>
                </div>
                <div class="slide">
                    <img>
                </div>
                <div class="slide">
                    <img>
                </div>
                <div class="slide">
                    <img>
                </div>
            </div>
            <div class="navigaion">
                <label for="r1" class="bar"></label>
                <label for="r2" class="bar"></label>
                <label for="r3" class="bar"></label>
                <label for="r4" class="bar"></label>
            </div>
        </div>
```

css部分
```
input[name="r"] {
    position: absolute;
    visibility: hidden;
}
.slides {
    width: 1000%;
    height: 100%;
    display: flex;
}
.slide {
    width: 10%;
    transition: 1.5s;
}
.slide img {
    width: 100%;
    height: 100%;
}
#r1:checked~.s1 {
    margin-left: 0;
}
#r2:checked~.s1 {
    margin-left: -10%;
}
#r3:checked~.s1 {
    margin-left: -20%;
}
#r4:checked~.s1 {
    margin-left: -30%;
}
```

#### - 首页图片刷新及搜索键刷新图片（js）
>>通过随机数获取随机图片url并设置

```
refresh_button.onclick = function() {
                var img_blocks = document.getElementsByClassName("show_pic");
                for (var i = 0; i < img_blocks.length; i++) {
                    img_blocks[i].setAttribute("src", "../../img/travel-images/normal/medium/pic (" + Math.floor(2 + Math.random() * 70) + ").jpg")
                }
            }
```
#### - .Search页选择输入方式处，选择标题搜索，会使内容搜索文本框失效，反之亦然（html+js）
>>给两个radio设置点击事件，更改文本框可用性

html部分
```html
<input type="radio" name="filter_way" id="by_title" onclick="disabled_change_a()">Filter by Title <br>
            <input id="title" type="text" disabled><br>
            <input type="radio" name="filter_way" id="by_description" onclick="disabled_change_b()">Filter by Description <br>
            <textarea name="Description" id="desc" cols="30" rows="3" disabled></textarea><br>
            <input type="submit" value="Filter" onclick="alert('imperfect system')">
```
js部分
```
function disabled_change_a() {
    document.getElementById("title").disabled = false;
    document.getElementById("desc").disabled = true;
}

function disabled_change_b() {
    document.getElementById("title").disabled = true;
    document.getElementById("desc").disabled = false;
}
```
####图片自动裁减
>>使用css中的object-fit属性

```
img{
	height:100px；//需要的高度
	width：150px；//需要的宽度
	object-fit：cover；
}

```
关于object-fit：cover
>>>被替换的内容在保持其宽高比的同时填充元素的整个内容框。如果对象的宽高比与内容框不相匹配，该对象将被剪裁以适应内容框。(引用自w3)可与非ie的浏览器兼容

####响应式布局
于各处采用不同响应式布局方式主要包括两种

1. vw vh和%作为长度单位
vw表示宽的1%，vh表示高的1% %表示相对母容器宽高，可以随着浏览器大小改变

2. @media的使用
 `@media (min-width: 767px){}`
 可以随着浏览器宽度变动使用两套css

####美化
>>本项目主要仿照样例图片效果（想不出来）
但自己参考网上已有代码设计了login和register部分

###对pj和课程建议
课上的...有点慢...

pj工作量有点少
pj就有点简单，感觉随便做做就做完了，中间也没遇到什么问题，完全不知道自己到底会了什么
