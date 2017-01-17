<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [需求概述](#%E9%9C%80%E6%B1%82%E6%A6%82%E8%BF%B0)
  - [关闭顶部通知条](#%E5%85%B3%E9%97%AD%E9%A1%B6%E9%83%A8%E9%80%9A%E7%9F%A5%E6%9D%A1)
  - [关注“网易教育产品部”/登录](#%E5%85%B3%E6%B3%A8%E7%BD%91%E6%98%93%E6%95%99%E8%82%B2%E4%BA%A7%E5%93%81%E9%83%A8%E7%99%BB%E5%BD%95)
  - [顶部右侧导航及内容区各产品的“了解更多”](#%E9%A1%B6%E9%83%A8%E5%8F%B3%E4%BE%A7%E5%AF%BC%E8%88%AA%E5%8F%8A%E5%86%85%E5%AE%B9%E5%8C%BA%E5%90%84%E4%BA%A7%E5%93%81%E7%9A%84%E4%BA%86%E8%A7%A3%E6%9B%B4%E5%A4%9A)
  - [轮播图](#%E8%BD%AE%E6%92%AD%E5%9B%BE)
  - [左侧内容区tab切换](#%E5%B7%A6%E4%BE%A7%E5%86%85%E5%AE%B9%E5%8C%BAtab%E5%88%87%E6%8D%A2)
  - [查看课程详情](#%E6%9F%A5%E7%9C%8B%E8%AF%BE%E7%A8%8B%E8%AF%A6%E6%83%85)
  - [右侧“机构介绍”中的视频介绍](#%E5%8F%B3%E4%BE%A7%E6%9C%BA%E6%9E%84%E4%BB%8B%E7%BB%8D%E4%B8%AD%E7%9A%84%E8%A7%86%E9%A2%91%E4%BB%8B%E7%BB%8D)
  - [右侧“热门推荐”](#%E5%8F%B3%E4%BE%A7%E7%83%AD%E9%97%A8%E6%8E%A8%E8%8D%90)
  - [页面布局动态适应](#%E9%A1%B5%E9%9D%A2%E5%B8%83%E5%B1%80%E5%8A%A8%E6%80%81%E9%80%82%E5%BA%94)
- [实现要求](#%E5%AE%9E%E7%8E%B0%E8%A6%81%E6%B1%82)
  - [效果要求](#%E6%95%88%E6%9E%9C%E8%A6%81%E6%B1%82)
  - [功能要求](#%E5%8A%9F%E8%83%BD%E8%A6%81%E6%B1%82)
  - [兼容性要求](#%E5%85%BC%E5%AE%B9%E6%80%A7%E8%A6%81%E6%B1%82)
  - [HTML要求](#html%E8%A6%81%E6%B1%82)
  - [CSS要求](#css%E8%A6%81%E6%B1%82)
  - [JS要求](#js%E8%A6%81%E6%B1%82)
  - [其他要求](#%E5%85%B6%E4%BB%96%E8%A6%81%E6%B1%82)
- [说明](#%E8%AF%B4%E6%98%8E)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 需求概述
### 关闭顶部通知条
点击顶部通知条中的“X 不再提醒”后，刷新页面不再出现此通知条（使用本地cookie实现）。
### 关注“网易教育产品部”/登录

* 点击关注按钮：首先判断登录的cookie是否已设置（loginSuc）。
* 如果未设置登录cookie，则弹出登录框，使用给定的用户名和密码（需要表单验证）调用服务器Ajax登录，成功后设置登录cookie。
* 登录成功后，调用关注API，并设置关注成功的cookie（followSuc）。
* 登录后“关注”按钮变成不可点的“已关注”状态。

### 顶部右侧导航及内容区各产品的“了解更多”
点击导航中的“网易公开课”，“网易云课堂”，“中国大学MOOC”，新窗口打开对目的页面，对应的跳转链接如下，点击项的hover效果见视觉稿。点击“了解更多>”的跳转链接及打开方式相同。

* 网易公开课：http://open.163.com/
* 网易云课堂：http://study.163.com/
* 中国大学MOOC：http://www.icourse163.org/

### 轮播图
三张轮播图轮播效果：实现每5s切换图片，图片循环播放；鼠标悬停某张图片，则暂停切换；切换效果使用入场图片500ms淡入的方式。点击后新开窗口打开目的页面，对应的跳转链接如下：

* banner1：http://open.163.com/
* banner2：http://study.163.com/
* banner3：http://www.icourse163.org/

### 左侧内容区tab切换
点击“产品设计”或“编程语言”tab，实现下方课程内容的更换。tab项的hover及选中效果见视觉稿，tab项对应的课程卡片数据见本文档的数据接口列表。

### 查看课程详情
鼠标悬停“产品设计”或“编程语言”tab下的任意课程卡片，出现浮层显示该课程的课程详情；鼠标离开课程详情浮层，则浮层关闭。课程卡片即详情浮层的效果见视觉稿，课程卡片及详情数据见本文档的数据接口列表。

### 右侧“机构介绍”中的视频介绍
点击“机构介绍”中的整块图片区域，调用浮层播放介绍视频。图片的hover效果见视觉稿，浮层中调用的播放器（不做浏览器兼容,可用html5）及视频内容接口见本文档的数据接口列表。

### 右侧“热门推荐”
实现每次进入或刷新本页面，“热门推荐”模块中，接口返回20门课程数据，默认展示前10门课程，隔5秒更新一门课程，实现滚动更新热门课程的效果。课程数据接口见本文档的数据接口列表。

### 页面布局动态适应
根据浏览器窗口宽度，适应两种视觉布局尺寸。窗口宽度<1205时，使用小屏视觉布局；窗口宽度>=1205时，使用大屏视觉布局。

## 实现要求
### 效果要求
正确还原视觉效果，正确测量大小宽高距离位置等数值，文字边框背景等颜色能正确取色。

### 功能要求
按照效果图和上面的功能点完成所有功能（可以不考虑跨域问题）。

### 兼容性要求
页面兼容IE8+、FF、Chrome，允许圆角、阴影只在高版本浏览器中实现。

### HTML要求
完善的头部信息，代码缩进，正确使用语义化标签及实体，考虑SEO需要，正确嵌套标签，正确使用标签属性，规范的注释格式。

### CSS要求
CSS文件内部规范化分类，命名和格式规范化，注释清晰，合理优化代码。

### JS要求

* 本作业要求不使用任何的JS框架
* JS代码要求有统一的命名规范
* JS代码要求整洁、紧凑、可读性好 
* JS代码要求注释完整

### 其他要求
代码简洁性、通用性、扩展性、可读性、可维护性。

## 说明
通过近三个月的前端课程学习，结合平时技术积累，完成了最后的大作业并取得了优异的成绩，总算是这段时间的辛苦付出没有白费。这也仅仅是一个开始，前端的路是先平稳后曲折，在前端领域技术更新日新月异的今天，唯有掌握好基础知识，加强独立思考的能力，才不会随波逐流。同时我也把课堂教授的点点滴滴记录下来，供自己和前端爱好者参考，让我们来开启探索之旅吧^_^。

<https://dancdw.gitbooks.io/netease-front-end/content/>