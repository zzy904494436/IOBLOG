---
title: lean-cloud的重复计数问题
date: 2019-04-24 16:22:12
categories: 前端
tags: 博客相关
---

## 阅读次数的统计
我参考了[这个文档](https://notes.doublemine.me/2015-10-21-%E4%B8%BANexT%E4%B8%BB%E9%A2%98%E6%B7%BB%E5%8A%A0%E6%96%87%E7%AB%A0%E9%98%85%E8%AF%BB%E9%87%8F%E7%BB%9F%E8%AE%A1%E5%8A%9F%E8%83%BD.html#%E9%85%8D%E7%BD%AELeanCloud)


## 发现问题

如图  
![](关于hexo-Next主题leancloud的计数问题/img_31609.png)

这个地方会有问题 出现了下面
```code
  月底次数：31:31
```
的情况，

通过查找 [lean-cloud]() 出现的地方,原因是
原来是添加了上面文档中的
![](关于hexo-Next主题leancloud的计数问题/img_31618.png)

这一条 跟 主题原来带的include 代码(86行左右)：
```code
  {% include '_third-party/analytics/lean-analytics.swig' %}
```
冲突了，
所以还是事先看看有没有这句话，有的话 就不需要做操作了！

bingo！！！

---
这次修改主要是测试多端hexo博客的同步问题 
本次blog提交自家里主机imac
---
## 以下测试 md语法：

[测试](http://www.baidu.com)  表示超链接

## 大标题

### 小标题
<!-- more -->
<!-- 标签别名 -->
{%cq%} blah blah blah {% endcq %}
空格  中文全角空格表示
---
文章标题
---

***
文章标题2*
***


> 内容     区块引用
---
>> 饮用的饮用
---
> 哈哈哈哈
---

* 1  asasd
* 2 asdasdasdasd
* 3 asdasdasdasdasdasd
列表
*内容*     表示强调内容
![Alt text](/path/to/img.jpg)  图片
![](/upload_image/20161012/1.png)

