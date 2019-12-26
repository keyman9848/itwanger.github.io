---
layout: post
category: life
title: 程序员，承认吧，都是你的错！
tagline: by 沉默王二
tags: 
  - 程序员
---


老读者都知道的，我没干过什么大事，无非就是敲敲代码、写写文章。还有就是及时吃饭、睡觉、打豆豆。

<!--more-->


这不，就有个哥们看不惯我了，再见之后还要撂下这句狠话：“你这种人是干不了大事的。”

![](http://www.itwanger.com/assets/images/2019/12/programmer-mistake-2.png)


好吧，我承认，都是我的错！我真没想过要干什么大事。我觉得打打杂，扫扫地挺好的。我估计我来到这个世界上的时候，父母也没对我抱太大的期望，否则清华北大没录取我这事会把他们气疯掉的。事实上，即便我只考了个大专，他们仍然没有抛弃我、放弃我。

**不知道大家有没有看过《西西里岛的美丽传说》，漂亮的女主人公（女神）被生活无情的摧残，但最后，她仍然对那些欺辱过她的女人报以纯洁的微笑**。

我对这位贬低我的哥们也报以微笑（😊），快，看我的表情，纯洁吧？那为什么我还要提这件事呢？难道不是因为我小肚鸡肠、耿耿于怀？还真不是的，我只是想引（che）出本篇文章的主题：**程序员，承认吧，都是你的错**！

（看我耍了多么大的心机）


不知道大家有没有过这样的体验：明明程序在本地测试通过，运行的好好的；但不知道为什么在正式环境下就偏偏有问题，不仅见了鬼，还奇了怪！

我们找啊找，费了老大的劲儿，可还是找不到原因。问题把我们折腾得够呛，于是我们只好摊摊手，摇摇头，叹口气，很难为情地扔下一句狠话：“**这特么肯定是环境有问题**。”

是的，对于大多数的项目来说，代码里常常混杂着很多东西：团队其他成员的代码、第三方类库、数据库链接、网络通信等等，以及程序运行的平台环境。

对于大多数的程序员来说，不得不面对的一个沉重的事实就是，工作中用的电脑是 Windows 操作系统，而项目正式部署的环境是 Linux 操作系统。跨平台之间的差异，有的时候能把我们搞崩溃。

早年间我做过一个大宗期货交易平台，某一家客户为服务器端提供的环境是 Windows，某一家客户提供的是 Linux。代码打成 的 war 包几乎没有任何差别，唯一差别就是几个配置参数不一样。Linux 的运行的好好的，但 Windows 就很不幸了，Web 版的首页打开几乎要一分钟之久，那种什么事也干不了的等待几乎能把所有的用户杀死在摇篮中。

当时我很傻很天真，脑子也没怎么动，心思全放在如何减轻首页加载的资源上面。把 CSS 压缩、把 JavaScript 压缩、减少请求的访问数目、图片懒加载、缓存、减轻数据库的压力等等，我能想到的办法都试了试，但几乎于事无补——首页的访问速度没有什么明显的改善。

经过一周时间的琢磨，我打算放弃了，差点愤怒地把键盘砸坏（握紧双拳，用力地砸下去）——大家有过那种要发泄情绪的时候吗？

很无助，就像少年派和一只吃人的老虎飘荡在同一条救生船上一样的无助！

**这特么肯定是环境有问题**。

但我决定忍住，于是我又花了一周的时间研究了很多其他性能优化的方案，虽然最后仍然没起多大用处。没办法，我终于妥协了。我开始和客户沟通，问他们能不能提供一个 Linux 环境的服务器。大家猜客户怎么说？他们说不用再提供，只需要一键切换就可以把 Windows 切换成 Linux，云服务器都有这种功能。what？

然后，我迫不及待地重新安装了 Linux 版的 JDK、MySQL、Tomcat，把之前在 Windows 上运行的 war 包往上面一扔，然后启动 Tomcat，大家猜结果怎么样？

首页访问速度和另外一台 Linux 的几乎差不多，几秒钟的事儿。当时我那个气急败坏的样子，就好像地主家生了个傻儿子一样。

从此，我就笃定一条：**只要问题搞不定，就赖环境，就赖第三方**！

后来，我在做支付宝支付的时候遇到了另外一个奇怪的问题，用户的钱已经从平台的支付宝账户上划走了，但我们平台的资金账户就是没有更新。

我当时就怀疑是支付宝的第三方 jar 包出了问题。因为系统一直运行的挺稳定的，我也没有对支付宝接口做任何的修改。

我就愤愤不平地提交了工单，质问支付宝的小哥：“你们支付宝接口是不是有问题，为什么支付宝上的账户资金已经划转了，却没有给我返回通知，导致我们平台上的资金账户没有更新？”

来来回回和小哥沟通了几次，他态度一直挺淡定、挺友好的，我却一次又一次的心虚：问题找出来了，是我不经意间修改了一行代码导致收到的通知被漏掉了（竟然忘了比较代码版本）。

当时自己那个灰头土脸的样子，真的是想找个地洞藏起来，羞愧难当啊！我至今还清楚地记得我最后回复的那句话：“对不起，是我错怪支付宝了。小哥，请见谅。”十足的勇气。

不知道那位小哥当时收到我这句真诚的道歉时会怎样想，会不会心里恶狠狠地骂一句：“又遇到一个傻X，当我们支付宝是过家家的啊。”

在我这十年程序生涯中，遇到过的 bug 多到像秋天里的蚊子一样，数也数不清，补丁打也打不完。我总结出来一条真理：**承认吧，都是你的错，问题就出在你自己写的代码里**。只有抱着这种心态，才能在最快的时间内找出问题的解决办法。

从统计学的角度来看，软件中的故障一般都是人为引起的，例外的情况少之又少。这一点在《代码大全》这本书中也曾被提到过，尽管统计的年代已经离我们很遥远了，但仍然具有借鉴意义。

>通过 1973 年和 1984 年的两次研究表明，所有上报的错误中，大约 95% 是由程序员引起的，2% 是由系统软件（编译器和操作系统）造成的，2% 是由其他软件（第三方类库）造成的，1% 是由硬件造成的。

就目前的情况来看，系统软件、第三方类库和硬件都越来越趋完善，那么相对来说，程序员肩负的责任就更大了。这大概也是程序员动不动被拿来祭天的原因了（呵呵）。

![](http://www.itwanger.com/assets/images/2019/12/programmer-mistake-3.png)

淡定淡定，就让我们做一个谦逊的程序员吧，遇到问题就毫不犹豫地从自己的代码找起，哪怕最后确定问题真的不是自己引起的，那么也为我们打足了底气，留下了确凿的证据。从另外一方面来说，这是防止别人甩锅的最好办法。

“嘿，哥们，这是我的错，就让我来把问题弄个水落石出吧！”就像我对待文章开头提到的那个抨击我的哥们来说，大家并不会觉得我不够硬气，反而只会觉得那哥们很可爱，而我很风度翩翩。

-------

好了各位读者朋友们，以上就是本文的全部内容了。**能看到这里的都是最优秀的程序员，二哥必须要伸出大拇指为你点个赞**👍。如果觉得不过瘾，还想看到更多，我再给大家推荐几篇。

[程序员的遮羞布：这个需求技术上无法实现](https://mp.weixin.qq.com/s/vGc273Mk13OX6uPGqFmClA)
[@程序员，别再迷恋多线程工作了](https://mp.weixin.qq.com/s/5BxReAzjZVqPR6ja58X9gQ)
[@程序员，请掌握这些核心生存技能](https://mp.weixin.qq.com/s/LJtNmmu9u1cLDeInK9Vp9w)

日常操作来了！如果觉得这篇文章有点用的话，**求在看、求转发**，明人不说暗话，我喜欢这种被大家伙宠爱的感觉。

one more thing！如果大家想要第一时间看到二哥更新的文章，可以扫描下方的二维码，关注我的公众号。我们下篇文章见！















