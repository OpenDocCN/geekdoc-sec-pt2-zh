

# 前言



![](img/opener.jpg)

如果世界上最强大的网络武器不是零日漏洞，而是书中最古老的伎俩呢？在这个快速发展的网络安全领域，bash 脚本一直是一个基础技能，它不仅仅是与操作系统交互的便捷方式。

由 Brian Fox 于 1989 年编写的 bash shell 被广泛应用于大多数版本的 Linux 操作系统，Linux 操作系统在全球基础设施中占据了重要份额。你会在构成互联网骨干的庞大服务器网络中找到 Linux 系统，还会看到它在执行太空任务、推动安全金融交易以及推动人工智能创新方面的应用。

Linux 的普及使得 bash 脚本成为黑客必备的技能，特别是在掌握 *依赖本地资源生活* 的艺术方面，即利用系统的本地工具和进程执行攻击，这可以帮助黑客融入合法活动中并避免被检测到。如果渗透测试员过于依赖不断增长的第三方工具库，他们将在有限的工具访问权限的限制环境中遇到困难。

Bash 脚本还使黑客能够自动化执行命令行工具。例如，它可以让黑客将多个工具串联在一起，针对多个目标运行这些工具，或策略性地安排它们的执行时间。通过编写脚本，黑客可以开发出强大、高效的渗透测试例程，以满足他们的定制需求。

无论你是渗透测试员、漏洞赏金猎人、刚刚踏入网络安全领域的学生，还是希望了解攻击者技术的防御者，这本书都会教你如何在进攻性安全参与的各个阶段利用 bash 脚本。你将学习如何编写可重用的进攻性脚本，使用 bash shell 在网络中进行操作，并深入了解 Linux 操作系统。

## 本书内容

本书首先教你 bash 语法和脚本的基础知识。然后，它将这些技能应用到针对基于 Linux 的目标网络的渗透测试的各个阶段，从初始访问到数据外泄。在这个过程中，你将探索 Linux 操作系统，并提升你的 bash 黑客技巧。

**第一章：Bash 基础** 提供了 bash 语法的高级概述，包括变量赋值、使用算术运算符、处理输入和退出码等内容。

**第二章：流程控制和文本处理** 介绍了更高级的 bash 概念，如测试条件、使用循环、将代码整合到函数中以及将命令发送到后台。你还将学习一些定制 bash 环境以进行渗透测试的方法。

**第三章：搭建黑客实验室** 引导你建立一个实验室，用于本书后续的学习。你将依赖 Kali Linux 和一个基于 Docker 的易受攻击目标环境来练习 bash 黑客技术。

**第四章：侦察** 从黑盒的角度介绍对网络进行侦察活动。你将结合黑客工具和 bash 脚本来自动化信息收集。

**第五章：漏洞扫描与模糊测试** 探讨如何使用 bash 识别和利用漏洞。你将学习编写 bash 脚本来执行扫描和模糊测试任务，这是任何渗透测试中的关键步骤。

**第六章：获得 Web Shell** 深入探讨获取低权限控制目标系统的技术，特别关注如何部署 Web Shell 和执行操作系统命令注入。你还将探索各种升级受限 Shell 环境的方法，为未来的攻击奠定基础。

**第七章：反向 Shell** 介绍反向 Shell 的建立，这是一个初步访问技术，可以将连接方向切换到远程服务器。你将了解反向 Shell 的工作原理，并利用它们获得对远程机器的稳定访问。

**第八章：本地信息收集** 探讨如何在不通过网络发送任何可能暴露你活动的包的情况下，从被攻陷的 Linux 主机收集信息。你将导航 Linux 文件目录和权限系统，收集关于用户会话的信息，查看已安装的软件，等等。

**第九章：权限提升** 讨论潜在的权限提升路径，如配置错误的权限、共享资源和其他漏洞。

**第十章：持久性** 探讨如何使你对网络的访问在环境变化时仍然具有韧性。你将窃取凭证、修改服务配置等。

**第十一章：网络探测与横向移动** 讨论在目标网络上通过“借用土地”方法访问其他服务器。

**第十二章：防御规避与数据外泄** 介绍企业环境中常见的防御安全控制。你将学习如何篡改安全工具以及通过规避手段从系统中窃取信息。

## 脚本练习

在各章中，29 个练习将促使你实践新学到的 bash 脚本技能。有些练习会带你完成完整的脚本，然后鼓励你扩展或改进它们；其他则挑战你从零开始编写自己的脚本。通过 bash，你将完成如下练习：

+   按端口号组织扫描结果（第四章）

+   解析 Web 扫描工具的输出（第五章）

+   构建一个利用操作系统命令注入漏洞的接口（第六章）

+   编写一个 SSH 暴力破解工具，攻击用户账户（第七章）

+   递归搜索文件系统中的可读日志文件（第八章）

+   恶意修改计划任务脚本（第九章）

+   创建一个恶意软件包安装程序（第十章）

+   编写一个基于频率的端口扫描器（第十一章）

+   扫描受损主机，检查是否存在防御工具（第十二章），还有更多内容

## 如何使用本书

我们鼓励你在整本书中积极实验我们介绍的技术。首先克隆本书的 GitHub 仓库，位于 *[`github.com/dolevf/Black-Hat-Bash`](https://github.com/dolevf/Black-Hat-Bash)*。这个仓库包含了按章节分类的脚本宝库，可以帮助你应用所学的内容。

但请注意，本书中呈现的技术仅用于教育目的。仅在你明确获得授权的系统上进行测试。为了安全地提升你的技能，在第三章中，我们将指导你搭建自己的实验环境，在那里你可以进行无风险的实验。
