---
layout: post
title: "还没被玩坏的robobrowser(4)——从页面上抓取感兴趣的内容"
description: "从页面上抓取感兴趣的内容"
category: robobrowser
tags: [robobrowser]
---
{% include JB/setup %}

### 背景  

本节的知识实际上是属于Beautiful Soup的内容。

robobrowser支持Beautiful Soup，一般来说通过下面3个方法获取页面上感兴趣的内容

* find
* find_all
* select

这一节主要通过一些例子来讲解这几个方法


### 预备知识

一般来说学习Beautiful Soup是需要了解过滤器这个概念的。不过为了让大家能够容易理解，这里暂时屏蔽过滤器的知识，感兴趣的同学可以去官网学习一下。

### 通过例子学习 

这一节里我们的例子还是http://itest.info/courses/2，python selenium自动化测试班这个页面。

#### find方法

find方法是返回页面上符合条件的第1个元素。

```python
#coding: utf-8
import re
from robobrowser import RoboBrowser

url = 'http://itest.info/courses/2'
b = RoboBrowser(history=True)
  b.open(url)

# 通过tag name抓取

#<title>重定向科技</title>
  title = b.find('title')  
  print title.text

# 通过属性(attribute)抓取

# <img id="logo-header" src="/assets/logo-0648b8fb283a9802457da74f0c157b12.png" />
  img = b.find(id='logo-header')
  print img['src']

# <a href="/courses/4">android测试工具自制班</a>
  print b.find(href='/courses/4').text

# <li class="active">python selenium自动化测试班</li>
  print b.find(class_='active', text=re.compile('python')).text


```


### find_all方法

find_all方法的用法跟find基本相同，但是find_all会返回所有符合条件的tag的集合(ResultSet)。

```python
#coding: utf-8
import re
from robobrowser import RoboBrowser

url = 'http://itest.info/courses/2'
b = RoboBrowser(history=True)
  b.open(url)

#页面上所有的a
  all_links = b.find_all('a')  
  for link in all_links:
    print link.text

# 页面上所有class是container的div
    divs = b.find_all(class_='container')
    print divs

# limit 参数控制返回的元素个数

# 页面上前2个p
    first_two_p = b.find_all('p', limit=2)
    print first_two_p

# 如果第1个参数是列表则返回相匹配的集合

# 页面上所有的meta和title
    print b.find_all(['meta', 'img'])


```

### select方法

select方法是我最喜欢的方法，该方法支持css选择器(可惜不是全部)，返回的是list。

```python
#coding: utf-8
import re
from robobrowser import RoboBrowser

url = 'http://itest.info/courses/2'
b = RoboBrowser(history=True)
  b.open(url)

#页面上所有的a
  all_links = b.select('a')  
  for link in all_links:
    print link.text

# 页面上所有class是container的div
    divs = b.select('.container')
    print len(divs)

```

### 其他技巧

* 找到页面上所有具有id属性的元素```b.find_all(id=True)```
* 不递归查找元素。也就是说只在<html></html>的直接子后代中查找```b.find('p', recursive=False)```

文本版权归乙醇所有，欢迎转载，但请标明出处。

下一节：Beautiful Soup的过滤器
