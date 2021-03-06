---
id: 193
title: 浩大的工程——整理个人音乐收藏
date: 2007-01-28T23:28:52+00:00
author: oasisfeng
layout: post
guid: http://blog.oasisfeng.com/2007/01/28/music-clean-up/
permalink: /2007/01/28/music-clean-up/
dsq_thread_id:
  - "250426818"
  - "250426818"
categories:
  - Computer
tags:
  - ID3
  - MP3
  - Music
  - 'Tag&amp;Rename'
  - 千千静听
  - 酷我MP3伴侣
---
　　不知不觉间，硬盘中下载的音乐已经多达15G，它们杂乱无章的分布在不同分区的3个文件夹下。整理如此海量的音乐显然是一件浩大的工程，所以长期以来都一直借口“忙”而逃避。直到硬盘空间濒临枯竭的今天，才意识到，是时候偿还这笔债了……

　　初拟了一下思路，工程大致分三步展开：（1）归并、整理；（2）海选、淘汰；（2）ID3 Tag 和 文件名 整理

　　前两步零散耗时数天，已基本完成，过程没有什么好讲的。主要说一下第三步工作——ID3 Tag和文件名的整理，这可是一项需要点技术含量的活儿。

<!--more-->　　“工欲善其事，必先利其器”，工具对Tag清理的效率影响绝对可以超越一个数量级。所以，在以往经验的基础上，经过慎重调研，我选择了“Tag&Rename” + “酷我MP3伴侣” 的组合。之前也用过不少Tag修改工具，但在易用性和功能两方面没有能同时令我满意的，直到Tag&Rename出现在我的视野中。当初首次试用时，被其复杂的界面惊讶的瞠目结舌，但真正用过之后才体会到它的强大和便捷，“根据Tag更名文件”，“根据文件名生成Tag”和“多文件Tag编辑”构成了其功能核心，而细微体贴之处如“按照专辑更名文件夹”、“同步ID3v1/v2”、“Tag提取和复制”等让人感受到作者的用心设计，用它大批量整理个人收藏音乐中的Tag足可事半功倍。Tag&Rename的具体使用方法这里就不细说了，有同类软件操作经验的朋友应该不难上手。它适合对Tag编辑有深入需求的人群，但不推荐普通用户尝试它，因为多数情况下你可能会需要一定的时间才能适应它的操作风格和热键。

　　BTW，我觉得Tag&Rename在易用性设计上有个不大不小的疏漏——缺少“Undo”功能。一不小心改错信息，特别是在批量操作时，就只有拍脑壳了……

　　就此次工程中涉及到的音乐文件，按Tag质量大致可分为三类：

　　**1. 0day MP3标准式标签**，因为我的音乐来源目前还是以0day为主，这也是最让我头疼的。0day MP3的标签通常都算的上Perfect，但英文歌曲也就罢了，连CPOP都全部用英文书写Tag，也不知是对传统的秉承还是出于其它考虑…… 虽然这些发布小组通常在NFO文件中都会附上中文的曲目表，但我始终没有找到可以自动解析NFO并修正Tag的工具（NFO文件格式不一，我自叹还没这个水平写出程序来，如果哪位大侠有这样的工具分享，在下感激不尽！）。手动去根据NFO填写Tag可不是我所希望面对的，好在有“酷我MP3伴侣”这个软件解了我眼下的困扰，虽然偶有无法识别或者专辑错位的情况，但总的结果还是让人颇为满意的~ 🙂

　　这里顺便也提一下“酷我MP3伴侣”的几点不足之处：
  
　　（1）无条件抹除Year、Genre、Track等字段的信息。这一点是最让我无法忍受的，你识别的信息不包含这些字段倒也无妨，可拜托别把原本的信息给删掉啊！
  
　　（2）以其广告覆盖Comment字段。这本也无可厚非，但我一向尊重Release Team的Comment，所以在两者发生冲突时，我选择保留原始的Comment。
  
　　为了规避上述两个问题，我首先在Tag&Rename中用“Copy from Foucused File”按钮将Year、Genre、Track、Comment等字段缓存，然后用“酷我”识别，待识别完成后再回到Tag&Rename中恢复上述字段。

　　**2. Tag含有不完整的信息，并包含明显的广告污染（出现在Artist、Title或Album字段）**，主要出现在Web下载的一些专辑中。清理方式基本同上，可事先用Tag&Rename批量抹除广告字段。

　　**3. 无Tag，文件名缺乏意义**，大部分出现于未知来源的音乐。这时就主要依仗“酷我MP3伴侣”了，如果连它也识别不了，就只好来蛮的——“听歌词+网上搜索”。;)

　　花了2个多小时，总算把Tag给全部搞定了，真是不容易啊！看来以后要音乐进口要严格把关，进行Tag审查了……

最后，按照惯例，特别鸣谢（排名不分先后）：

[**千千静听**](http://www.ttplayer.com/)
  
　　对DTS CD的完美支持！我的Winamp、Foobar甚至WinDVD都无能为力（可能是没装插件吧……）

[**酷我MP3伴侣**](http://www.koowo.com/partner/index.htm)
  
　　赞！Tag在线识别开创了MP3音乐管理的新思路！前景广阔，可惜市场推广做的好像有些问题……

[**Tag&Rename**](http://www.softpointer.com/tr.htm)
  
　　堪称Music Tag清理的神器！

[**搜狗拼音**](http://www.sogou.com/pinyin/)
  
　　终于切身体会到网络词库的优势了~ 词库涵盖了几乎所有歌手的名字！