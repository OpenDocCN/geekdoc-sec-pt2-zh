# 第二十二章：紧急通信

![](img/chapterart.png)

许多家庭大部分时间是分开度过的——孩子可能被送到学校，而一个或两个父母则在工作。如果在这段时间内发生了任何不安的事情，普遍的本能反应是拿起手机，相互联系并决定下一步该做什么。但是，如果在那一刻，你的手机显示的只是“无服务”或“呼叫失败”，你可能会发现自己处于困境之中。毕竟，我们现在已经不再在每个街角看到公用电话亭，大多数家庭也没有固定电话可以尝试。

无疑，无线电信基础设施也容易受到干扰。最简单的观察是，典型的手机信号塔能够处理的并发传输数量相对较少，远远少于其覆盖范围内的手机数量。因此，在发生重大恐怖袭击或其他引发大众关注的灾难事件后，大家都急于联系亲人，网络不可避免地会超负荷并崩溃。这种问题可能会持续数小时。更糟糕的是，停电、地震和飓风等自然灾害可能会让当地的通信骨干网络停运数天，直到完成物理修复。

如果家里所有成员都能独立出行并安全到家，那么失去通信的后果并不会特别严重。最糟糕的情况也许只是一些焦虑的等待。但是，也有更令人揪心的结果：想象一个自然灾害发生，两个父母急忙去接远在外地学校的小孩，结果由于道路封闭和绕行，卡在了交通中几个小时。当他们终于到达目的地时，发现教室里空无一人，周围一片混乱，似乎孩子已经和别人离开，或者可能迷路了。像这样的情况，就是为什么拥有某种形式的备用通信工具不仅仅是一种奢侈，而是非常现实的需求。

## 丢失的笔和纸艺术

在考虑紧急通信方案时，我们往往倾向于采用高科技解决方案：对讲机、卫星电话或像 goTenna 这样的实验性技术，goTenna 是一个由纽约的初创公司推出的对等网络平台。然而，遗憾的是，这些方案并不像看上去那么万能。手持无线电在拥挤的城市中范围极其有限；卫星技术费用高昂；而且，网状网络在大多数社区中并不流行，甚至在正常情况下都不可靠，更别提在停电时了。

鉴于这些障碍，与其试图复制即时通讯的便利，不如制定一个帮助家人收集信息而无需立即联系的策略。对于年幼的孩子，这个计划可以包括告诉他们在哪里等待接送以及等待多长时间，然后在天黑后去哪里避难。对于青少年和成年人，这个计划可能包含一个优先级排序的集合地点列表——比如朋友家或附近的汽车旅馆——以及每个地点等待多久的建议，或者如果需要继续上路时在哪里留个便条。由于此类指示很难记住，最好将其打印在一张塑封卡片上，并确保每个家庭成员将其随身携带在钱包、背包或手提包里。添加纸张和写作工具也很重要。

## 卫星通讯

在纸和笔之后，卫星通讯可能是最可靠的保持联系的方式——实际上，这项技术通常被那些响应自然灾害或前往世界最偏远地区的人所依赖。话虽如此，卫星*电话*并不是大多数预备者的好选择，因为这些设备和套餐都非常昂贵。设备本身大约需要$1,000，而每月的订阅费用大约是$70——大多数家庭至少需要一对设备。电池续航也相当差，通常待机两到三天后就需要充电。

更好的替代品是卫星*通讯器*，由 Garmin 旗下品牌 inReach 销售。基础的 inReach SE+设备使用全球 Iridium 网络，价格约为$400。月订阅费用大约是$12，这使得它成为一个更为合理的开支，尤其适合那些偶尔去远足或穿越没有手机信号覆盖的乡村地区的人。这些设备的电池待机时间可长达几周，存储时可保持约三年，因此充电并不是一个迫切需要的事项。

卫星通讯器允许类似于手机短信的双向通讯，尽管延迟要高得多，大约是五分钟左右。消息可以发送到其他 inReach 设备、电子邮件地址，或外部的常规电话；还会附带发送者的 GPS 坐标。还可以请求当局的紧急帮助，这在大规模灾难中可能效果有限，但在远足中受伤或迷路时可能非常宝贵。

一些消息服务依赖于地面基础设施；卫星仅仅是转发信号在订阅者和中心之间传递。经过一些调查，我相信主要的 Iridium 通信网关位于亚利桑那州的坦佩市，而他们的卫星控制设施则在弗吉尼亚州的利兹堡市。由于他们的设置方式，Garmin 的 inReach 服务器的位置更难推测，但该公司在堪萨斯州的奥莱瑟确实有一些数据中心技术员的职位。他们的其他一些职位也提到 Azure，这是微软运营的云环境；距离 Garmin 总部最近的 Azure 数据中心位于爱荷华州的西德莫因斯，所以它可能是一个合适的选择。虽然没有内部信息很难做出确定的判断，但我敢说，除非上述位置发生区域性灾难，否则你的 inReach 很可能运行良好。

