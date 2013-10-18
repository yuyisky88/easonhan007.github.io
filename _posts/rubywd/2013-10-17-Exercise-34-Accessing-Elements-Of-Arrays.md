---
layout: post
title: "练习34: 存取数组里的元素" 
description: "笨方法学ruby"
category: ruby
tags: [ruby]
---
{% include JB/setup %}

数组非常有用，但只有你存取里面的内容时，它才能发挥出作用来。你已经学会了按顺序读出数组中的内容，但如果你要得到第 5 个元素该怎么办呢？你需要知道如何存取数组中的元素。存取第一个元素的方法是这样的：

```sh
animals = ['bear', 'tiger', 'penguin', 'zebra']
bear = animals[0]
```

你定义一个 animals 的数组，然后你用` 0 `来存取第一个元素！？这是怎么回事啊？因为数学里面就是这样，所以 Ruby 的数组也是从 0 开始的。虽然看起来很奇怪，这样定义其实有它的好处。

最好的解释方式是将你平常使用数字的方式和开发人员使用数字的方式做比较。

假设你在观看上面数组中的四种动物：(` ['bear', 'tiger', 'penguin', 'zebra'] `) 的赛跑。而它们比赛的名次正好跟数组中的顺序一样。这是一场很刺激的比赛，因为这些动物没打算吃掉对方，而且比赛还真的举办起来了。结果你的朋友来晚了，他想知道谁赢了比赛，他会问你「嘿，谁是第 0 名？」吗？不会的，他会问「嘿，谁是第 1 名？」

这是因为动物的次序是很重要的。没有第一个就没有第二个，没有第二个话也不会有第三个。第零个是不存在的，因为零的意思是什么都没有。「什么都没有」怎么赢比赛嘛？完全不和逻辑。这样的数字我们称之为「序数(ordinal number)」

而开发人员不能用这种方式思考问题，因为他们可以从数组中的任何一个位置取出一个元素来。对开发人员来说，上述的数组更像是一叠卡片。如果他们 想要 tiger，就抓它出来，如果想要 zeebra，也一样抓出来。要随机地抓数组里的内容，数组的每一个元素都应该要有一个地址(address)，或者一个「索引(index)」，而最好 的方式就是使用以 0 开头的索引。相信我说的这一点吧，这种方式获取元素会更容易。而这一类的数字被称为「基数(cardinal number)」，它意味着你可以任意抓取元素，所以我们需要一个 0 号元素。

那么，这些知识对你的数组操作有什么帮助呢？很简单，每次你对自己说：「我要第 3 只动物」时，你需要将「序数」转换成「基数」，只要将前者减 1 就可以了。第 3 只动物的索引是 2，也就是 penguin。由于你一辈子都在跟序数打交道，所以你需要这种方式来获得基数，只要减 1 就都搞定了。

记住：ordinal == 有序，以 1 开始；cardinal == 随机存取，以 0 开始。

让我们练习一下。定义一个动物列表，然后跟着做后面的练习，你需要写出所指位置的动物名称。如果我用的是「first」、「second」等说法。那说明我用的是叙述，所以你需要减去 1。如果我给你的是基数 ( 0, 1, 2 )，你只要直接使用即可。

```sh
animals = ['bear', 'python', 'peacock', 'kangaroo', 'whale', 'platypus']
```

The animal at 1. The 3rd animal. The 1st animal. The animal at 3. The 5th animal. The animal at 2. The 6th animal. The animal at 4.

对于上述某一条，以这样的格式写出一个完整的句子：「The 1st animal is at 0 and is a bear.」然后倒过来念「 “The animal at 0 is the 1st animal and is a bear.」

使用 IRB 去检查你的答按。

Hint: Ruby 还有一些便利的 method 是属于在数组中存取特定元素的用法。：` animals.first `和` animals.last `。

加分练习
--------

1. 上网搜索一下关于 序数 （ordinal number) 和基数 (cardinal number) 的知识并阅读一下。 
2. 以你对于这些数字类型的了解，解释一下为什么今年是 2010 年。呢是：你不能随便挑选年份。 
3. 再写一些数组，用一样的方式做出索引，确认自己可以在两种数字之间互相翻译。 
4. 使用 IRB 检查自己的答按。 

> Warning: 会有开发人员告诉你，叫你去阅读一个叫「Dijkstra」的人写的关于数字的主题。我建议你还是不读为妙，除非你喜欢听一个在写程序这一行刚兴起时就停止了从事写程序工作的人对你大吼大叫。
