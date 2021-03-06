---
id: 1111
title: 活用通知栏，改善Android应用运行期体验
date: 2012-09-10T19:27:51+00:00
author: oasisfeng
layout: post
guid: http://blog.oasisfeng.com/?p=1111
permalink: /2012/09/10/notification-as-part-of-android-app-runtime-ui/
categories:
  - Development
  - Mobile
tags:
  - Android
  - Google Now
  - Jelly Bean
---
Android引以为傲的最为成功的UI设计之一，就是它灵活而强大的下拉通知栏，甚至连对UI有自己独到理解的Apple，都心甘情愿效仿这一设计。

不过大部分应用开发者对通知栏的运用理解上存在一些局限，以至于没有充分发挥出这一神器对App应有的价值。比较常见的理解是，通知栏是主要是用来展现Push通知，以及在用户关闭App期间通过后台服务推送信息给给用户。这确实是目前通知栏最常见的使用场景，但却在思维上将其局限于App运行期以外的交互方式。

为什么通知栏就不可以是App**运行期间**的一种交互形式呢？对于运行期的交互途经，一般开发者首先联想到的是Activity的范畴，需要通知时使用Dialog和Toast。其实通知栏作为一种应用运行期的交互方式，具有『低骚扰』、『节省界面空间』和『长留存』三个相当明显的体验优势。

下面就举几个典型的运用场景加以说明。

**（1）App版本升级通知**

很多App的升级通知都在启动阶段通过弹出对话框提示用户，用户确认后就开始下载并安装，在此过程中用户只能眼巴巴的等待下载完成。这是一个不太友好的用户体验，尤其是对工具类App而言。如果用户冲着一个急迫的待解需求打开App，这时候弹出升级提示，一方面很容易打断用户当前的使用意图，如果用户确认升级则迟迟无法解决当时的急迫需求；另一方面，如果用户吃一堑长一智，为了尽快解决需求，而关闭升级提示对话框，那么开发者希望以此推动用户升级App的效果就大打折扣了。

这时候活用通知栏，就可以很好的化解上述矛盾了。通过异步检测新版本，并创建一个通知栏消息，既能告知用户有新版本可升级（Ticker在顶栏的滚动显示效果），又不必阻断用户当前想要完成的操作。即使用户急于解决当时的需求而忽视了升级消息，在关闭App后，升级通知仍然滞留在通知栏中，可以有效的二次提示用户进行升级。如果非Play Store渠道安装的App，与之配合的最佳交互实践是：在用户点击该消息后，通过DownloadManager在后台下载安装包，待下载完成后创建另一条通知消息，用户点击再触发安装（升级）流程。这样引入的是一种很轻的交互，不会在低配置机型上因再次启动App界面带来的响应迟缓感。

**（2）交互频繁场景下的非关键通知**

这一点在游戏中体现的尤为典型，如果在用户的紧张操作过程中，需要给用户一些不急迫的非关键性消息（例如获得头衔、好友邀请），通过通知栏来递送就有不可取代的明显优势了。过去的交互设计习惯中，往往需要引入App内的『状态栏』来显示这类消息。这样做的缺点很明显，不仅增加开发成本，占用宝贵的屏幕空间，而且多条消息也难以实现堆叠，其实状态栏的职能用通知栏来取代是非常适用的。

与之相关的一个讨巧的通知栏使用技巧是：创建一条只含Ticker文字的通知，短时间后移除，就可以达到在通知栏滚动显示一些不需要保留的即时性消息，类似过往对『状态栏』的典型使用场景。

另外，活用同ID通知的『替换』，可以将多条消息合并提供给用户，节省通知栏的空间占用，给用户留下一个谦和的体验感受。而对于仅在运行期间有意义，不需要在App不活动时保留的消息，请记得在onPause()中移除，留给用户一个洁净的通知栏。

**（3）『随叫随到』的信息区**

很多互联网App的设计中，都不乏『个人信息（User Profile）』之类常驻界面信息区，开发者往往习惯在界面上开辟一小块区域显示这类信息，点击（头像）可以进入个人资料界面。

对于一些无需较强账户认知的App（如资讯类、工具类）而言，持续占用一块屏幕区域，哪怕是ActionBar上的一个按钮，对UI设计也是奢侈的。这时，不妨考虑利用Sticky的Notification（通过 Service.startForeground() 激活），Icon用于显示用户的头像，右侧的双排文字区合理排布用户的关键信息或状态。即使觉得默认的布局不够灵活，也可以定制自己的Layout以容纳更多的信息单元，并在有限的显示面积内支持简单的交互。如果支持Jelly Bean，还可以运用更为体验友好的大尺度和富媒体通知样式，以及可定制的交互按钮（Actions）。

Tip：别忘了在应用onPause()时移除这个Sticky通知。

当然，对于这种非常规的UI设计思路的认同，可能就仁者见仁智者见智了，不过一旦采用了这种设计，就需要给用户做好积极的引导，以免用户因习惯的原因而找不着这个入口。

**（4）隐形通知**

这应该是Google Now首次引入的一种通知体验设计模式。通过使用最低的Priority（Jelly Bean）或全透明的Icon（ICS及更早版本），使该通知在用户未下拉开通知展现区时呈现出一种『隐形』的效果。

这种通知一般展现一些优先级非常低，不需要用户显式关注的消息，但可以给用户形成一种暗示，『当我需要这类信息时，可以拉开通知栏试试看，它应该就在那里』，即使用户不再需要这些信息，也可以随时『挥之即去』（ICS+）。

虽然Google Now将隐形通知使用于后台服务中，但我们完全可以将其借鉴到App运行期间，发挥其无干扰的价值。比如用于展示不希望干扰用户的相关推荐、最近的非重要App事件、频繁更新的状态、游戏中的『任务指引』等。

同样记得要在onPause()时清理不需要留存的隐形通知。

&nbsp;

将通知栏纳入App运行期的交互体验，是一种相对另类的设计思路，如果运用得当，不仅可以省下不少开发工作量，还能给用户一种略带惊艳的舒适体验。同时，需要保持清醒的是，通知栏也是一种相对紧张的资源，尤其是被国内大量常驻类App无条件霸占之后，如何掌握好通知的使用与滥用间的平衡点，也是需要一定设计智慧的。