## 对讲机

对讲机有点像防弹背心：对任何技术爱好者来说，奇怪得很难抗拒，但对大多数人来说却几乎没什么用。公平地说，手持对讲机*确实*比凯夫拉更实用。只是这两种工具都没有我们想象的那样运作得那么顺利。

如果发生长时间停电，手持对讲机可以成为与住在附近的朋友或亲戚联系，或者与在家附近跑腿的家庭成员保持联系的好方法。但它们的通信范围非常有限。在高层建筑环境中，直接的手持对讲机到手持对讲机通信大概能覆盖两到五个街区；在人口稠密的郊区，通常不能超过一英里。有一些方法可以扩展覆盖范围——我们稍后会讲到——但这些都需要付出代价。

通过低成本手持对讲机收听急救人员的广播来了解紧急情况也是很困难的。许多城市和郊区的应急机构已经转向频跳数字无线电系统，而且越来越多的通信内容已被加密，以防止好奇的旁观者窃听。Uniden 公司专门的$500 扫描仪可能能跟踪未加密的通信流量，但你在低成本的 BaoFeng 对讲机上听到的可能只是愤怒的调制解调器噪音，偶尔能听到零星的对话。你所在地区可能仍在使用较旧的单频系统——例如，加利福尼亚公路巡警仍依赖传统的 FM 广播——但我不认为这种情况会持续下去。业余无线电频段的通讯可能更易接触，但很少有什么值得关注的内容。在重大灾难中，大多数陌生人既无法也不愿意提供帮助，无线电波就变成了类似于你常在 Facebook 或 Nextdoor 上看到的谣言传播场所——只是没有快速验证信息真伪的方法。最终，几乎所有情况下，一台电池驱动的 AM/FM 无线电接收器，它能接收官方广播，可能更具性价比。

如果你仍然对双向无线电通信感兴趣，问问自己你和你潜在的联系人是否真心有兴趣掌握这项技术。尤其是对于需要执照的业余无线电频段，无线电设备可能会很挑剔，并且学习曲线相当陡峭，因此，可能不太现实仅仅购买一对手持设备，随便收起来，期待能顺利使用。

### 了解手持设备的覆盖范围

双向无线电的制造商常常对其产品的能力做出夸大的宣传，但在城市高层环境中，手持无线电的覆盖范围相对有限。垂直方向上，你可能能够清除建筑物的 5 到 20 层；水平上，如前所述，如果你站在街上，通常能覆盖两到五个城市街区。在郊区，情况略好些。根据住房密度和地形（山丘和商业建筑可能会阻碍信号），手持到手持的直接通信通常能在一英里的范围内实现。最后，在人口稀少的农村地区，通常可以达到三到四英里的范围——当然，如果环境不理想，这个距离也可能会减少。

初学者往往认为通过提高发射功率或安装更大天线可以显著增加设备的通信范围，但对于手持设备来说，最大范围是受基本物理原理限制的。问题很简单：大部分情况下，无线电波是沿直线传播的。通常情况下，普通身高的人在地平线上的视距大约为三英里；超过这个距离，景象就会进入地球这个我们称之为“无线电阴影”的区域。

当然，在城市和郊区环境中，地平线并不是你唯一的担忧。当你的无线电信号必须穿过石膏板或砖石时，它会遭到衰减；但更重要的是，它传播的距离越长，就越有可能遇到一个更不容易穿透的障碍物——比如金属车库门或别人家里的大型家电。同时，信号越来越微弱的情况也有可能被更接近接收者的干扰源所淹没；电动机、灯光调光器、运动传感器、荧光灯和 LED 灯具、电视、电脑和汽车点火系统等，都是需要注意的潜在干扰源。

换句话说，虽然发射功率或天线选择可能会有所不同，但效果通常令人失望；例如，从一个 2 瓦特（W）的手持设备切换到 5 瓦特的设备，可能不会让你在郊区的范围增加超过 30%，而从 5 瓦特到 8 瓦特，只是让你的电池更快耗尽。

*有效*扩展无线电范围的一个方法是达到一个更高的视角。当你这么做时，你的视野会变得更广：当你爬升到 30 英尺时，你可以看到几乎 7 英里的远处。同样重要的是，你与其他人之间的直线路径不再贴近地面，因此信号主要通过空旷空间传播，避开了许多沿途的低障碍物。

