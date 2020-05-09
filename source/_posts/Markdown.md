---
title: Markdown简单语法
date: 2020-05-04 14:55:33
tags:
- Hexo
- NexT
copyright: true
categories:
- 文本处理
top: true

---


VSC中支持Markdown语法输入提示 建议使用文本编辑器做文字处理
<!--more-->
ctrl+shift+v可同步预览，并提供分屏功能
# Markdown All in One插件 
Ctrl + B	粗体
Ctrl + I	斜体
Alt + S	删除线
Ctrl + Shift + ]	标题(uplevel)
Ctrl + Shift + [	标题(downlevel)
Ctrl + M	Toggle math environment
Alt + C	Check/Uncheck task list item

# 一、标题
#为标题标识符 h1-h6为1-6个# xxxx
```
# xxxx
## xxxx
### xxxxxx
```
# 二、字体
```
**这是加粗的文字**
*这是倾斜的文字*`
***这是斜体加粗的文字***
~~这是加删除线的文字~~
```
**这是加粗的文字**
*这是倾斜的文字*`
***这是斜体加粗的文字***
~~这是加删除线的文字~~

# 三、列表
```
- 列表内容
+ 列表内容
* 列表内容
```

- 列表内容
+ 列表内容
* 列表内容

注意：- + * 跟内容之间都要有一个空格
有序列表就是数字加点加空格

# 四.超链接
```
[超链接名](超链接地址 "超链接title")
title可加可不加
```
[掘金](https://juejin.im/)
也可以直接用html里的a标签
<a href="https://juejin.im/" target="_blank">掘金</a>

```
<a href="https://juejin.im/" target="_blank">掘金</a>
```

# 五.代码块
```
 |```|
xxxxxx
 |```|
 把符号去掉。就是三个```包起代码
```
# 六.分割线
三个或者三个以上的 - 或者 * 都可以。
```
---
----
***
*****
```
---
----
***
*****
# 七、引用
>sdsdsdsdsd
sdsdsdsd
sddsd

```
>sdsdsdsdsd
sdsdsdsd
sddsd

```
写完引用后空一行，

# 八、图片
```
![图片alt](图片地址 ''图片title'')

图片alt是图片说明，可以不写,主要用于SEO优化
图片title是图片标题，当鼠标移到图片上时显示的内容。可加可不加
```
```
![MOMO辈先](https://i.loli.net/2020/05/06/DpgOhFvyioU6Ynl.png "MOMO先辈")
```
```
<img src="https://i.loli.net/2020/05/06/DpgOhFvyioU6Ynl.png" alt="MOMO先辈">一样可以实现
```
![MOMO辈先](https://i.loli.net/2020/05/06/DpgOhFvyioU6Ynl.png "MOMO先辈")
ps：之前用cnblog的图好像挂了(