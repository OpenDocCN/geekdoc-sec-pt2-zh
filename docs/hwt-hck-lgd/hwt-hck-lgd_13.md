# 第十章：10 最终自由

![](img/chapterart.png)

在上一章中，我们进行了仔细的网络侦察，识别出了 Citrix 数据库，甚至成功抓取并破解了服务账户 *sqlexpress* 的密码。在 Strat Jumbo 防御网络那充满阴暗的世界中，这一重大发现带来的激动之情，让我们迫不及待地想要使用新获取的凭证来测试我们对 Citrix 数据库的访问权限。

但是，别急！在随机服务器上开启一个新的互动会话——无论是 RDP 还是 NTLM——必须小心谨慎，特别是在 ATA 潜伏的情况下。有小概率可能会有一些管理员定期发起连接到数据库……