在这种方式下扩大你的通讯范围，有时大自然会帮你完成大部分工作。如果你的家位于俯瞰乡村山谷的山丘上，你可能能够毫不费力地跨越广阔的距离进行通讯。对于其他人来说，最简单的获取信号的方式可能是爬上停车结构或高楼大厦的顶端。这个解决方法并不总是方便或实用，但如果其他方法失败，它确实是一个可靠的生活技巧。另一种方法是在家中建立一个基站，将天线安装在高杆或屋顶上；不过，这个解决方法并不总是适用于公寓生活或那些严格的业主协会规定。

从更高的视角进行传输的自然延伸是使用专门的中继设备，也称为*中继器*。在美国的大多数人口密集地区都能找到中继器（参见[`repeaterbook.com/repeaters/`](https://repeaterbook.com/repeaters/)），这些中继器通常安装在山顶或高楼上。中继器简单地监听其输入频率上的流量，然后在输出频率上进行广播。由于从你的手持设备到中继器（以及反向）的路径不贴近地面，通过中继器进行通讯的两个街面级手持设备的覆盖范围可以增加十倍甚至更多。另一方面，中继器可能会被风暴、飓风、地震等自然灾害损坏，虽然一些中继器具有应急电源，但并不是所有的都有。换句话说，中继器会给你的计划增加新的故障模式。

当从高地或使用基站或中继器进行传输时，你的通讯范围的实际上限大约是在人口密集地区达到 20 到 30 英里，或者在乡村山谷中达到 40 到 60 英里。偶尔可能会达到更远的距离，有时你可以找到一个中继器网络，它可以将你的声音传送 200 英里甚至更远——但这样的系统少之又少。

在没有可靠远程通讯的情况下，手动转发的无线电消息可以作为一种解决方法。如果你与周围的其他操作员建立友谊，他们可能愿意代表你转发信息，帮助你通过几次中转到达远方。成功的几率会增加，如果你熟悉你的无线电设备，找出常规操作员聚集的地点，并事先掌握空中礼仪。

### 无线电波段和服务类型

任何想要获得对讲机的人都必须在多种频段和服务之间做出选择。有 CB、GMRS、FRS、MURS、业余无线电等——每种服务都指定了其电磁波谱的不同部分，并且各自有不同的规则。其中一些选项非常适合应急准备，而另一些则可能会破坏原本合理的生存计划。

对于手持设备来说，无线电工作的频率对其范围和可靠性影响较小。确实，不同的电磁波谱部分具有非常不同的传播特性：Wi-Fi 信号可以穿透干墙，可见光可以穿过玻璃，而远红外线则可以毫无阻碍地穿过金属锗透镜。类似地，在某些无线电频率上，信号可以穿越海洋或反射到电离层并到达遥远的地方，而在其他波长上，则是视距传播占主导地位，一点雨水就可能妨碍信号传播。但尽管这可能指出了选择合适波长的重要性，几乎所有提供超视距信号传播的频率都需要庞大的天线，这些天线实际上无法安装在手持设备上。

在实际应用中，现代手持设备通常在两个短距离频段内工作：144 MHz 频段（也称为 2 米）和 420/430 MHz（70 厘米）；有时你还会遇到 222 MHz（1.25 米），但这相对较为罕见。这些频率的表现非常相似；在乡村环境中，2 米频段相比 70 厘米频段可能获得一些额外的范围，但差异非常小。更重要的是你选择的具体无线电服务类型。根据你购买的设备和获得的许可，你可能会在需要时拥有不同的特权和不同类型的无线电基础设施。

第一个值得提到的服务是*公民频段（CB）*无线电，这是一个古老但为大众所熟知的频段。在美国，在这里进行发射不需要明确的许可证，除了发射机本身的制造商认证之外。操作员的功率限制为 4W，且不允许使用中继器。CB 无线电使用 40 个指定频道，中心频率为 27 MHz；敏锐的读者会注意到，这个频率远低于今天手持无线电通常使用的频率。低频理论上提供了更好的传播能力，但也意味着大多数小天线的 CB 手持设备无法高效发射。这项技术更适合用于车辆和家庭，而手持设备只是一个表现不佳的附加设计。

无论如何，曾经在各种场合都很流行的 CB 现在基本上已经灭绝，除了少数长途卡车司机，他们把它当作一种路边聊天室。CB 周围有着独特的文化，拥有自己的行话和一系列反复出现的谈话话题。如果你在主要道路附近的这些频率上呼叫求助，可能会得到帮助；但除此之外，这不是每个人都喜欢的环境，可能也不是一个值得拥抱的服务。

另一类不需要特别许可的无线电是*家庭无线电服务（FRS）*。该设备在 462 至 467 MHz 之间的 22 个指定频道上工作，功率限制为 2 W。许多最便宜的“塑料包装”对讲机就是 FRS。它们没有多余的功能：您不会找到任何中继器，设备不支持数字通信，也没有什么 FRS 社区可言。这些频率在大多数地区通常很安静，除了偶尔有孩子玩弄他们在圣诞树下找到的对讲机（这已经是越来越不常见的礼物）。当您的对话伙伴不是特别懂技术且不愿意为许可证付费时，FRS 可以是一个不错的短程应急通信选择。无线电的低成本也是一个优点。

接下来是*通用移动无线电服务（GMRS）*，它是 FRS 的升级版，允许更高的传输功率并支持使用中继器。有趣的是，尽管大多数 GMRS 频道与 FRS 共享，但要使用 GMRS 无线电，您仍然需要在美国“获取许可证”。这个许可证实际上只是另一个税收：你向联邦通信委员会（FCC）支付 35 美元，然后为了你的努力获得一张纸，这张纸对你和家庭其他成员有效。

满足此要求后，您可以使用的最大传输功率为 50 W，尽管手持设备通常保持在大约 2 W。根据我所知道的情况，似乎没有明显的 GMRS 文化。该服务似乎主要用于相互认识的人的私人通信，类似于 FRS。在农场和其他农村地区相当流行，但在网络覆盖良好的地方，手机已经大部分取代了它。尽管如此，在紧急情况下，GMRS 仍然是一个可靠的选择。GMRS 中继器可以在一些大城市地区找到；要查看是否有附近的中继器，您可以访问[`mygmrs.com/browse/.`](https://mygmrs.com/browse/.)

最后一类服务——*业余无线电（ham radio）*——是一种有些不同的“存在”。从本质上讲，它是一种允许你建造几乎任何你想要的设备并以几乎任何你喜欢的方式传输的许可证，涉及的频率范围专门用于业余爱好者。获得此许可证需要通过考试，而这个考试要求你花一到两天的时间背诵一些答案——其中有些是有用的，有些则显得有些荒谬。考试过程相对简单，但你需要付出努力；你可以在[`hamstudy.org/.`](https://hamstudy.org/)上学习并安排一个由志愿者主持的考试。

业余无线电文化相对成熟，许多俱乐部维护着中继器，制定区域频率计划，建立应急响应计划等等。该服务还有一套相对完善的空中礼仪，尽管有时显得有些古怪，并且有一股实验基本数字技术的文化，包括数据包网络和键盘对键盘通讯。由于自 1990 年代以来频谱使用量下降，业余无线电操作员使用的频率通常并不拥挤，但如果你在任何大都市区域扫描一段时间，仍然能听到不少聊天声音。在危机时刻，业余无线电频段是你最有可能遇到当地其他预备者的地方。

与此同时，*业余无线电*也是更具实质性的代名词：一系列更复杂的手持式收发器，通常工作在 144 到 148 MHz 或 420/430 到 450 MHz 之间，专为那些不想局限于 CB、FRS 或 GMRS 等消费类技术的持证业余爱好者设计。传统上，这些设备来自少数几家日本制造商——雅侑（Yaesu）、爱可默（Icom）、阿林科（Alinco）和建伍（Kenwood），但近年来，业余无线电手持设备的销售已被来自中国的新兴品牌主导，其中尤以无处不在的宝锋（BaoFeng）为代表：一种售价约 25 美元的廉价无线电，在美国的极右翼和极左翼民兵中成为了一种时尚配件。根据制造商和预算的不同，这一类别中的设备从支持模拟语音传输的基础产品，到能够发送数字音频、短信、GPS 信标等更复杂设备不等。通常的最大传输功率为 5 瓦。

在继续之前，必须说明的是，确实存在一些其他小众的非商业无线电系统，但它们比前述选项更受限制，或者吸引力较小。例如，*多用途无线电服务（MURS）*仅提供五个频道，并且可供选择的消费者无线电极为稀少。

### 数字无线电与数据传输

数字通信在灾难中的价值，正如它们在日常生活中的价值一样。例如，当你最喜欢的移动应用无法使用时，连接计算机的无线电可以运行社区公告板，或者自动显示从家人处接收到的 GPS 坐标。

可惜的是，大多数消费者和业余无线电设备仍然停留在过去。它们使用模拟信号来编码声音，通过持续调整载波信号的频率或幅度来传输声波。这在一个几乎所有领域都已转向数字化的世界中，是一个罕见的时代错位。与模拟语音相比，现代数字协议需要更少的带宽、更少的传输功率，并且提供远优于模拟的声音质量。数字模式还支持可靠的高速数据传输，具备上述所有优点——以及更多。

但是今天，押注数字业余无线电仍然是有风险的。除了老一代业余无线电爱好者大多比较顽固外，还存在一种“系统战争”：三个完全不兼容的竞争者分别是由 Kenwood 和 Icom 支持的 D-STAR、由 Yaesu 支持的 System Fusion，以及源自商业用途技术的数字移动无线电（DMR）。目前很难说谁在领先。例如，Fusion 系统的中继器有很多，但这大多是因为制造商以廉价价格将它们发放给当地俱乐部；实际使用该系统的人数远低于中继器的数量。从这个角度来看，D-STAR 和 DMR 在实际使用方面可能领先，而 DMR 的增长速度更快，部分原因是来自中国的 100 美元以下无线电设备变得更容易获得。但胜者仍然难以确定。如果你今天决定选择数字无线电，就有可能赌错了马，然后为了与他人沟通，不得不转向完全不同的系统。

除了现代的数字语音和数据，*自动数据报告系统（APRS）*也值得一提。这个相对古老但仍广泛使用的数字协议用于在无线电之间发送各种短消息。这些消息可以是自动 GPS 信标、气象站报告或手动输入的文本。APRS 的巨大优势在于，许多地区有着完善的 APRS 基础设施，可以自动转播并路由消息，可能会传送到几百英里外的目的地。实际上，APRS 是一个现在真正运作的去中心化网状网络的例子。很少有无线电设备支持手持设备之间的独立 APRS 消息传递，但许多设备可以连接到笔记本电脑或手机，因此有兴趣的用户可能会觉得这是一项有趣的技术，值得进行实验。要查看你所在地区的 APRS 中继器和活动，可以访问[`aprs.fi/`](https://aprs.fi/)。

### 许可要求

许多生存主义者认为，在需要使用无线电的情况下，没人会去执行许可规定。这个观点可能有一定的道理。但如果他们今天因为担心 FCC 会突然闯入家门而避免使用未授权的无线电，他们就无法知道在灾难发生时，自己能够接收到哪些中继器信号，或者无线电在自己所在社区的实际覆盖范围。

更糟糕的是，廉价无线电设备常常会发现根本无法正确传输信号。业余无线电收发器也很容易因按错按钮而进入意外模式，恢复起来可能相当困难。说明书假设你已经知道*SSB*、*静噪音调*、*滤波器*和*VFO*的含义。这些问题并不是不可克服的，但在没有互联网可以求助的情况下，只能靠手电筒操作时，问题就不那么好玩了。

基于这些原因以及更多的考虑，想要进入业余无线电的人应该获得基本的许可证：*技术员等级*。考试很简单。部分问题虽然让人困惑且毫无意义，但很容易记住（而且你不需要满分才能通过）。如果你真的讨厌考试，选择一款可靠的 GMRS 手持设备可能是更好的选择；Midland GXT1030VP4 看起来是个不错的选择，额外的好处是，在紧急情况下它可以使用普通的 AA 电池。

对于那些选择业余无线电路线的人来说，业余无线电社区有时会显得有些古怪，许多俱乐部对于他们熟悉的事物非常保护，而且对新技术持怀疑态度。这在一定程度上可以通过人口统计来解释：许多活跃的成员都是退休人员，他们更愿意讨论前列腺检查而不是正交振幅调制数字模式。尽管如此，你其实不需要融入其中。频率并不拥挤，只要你不是个混蛋，一般不会踩到别人的脚趾。

### 超越手持设备

一些经验丰富的业余无线电爱好者可能会对本章集中讨论手持无线电感到惊讶。毕竟，他们可能会抗议，传输在高频（HF）频段（3 到 30 MHz）并使用天波传播的固定设备，能够轻松到达数百英里远的目的地！

这是事实，但强调手持设备是有意为之的。即使该技术的最终好处有限，花费 50 美元或 200 美元购买一对便携无线电来维持街头级别的通讯，也相对容易辩护。相比之下，投资数千美元购买固定的收发信机、天线塔和应急电源要难以推销，尤其是在双方都需要这么做的情况下。

严肃的业余无线电爱好者在一些灾难中可能会占据优势，擅长电子技术的预备者可能会倾向于为了兴趣而追求这一爱好。但对于大多数人来说，这些好处可能不足以让你冒险投入其中——尤其是如前所述，卫星通讯设备提供了一个可信的替代方案。
