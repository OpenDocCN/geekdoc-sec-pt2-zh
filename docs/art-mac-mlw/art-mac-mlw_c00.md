# 前言

![](img/chapterart.png)

Mac 真的会感染恶意软件吗？如果我们相信曾在 Apple.com 上发布的一条苹果市场营销声明，显然答案是否定的：

> [Mac]不会感染 PC 病毒。Mac 不容易受到困扰 Windows 系统的数千种病毒的攻击。这得益于 Mac OS X 内置的防护措施，能够在不需要你额外操作的情况下保障你的安全。^(1)

当然，这个说法相当具有误导性，值得一提的是，苹果公司很早就将其从官方网站上移除了。确实，这其中可能有一点事实依据；由于固有的跨平台不兼容性（而非苹果的“防御”），本地的 Windows 病毒通常无法在 macOS 上执行。但跨平台恶意软件早就开始同时针对 Windows 和 macOS 了。例如，2019 年，Windows 广告软件被发现在一个跨平台框架中打包，这使得它能够在 macOS 上运行。^(2)

不管市场营销的说法如何，苹果与恶意软件的共生历史由来已久。事实上，第一种“家庭电脑野病毒”——[Elk Cloner](http://virus.wikidot.com/elk-cloner)曾感染了苹果操作系统。^(3) 从那时起，针对苹果电脑的恶意软件持续滋生。如今，Mac 恶意软件已成为对终端用户和企业日益增长的威胁，已不再令人惊讶。

这种趋势的原因有很多，但其中一个简单的原因是，随着苹果在全球电脑市场份额的增长，Mac 变成了一个更加吸引机会主义黑客和恶意软件作者的目标。根据 Gartner 的统计，苹果在 2021 年第二季度单独出货超过 600 万台 Mac。^(4) 换句话说，更多的 Mac 意味着更多的目标，进而带来更多的 Mac 恶意软件。

此外，尽管我们常常认为 Mac 主要是面向消费者的设备，但它在企业中的应用正在快速增加。一份 2020 年初的[报告](https://www.applemust.com/mac-adoption-at-sap-double-as-apple-enterprise-reach-grows/)研究了这一趋势，指出苹果的系统如今已经在“财富 500 强”企业中使用。^(5) 不幸的是，这种增长也带来了旨在专门针对 macOS 企业环境的复杂恶意软件的增加，目的包括工业间谍活动等。

尽管苹果的市场份额仍然大体上落后于微软，一些研究表明，恶意威胁同样也针对 Mac，甚至更多。例如，Malwarebytes 在其“[2020 年恶意软件报告](https://resources.malwarebytes.com/files/2020/02/2020_State-of-Malware-Report-1.pdf)”中指出：

> 而且，Mac 首次超越 Windows PC，在每个终端检测到的威胁数量上领先。^(6)

一个有趣的趋势，与 macOS 日益增长的流行度相符，是攻击者将他们的 Windows 恶意软件移植到 macOS，使其能够在 Apple 的桌面平台上原生运行。事实上，2020 年超过一半的新发现的独特 macOS 恶意软件“物种”最初源自 Windows 或非 macOS 平台。^(7) 最近，已经发现一些恶意软件样本的 macOS 变种，包括 Mami、Dacls、FinSpy、IPStorm 和 GravityRAT。

那么，为什么恶意软件作者不把他们的 Windows 或 Linux 恶意软件移植到 macOS 呢？这种恶意软件已经在其他操作系统上完成特性测试并且通过了验证。通过将这类恶意软件移植到 macOS（或者简单地重新编译为 macOS 版本），攻击者可以立刻获得与一整个新目标群体的兼容性。

另一方面，攻击者似乎也在投资 macOS 专用恶意软件。例如，2020 年的一份[报告](https://www.sentinelone.com/blog/four-distinct-families-of-lazarus-malware-target-apples-macos-platform/)突显了越来越多由技术精湛的 macOS 黑客制造的 Mac 专用恶意软件攻击：

> 所有以上审查的样本出现在过去的八到十周内，证明了威胁行为者……也在跟上 Apple 平台的更新。这些攻击者不是简单地将 Windows 恶意软件移植到 macOS，而是那些专门为 Apple 平台编写定制恶意软件的 Mac 专用开发者。^(8)

正如下面的示例所展示的，这些发展导致了针对 macOS 及其用户的攻击和恶意软件的复杂化。

**零日漏洞的使用**

1.  在题为“被火焰（Firefox）烧伤：Firefox 零日漏洞植入 macOS 后门”的文章中，我写到攻击者如何利用 Firefox 零日漏洞持续部署持久的 macOS 植入程序。^(9)

    在另一份分析不同 macOS 恶意软件的报告中，TrendMicro 的研究人员指出：

    > 我们发现了一次不同寻常的感染……在我们的调查中，最显著的是发现了两个零日漏洞：一个通过 Data Vaults 的行为缺陷窃取 cookies，另一个则被用来滥用 Safari 的开发版本。^(10)

**复杂的针对性**

1.  在风 Shift APT 组织最近的攻击中，研究人员指出，“观察到 WINDSHIFT 发动了复杂且不可预测的针对特定个人的网络钓鱼攻击，并且很少针对企业环境。”^(11)

    在另一个案例中，谷歌的研究人员发现了一起特别“针对香港网站访客的攻击，这些网站属于一家媒体机构和一个知名的支持民主的劳工及政治团体。”^(12) 这次攻击被归因于国家级攻击者，该攻击（同样利用了零日漏洞）旨在偷偷感染那些政治观点与当权者不同的 macOS 用户。

**先进的隐匿技巧**

1.  在一份关于最近 Lazarus APT 小组 macOS 植入的报告中，我指出该小组的能力不断演进，正如“一个新样本能够远程下载并直接从内存执行有效负载”，从而挫败了各种基于文件的安全工具。”^(13)

    在《[FinFisher Filleted](https://objective-see.com/blog/blog_0x4F.html)》中，我讨论了一个复杂的 macOS 恶意软件，提到了使用内核级 rootkit 组件。我指出该 rootkit “包含通过将目标进程从（进程）列表中取消链接来移除目标进程的逻辑。一旦移除，进程将被隐藏。”^(14)

**绕过最近的 macOS 安全特性**

1.  在一份详细报告《All Your Macs Are Belong To Us》中，我写到了一个现在已经修补的漏洞 CVE-2021-30657，描述了恶意软件如何利用这一漏洞运行未签名和未认证的代码，“绕过所有文件隔离、Gatekeeper 和认证要求。”^(15)

    最近，我分析了另一种被 Apple 无意认证的 macOS 恶意软件。正如我在分析中所讨论的，一旦被认证，“这些恶意负载被允许运行……即使是在 macOS Big Sur 上。”^(16)

这种攻击复杂度增加的原因仍在争论之中：它是因为 Mac 用户变得更加具备威胁意识（即：不再天真）吗？还是因为先进的 macOS 安全工具的可用性增加、macOS 核心安全性的提升，或者二者的结合？

让我们用 Kaspersky《[威胁对 macOS 用户](https://securelist.com/threats-to-macos-users/93116/)》报告中的一句话来结束这一部分，这句话总结了 Mac 与恶意软件之间的辩论：

> 我们关于 macOS 威胁的统计数据提供了相当有力的证据，表明关于该操作系统完全安全的说法不过是空洞的论调。然而，反对 macOS（以及 iOS）不可攻击这一观点的最大理由是，事实上已经有针对这些操作系统个别用户及其用户群体的攻击发生。在过去几年里，我们至少看到过八个攻击活动，其组织者假定 MacBook、iPhone 及其他设备的用户并不预计会遇到专为 Apple 平台打造的恶意软件。^(17)

总的来说，很明显，Mac 恶意软件将长期存在，并以越来越复杂和隐蔽的方式出现。

## 谁应该阅读本书？

你！如果你手中拿着这本书，请继续阅读。虽然对网络安全基础知识，甚至恶意软件基础的基本了解可能帮助你从这本书中获得更多，但它们并不是必备条件。也就是说，这本书是特别针对某些群体写的，包括但不限于：

+   **学生们：** 作为一名计算机科学专业的本科生，我对计算机病毒有浓厚的兴趣，并渴望有一本这样的书。如果你正在攻读技术学位并希望深入了解恶意软件，或许是为了提升或补充你的学习，这本书就是为你准备的。

+   **Windows 恶意软件分析师：** 我的恶意软件分析师生涯始于国家安全局（NSA），在那时我研究了针对美国军事系统的 Windows 恶意软件和漏洞。离开该机构后，我开始研究 macOS 威胁，但发现这一领域缺乏相关资源。从某种意义上说，这本书旨在填补这一空白。所以，如果你是一名 Windows 恶意软件分析师，想要了解如何分析针对 macOS 系统的威胁，这本书就是为你准备的。

+   **Mac 系统管理员：** 基于 Windows 的统一企业时代已基本过去。如今，Mac 在企业中变得越来越普遍。这催生了专门的 Mac 系统管理员以及（不幸的是）专注于运行 macOS 的企业系统的恶意软件作者。如果你是一名 Mac 系统管理员，了解那些针对你所保护的系统的威胁是至关重要的。这本书旨在为你提供这样的理解（以及更多内容）。

## 本书中的内容

全面分析 Mac 恶意软件需要理解多个话题并掌握许多技能。为了以实践的方式涵盖这些内容，本书被分为三个部分。

在第一部分《Mac 恶意软件基础》中，我们将涵盖一些基础性话题，包括 Mac 恶意软件的感染途径、持久性方法和能力。

在第二部分《Mac 恶意软件分析》中，我们将过渡到更高级的话题，如静态和动态分析工具与技术。前者涉及使用各种工具在不执行样本的情况下进行检查。静态分析通常以反汇编器或反编译器结束。动态分析则是在样本执行时进行分析，使用被动监控工具和调试器。

在第三部分《分析 EvilQuest》中，你将通过对一个复杂的 Mac 恶意软件样本 EvilQuest 进行深入分析，来应用书中所教授的所有知识。这一实践部分展示了你也可以如何分析即使是复杂的恶意软件样本。

拥有这些知识，你将顺利踏上成为一名熟练的 Mac 恶意软件分析师的道路。

## 关于 Mac 恶意软件术语的说明

牛津语言词典对恶意软件的定义如下：

> 专门设计用于干扰、破坏或非法访问计算机系统的软件。^(18)

你可以简单地将恶意软件理解为任何带有恶意意图编写的软件。

就像生活中的任何事情一样，总是存在灰色地带。例如，考虑一种与共享软件捆绑在一起的广告软件，用户在没有阅读长篇协议的情况下点击“允许”后才会安装。这算不算恶意软件？广告软件的作者会认为不是；他们甚至可能声称他们的软件为用户提供了一种服务，比如投放感兴趣的广告。这个论点可能听起来很荒谬，但即便是反病毒行业也会将此类软件称为“潜在不需要的软件”，以避免法律挑战。

在本书的背景下，这种分类大致上是无关紧要的，因为我的目标是为你提供分析任何程序、二进制文件或应用程序的工具和技术，而不管它是否具有恶意性质。

## 关于安全分析恶意软件的注意事项

本书演示了许多分析 Mac 恶意软件的实践技巧。在本书的第三部分，你甚至可以跟随分析一个名为 EvilQuest 的恶意软件样本。但由于恶意软件是有害的，因此应该小心处理。

作为恶意软件分析员，我们通常会在研究过程中故意运行恶意软件。通过在各种动态分析和监控工具的密切监视下执行恶意软件，我们将能够了解恶意样本如何感染系统并持久地安装自己，以及它随后部署的有效负载。但当然，这种分析必须在一个严格控制和隔离的环境中进行。

一种方法是使用独立计算机作为专用分析机器。该机器应以最简化的方式设置，禁用诸如文件共享等服务。在网络方面，大多数恶意软件需要互联网访问才能完全功能化（例如，连接到命令与控制服务器进行任务执行）。因此，这台分析机器应该以某种方式连接到网络。至少，建议通过 VPN 路由网络流量以掩盖你的位置信息。

然而，利用独立计算机进行分析也有其缺点，包括成本和复杂性。后者在你想要将分析系统恢复到干净的基准状态时尤为明显（例如，重新运行一个样本，或在分析新样本时）。尽管你可以重新安装操作系统，或者如果使用的是 Apple 文件系统（APFS），可以恢复到基准快照，但这两者都是相当耗时的工作。

为了解决这些缺点，你可以改为利用虚拟机进行分析。像 VMWare 和 Parallels 等公司提供适用于 macOS 系统的虚拟化选项。其基本理念很简单：虚拟化一个新的操作系统实例，使其可以与底层环境隔离，并且最重要的是，可以一键恢复到其原始状态。要安装新的虚拟机，请按照每个供应商提供的说明操作。这通常涉及下载操作系统安装程序或更新程序，将其拖放到虚拟化程序中，然后继续完成其余设置。

在执行任何分析之前，确保禁用虚拟机与主机系统之间的任何共享。运行勒索软件样本时，发现它能通过共享文件夹加密主机系统上的文件，那可就太不幸了！虚拟机还提供了网络选项，例如仅主机和桥接。前者只允许与主机进行网络连接，这在各种分析情境中可能非常有用，例如当你设置本地命令和控制服务器时。

如前所述，恢复虚拟机到其原始状态的能力可以极大地加快恶意软件分析速度，因为它可以让你在分析过程中恢复到不同的阶段。首先，你应该在开始分析之前始终拍摄一个快照，以便在分析完成后，你可以将虚拟机恢复到已知的干净状态。在分析过程中，你还应该明智地使用快照，例如在允许恶意软件执行某些核心逻辑之前。如果恶意软件未能执行预期的操作（可能是因为它检测到你的分析工具并提前退出），或者你的分析工具未能收集到你所需的数据，没关系。只需恢复到快照，进行必要的更改，然后让恶意软件重新执行。

虚拟机分析方法的主要缺点是恶意软件可能包含反虚拟机逻辑。这种逻辑试图检测恶意软件是否在虚拟机中运行。如果恶意软件能够成功检测到自己正在被虚拟化，它通常会退出，试图阻止继续分析。有关识别和克服这种逻辑并继续进行基于虚拟机的分析的方法，请参见第九章。

有关设置分析环境的更多信息，包括设置隔离虚拟机的具体步骤，请参见《如何在 macOS 上逆向恶意软件而不被感染》^(19)

## 其他资源

进一步阅读，我推荐以下资源。

### 书籍

以下是我最喜欢的一些书籍，涵盖逆向工程、macOS 内部原理以及一般恶意软件分析等主题：

+   “macOS/iOS (*OS) 内部结构”三部曲，作者 Jonathan Levin（Technologeeks Press，2017）

+   *计算机病毒研究与防御艺术* 作者 Peter Szor（Addison-Wesley Professional，2005）

+   *逆向工程：逆向工程的秘密* 作者 Eldad Eilam（Wiley，2005）

+   *OS X 事件响应：脚本编写与分析* 作者 Jaron Bradley（Syngress，2016）

### 网站

以前，关于 Mac 恶意软件分析的信息在网上非常匮乏。如今，情况已经大为改观。许多网站收集了相关信息，像我自己的 Objective-See 博客也专注于 Mac 安全话题。以下是一些我最喜欢的网站的非详尽列表：

+   [`papers.put.as/`](https://papers.put.as/): 一个相当全面的关于 macOS 安全话题和恶意软件分析的论文和演示文稿档案库。

+   [`themittenmac.com/`](https://themittenmac.com/): 这是知名的 macOS 安全研究员和作者 Jaron Bradley 的网站，网站中包含了 macOS 的事件响应工具和威胁狩猎知识。

+   [`objective-see.com/blog.html`](https://objective-see.com/blog.html): 我的博客，过去五年中发布了我以及其他安全研究人员在 macOS 恶意软件、漏洞利用等话题上的研究。

## 下载本书中的恶意软件样本

如果你想深入探讨书中的内容，或者以动手实践的方式跟进（我强烈推荐），本书中提到的恶意软件样本可以从 Objective-See 的[在线恶意软件集合](https://objective-see.com/malware.html)中下载。^(20) 集合中的样本密码是 `infect3d`。

值得重申的是，这个集合包含了真实的恶意软件。请不要感染自己！或者如果感染了，至少别怪我。

## 结尾注释
