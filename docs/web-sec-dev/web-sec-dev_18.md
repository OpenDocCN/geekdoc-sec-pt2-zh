# 第十六章：**不要成为共犯**

![image](img/common01.jpg)

恶意行为者在互联网上有很多藏身之处。黑客常常冒充他人，并使用被攻陷的服务器来躲避检测。本章探讨了你的网站可能如何帮助攻击者逃脱恶意行为，即使你并不是他们攻击的目标。

确保你不是网络犯罪的共犯，这样你将获得良好的网络公民分数。更实际地说，如果黑客将你的系统作为攻击其他目标的跳板，你很快就会发现你的域名和 IP 地址被主要服务列入黑名单，甚至可能会被你的托管服务商断开连接。

本章涵盖了几种可能使你成为网络恶意行为共犯的漏洞。前几个漏洞被黑客用来发送有害邮件：诈骗者常常使用*电子邮件地址伪造*来伪装发件人，并在网站上利用*开放重定向*来伪装邮件中的恶意链接。

接下来，你将看到如何将你的网站嵌入到他人页面的框架中，并作为*点击劫持*攻击的一部分。在这种类型的攻击中，你的网站被用作诱饵和替换的手段，欺骗用户点击一些有害的内容。

在前一章中，你已经了解了黑客如何利用 XML 解析器中的漏洞来触发网络请求。如果攻击者能够精心构造恶意 HTTP 请求，触发从你的服务器发出的外部网络访问，那么你就启用了*服务器端请求伪造*攻击。你将学习这种攻击类型的常见发起方式以及如何防御。

最后，你将了解恶意软件被安装到你的服务器上，进而用于*僵尸网络*的风险。你可能在不知情的情况下托管了可以被攻击者远程控制的僵尸代码！

### 电子邮件欺诈

电子邮件是通过*简单邮件传输协议（SMTP）*发送的。SMTP 最初设计中的一个重大疏漏是没有身份验证机制：电子邮件的发件人可以在`From`头部附加*任何*他们想要的电子邮件地址，直到最近，接收方无法验证发件人是否真的是他们声称的身份。

结果，当然，我们都会收到大量垃圾邮件。专家估计，约有*一半*的电子邮件是垃圾邮件——每天发送近 150 亿封垃圾邮件。垃圾邮件通常包含不需要的（且常常具有误导性）营销材料，给收件人带来麻烦。

与垃圾邮件相关的是*钓鱼*电子邮件：发件人试图欺骗收件人泄露敏感的个人信息，如密码或信用卡详情。一种常见的伎俩是向受害者发送看似是他们使用的网站的密码重置邮件，但实际重置链接指向一个*伪域名*——一个看起来与真实域名相似的域名，托管着该网站的伪造版本。假网站会在攻击者的代理下收集用户的凭据，然后将用户重定向到真实网站，使受害者毫无察觉。

更恶劣的这种类型的攻击是*精准钓鱼*（spearphishing），其中恶意电子邮件的内容是针对小范围受众量身定制的。进行这种攻击的诈骗者通常会对受害者进行详细的调查，以便能够提及同事的名字或冒充同事。*CEO 诈骗*——诈骗者冒充 C 级高管，通过电子邮件向其他员工请求电汇——根据 FBI 的数据，仅 2016 年至 2019 年间，这类诈骗就让黑客获利超过 260 亿美元。这个数字仅包括那些向执法部门报告损失的受害者。

值得庆幸的是，邮件服务提供商已经开发出复杂的算法来检测垃圾邮件和钓鱼邮件。例如，Gmail 会扫描每封传入的邮件，并迅速判断其是否合法，将任何看起来可疑的邮件发送到垃圾邮件文件夹。垃圾邮件过滤器在分类邮件时会使用许多输入：邮件和主题行中的关键词、邮件域名以及邮件正文中是否包含任何可疑的外链。

您的网站和组织可能会从自定义域发送电子邮件，因此责任在于*您*防止电子邮件被标记为垃圾邮件，并保护您的用户免受伪装成您域名的恶意电子邮件的攻击。您可以通过以下几种方式做到这一点：通过实施发件人策略框架（Sender Policy Framework，SPF）和在生成电子邮件时使用域名密钥识别邮件（DomainKeys Identified Mail，DKIM）。

#### *实施发件人策略框架*

实施*发件人策略框架（SPF）*意味着在 DNS 中将被授权从您的网页域名发送电子邮件的 IP 地址列入白名单。由于 SMTP 位于 TCP 之上，因此电子邮件发送方的 IP 地址无法像`From`头部那样被伪造。通过在您的域名记录中明确列出 IP 地址，邮件接收代理将能够验证传入的邮件是否来源于允许的来源。

列表 16-1 展示了如何在您的 DNS 记录中指定发件人策略框架。

```
v=spf1❶ ip4:192.0.2.0/24 ip4:198.51.100.123❷ a❸ -all❹
```

*列表 16-1：一个 DNS 记录，用于将授权从给定域发送电子邮件的 IP 地址范围列入白名单，作为 SPF 的一部分*

此记录将作为*.txt*记录添加到您的域名记录中。在此语法中，`v=`参数❶定义了使用的 SPF 版本。`ip4`❷和`a`❸标志指定了允许为给定域发送消息的系统：在此案例中，是一系列 IP 地址，以及对应域名的 IP 地址（由`a`标志指示）。记录末尾的`-all`标志❹告诉邮件提供商，如果前面的机制没有匹配，邮件应被拒绝。

#### *实施域名密钥识别邮件（DKIM）*

*DomainKeys*可用于为发出的邮件生成数字签名，以证明电子邮件确实是从您的域名合法发送的，并且在传输过程中没有被篡改。*域名密钥识别邮件（DKIM）*使用公钥加密技术，使用私钥为来自域名的发出邮件签名，并允许接收者通过使用托管在 DNS 中的公钥验证签名。只有发送者知道私钥，因此只有他们才能生成合法的签名。邮件接收代理将通过将电子邮件内容和托管在您域上的公钥结合来重新计算签名。如果重新计算的签名与附加在邮件上的签名不匹配，则邮件将被拒绝。

要实现 DKIM，您需要在您的域中添加一个域密钥，作为*.txt*记录。清单 16-2 显示了一个示例。

```
k=rsa;❶ p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDDmzRmJRQxLEuyYiyMg4suA❷
```

*清单 16-2：一个（公有）域名密钥托管在 DNS 系统中，相应的私钥需要与为该域名生成电子邮件的应用共享。*

在此示例中，`k`表示密钥类型❶，`p`是用于重新计算签名的公钥❷。

#### *保护您的电子邮件：实用步骤*

您的组织可能会从多个位置生成电子邮件。作为响应用户在您网站上操作的电子邮件——即事务性电子邮件——将由您的 Web 服务器软件触发，通常通过像 SendGrid 或 Mailgun 这样的电子邮件服务生成。手动编写的电子邮件将通过 Web 邮件服务（例如 Gmail）或托管在您网络上的电子邮件服务器软件（例如 Microsoft Exchange 或 Postfix）发送。您的团队也可能使用像 Mailchimp 或 TinyLetter 这样的电子邮件营销或新闻通讯服务发送电子邮件。

查阅您的服务提供商或电子邮件服务器的文档，了解如何生成并添加实现 SPF 和 DKIM 所需的 DNS 记录。实际上，您可能*已经*在使用 DKIM，因为许多事务性邮件和营销服务在您注册时要求您添加相关的 DNS 记录。当您在实施 SPF 时锁定 IP 范围和域名时，请记得考虑*所有*从您的域名发送电子邮件的软件！

### 伪装恶意链接在电子邮件中

垃圾邮件算法会检查电子邮件中的恶意链接，为了支持这一点，Webmail 提供商保持更新的域名黑名单，这些域名已知是有害的。扫描指向这些域名的链接是阻止危险电子邮件的一种常见且有效的方法。

因此，骗子们不得不想出新的手段来伪装有害链接，以防止他们的电子邮件被标记并直接发送到垃圾邮件文件夹。这样做的一种方法是使用像 Bitly 这样的 URL 缩短服务，它会将 URL 编码为更短的形式，并在用户访问链接时重定向到该网址。然而，在不断升级的垃圾邮件战争中，电子邮件扫描算法现在会*展开*指向已知 URL 缩短服务的链接，并检查最终目的地是否有害。

黑客还发现了更微妙的方式来伪装电子邮件中的恶意链接。如果你的网站可以用来伪装指向互联网上任意 URL 的链接——如果你在网站上实现了*开放重定向*——你可能会像 URL 缩短服务一样帮助黑客伪装恶意链接。你不仅会让用户容易受到钓鱼攻击，而且你发送的*真正*电子邮件可能会被垃圾邮件检测算法列入黑名单。

#### *开放重定向*

在 HTTP 中，*重定向*发生在 Web 服务器响应 `301`（临时重定向）或 `302`（永久重定向）响应代码时，并提供浏览器应导航到的 URL。重定向最常见的用途之一是，如果未经身份验证的用户尝试访问网站，重定向其到登录页面。在这种情况下，网站通常会在用户完成身份验证后发出第二次重定向*回到*原始 URL。

为了启用第二次重定向，Web 服务器必须在用户登录时记住原始目的地。通常，这通过在登录 URL 中对最终目标 URL 进行编码作为查询参数来实现。如果黑客能够在这个查询参数中编码任意 URL——换句话说，如果第二次重定向可以将用户发送到互联网上的另一个网站——这就被称为*开放重定向*。

#### *防止开放重定向*

大多数网站永远不需要重定向到外部 URL。如果你的网站的任何部分会在另一个 URL 中编码一个 URL 以将用户重定向到该目的地，你应该确保这些编码的 URL 是*相对* URL，而不是*绝对* URL：编码的链接应该指向你的网站内部，而不是外部。

相对 URL 以斜杠（*/*）开头，容易检查。黑客已经找到了一些方法，能够将绝对 URL 伪装成相对 URL，因此你的代码需要考虑到这一点。清单 16-3 展示了如何通过简单的模式匹配逻辑来检查 URL 是否为相对 URL。

```
import re
def is_relative(url):
  return re.match(r"^\/[^\/\\]"❶, url)
```

*清单 16-3：使用 Python 中的正则表达式检查链接是否为相对链接（网站内部）*

这个模式 ❶ 表示 URL 必须以斜杠开头，接下来的字符不能是另一个斜杠或反斜杠 (*\*)。检查第二个字符是为了防止像 *[www.google.com](http://www.google.com)* 这样的 URL，这些 URL 会被浏览器解释为绝对 URL；它们将自动以 *http* 或 *https* 为前缀，具体取决于页面当前使用的协议。

防止开放重定向的另一种方法是避免在查询参数中*完全*编码 URLs。如果你正在为登录后重定向编码一个 URL，考虑将该 URL 存放在临时 cookie 中，而不是查询参数中。攻击者无法轻易伪造受害者浏览器中的 cookie，因此你将关闭恶意链接的门。

#### *其他考虑事项*

某些类型的网站确实需要用户发布外部链接。例如，如果你运营一个社交新闻网站，用户经常会发布指向外部 URL 的链接。如果这适用于你的站点，使用 *Google Safe Browsing* API 检查每个 URL 是否与有害网站的黑名单匹配。

在你确保了你的电子邮件和重定向代码安全后，确保你的网页无法被其他人的恶意网站嵌套也是非常重要的。让我们看看如何保护你的用户免受点击劫持攻击。

### 点击劫持

HTML 允许网页包含另一个网页，使用 `<iframe>` 标签。这使得来自不同网页域名的内容能够以受控的方式混合，因为在框架内运行的 JavaScript 无法访问包含页面。`<iframe>` 标签常用于在网页中嵌入第三方内容——OAuth 和 CAPTCHA 小部件通常使用它们来保护 cookies。

正如互联网中的任何有用的东西一样，黑客已经找到了滥用 `<iframe>` 标签的方法。现代 CSS 允许使用 `z-index` 属性将页面元素层叠在彼此之上；具有较高 `z-index` 的元素将遮挡具有较低 `z-index` 的元素，并且首先接收点击事件。页面元素还可以使用 `opacity` 属性使其透明。通过结合这些技术，黑客可以将一个透明的 `<div>` 放置在 `<iframe>` 元素上方，然后诱使受害者点击存储在 `<div>` 中的任何内容，而不是他们认为自己正在点击的底层内容。

这种点击劫持——*点击劫持*——已经以各种方式被使用。在某些情况下，受害者被诱导打开他们的摄像头，以便攻击者能够远程观看他们。此技术的另一个变种是 *点赞劫持*，即受害者被诱导在 Facebook 上未经他们同意地点赞某些内容。在黑暗网络上出售点赞用于促销目的已成为黑客的一个重要赚钱方式。

#### *防止点击劫持*

如果您运营一个网站，您应该确保您的网站不会成为点击劫持攻击的诱饵。大多数网站根本不需要被包含在 `<iframe>` 标签中，因此您应该直接告诉浏览器这一点。现代浏览器支持 `Content-Security-Policy` 头部，允许服务器的响应指定页面不应有 `frame-ancestors`，如在示例 16-4 中所示。

```
Content-Security-Policy: frame-ancestors 'none'
```

*示例 16-4：一个告知浏览器绝不将您的网站托管在框架中的头部*

实现此策略会告知浏览器绝不将您的网站放入框架中。

如果由于某种原因您的站点确实需要包含在 `<iframe>` 中，您应该告诉浏览器 *哪些* 网站允许托管这样的框架。您可以使用相同的 `Content-Security-Policy` 头部来指定该网站可以作为其自身框架的祖先。示例 16-5 显示了如何使用关键字 `self` 来允许您的站点托管指向同一站点其他部分的 iframes。

```
Content-Security-Policy: frame-ancestors 'self'
```

*示例 16-5：一个允许网站托管其自身 iframes 的头部*

最后，如果您确实需要第三方网站能够在框架中托管您的网站，您可以像在示例 16-6 中所示的那样，列出单独的 Web 域名。

```
Content-Security-Policy: frame-ancestors example.com google.com
```

*示例 16-6：一个允许网站被* [example.com](http://example.com) *和* [google.com](http://google.com) *通过 iframe 托管的头部*

现在您已经了解了如何防范点击劫持，让我们看看攻击者如何试图从您的服务器发起恶意网络请求。

### 服务器端请求伪造

黑客进行恶意 HTTP 请求时，通常会试图掩盖这些请求的来源。例如，拒绝服务攻击——将在下一章讨论——当来自许多不同的 IP 地址时效果更佳。如果您的 Web 服务器发出外部 HTTP 请求，而黑客可以控制这些请求发送到哪些 URL，那么您的服务器就容易受到服务器端请求伪造（SSRF）攻击，黑客可以利用您的服务器发送恶意请求。

确实有一些合理的理由需要从您的服务器发出外部网络请求。如果您使用任何形式的第三方 API，这些通常通过 HTTPS 提供为 Web 服务。例如，您可能会使用服务器端 API 发送事务邮件、为搜索索引内容、在错误报告系统中记录意外错误或处理支付。然而，当攻击者能够操控服务器调用其选择的 URL 时，问题就出现了。

通常，SSRF 漏洞发生在 HTTP 请求的出站 URL 从发送给服务器的 HTTP 请求的某一部分不安全地构造时。黑客通过对网站进行*蜘蛛抓取*，访问每一页，并使用黑客工具将他们遇到的每个 HTTP 参数替换为他们控制的 URL 来检查网站是否存在 SSRF 漏洞。如果他们检测到任何 HTTP 请求发送到他们设置的陷阱 URL，他们就知道这些请求一定是从您的服务器触发的，这意味着您容易受到 SSRF 攻击。

黑客还会检查您网站是否接受 XML 内容，并使用 XML 外部实体攻击来尝试执行 SSRF。第十五章讨论了这种攻击途径。

#### *保护免受服务器端伪造（SSRF）攻击*

您可以在多个层级上保护自己免受服务器端伪造（SSRF）的攻击。第一步，也是最重要的一步，是审计您代码中所有发起外部 HTTP 请求的部分。您几乎总是能够提前知道哪些域名需要在 API 调用中被调用，因此构建 API 调用的 URL 时应该使用在配置或代码中记录的 web 域名，而不是来自客户端。确保这一点的一个方法是使用通常与大多数 API 一起免费提供的软件开发工具包（*SDK*）。

因为您应该遵循深度防御的做法——从多个重叠的方式保护自己免受漏洞攻击——所以在网络层面安装防护措施以防止 SSRF 攻击也是明智之举。在您的防火墙中将需要访问的单个域名列入白名单，禁止所有其他域名，是捕捉在代码审查过程中可能忽略的安全问题的一种好方法。

最后，考虑使用渗透测试来检测代码中的 SSRF 漏洞。这可以通过聘请外部团队来检查您网站的漏洞，或使用自动化在线工具来实现。实际上，您将使用黑客用来发现漏洞的相同工具，在他们自己有机会进行攻击之前进行检查。

### 僵尸网络

黑客总是在寻找备用的计算能力来支持他们的攻击。如果黑客成功侵入您的服务器，他们通常会安装一个*僵尸*——一种可以通过远程命令控制的恶意软件。大多数僵尸作为一个点对点网络的一部分运行——一个*僵尸网络*——它们通过加密协议相互通信。

机器人通常用于感染普通消费者设备，如笔记本电脑。然而，将机器人安装到服务器上是一笔大生意，因为服务器将为机器人提供显著更多的计算能力。骗子们会在暗网上支付高价购买可以控制僵尸网络的访问密钥。他们通常利用这些空闲的计算能力来挖掘比特币或进行*点击欺诈*——即人为地夸大网站的页面浏览量。僵尸网络还用于生成垃圾邮件或进行拒绝服务攻击（将在下一章讨论）。

#### *防范恶意软件感染*

显然，您要避免在服务器上安装任何机器人恶意软件。第六章讨论了可能允许黑客在您的服务器上安装机器人命令注入和文件上传漏洞。请确保按照本章的建议来修复这些漏洞。

此外，您还应该积极保护您的服务器免受感染。运行最新的杀毒软件将帮助您快速发现任何类型的恶意软件。监控您的外发网络访问将突出可疑活动：已安装的机器人将定期轮询其他 IP 寻找其他机器人。您还应该考虑在您的 web 服务器上运行*完整性检查器*——一种检查敏感目录中文件变化的软件。

如果您使用虚拟化服务或容器，您在这里有一个优势：系统的任何重建通常都会清除已安装的恶意软件。定期从镜像重建系统将大大帮助您防止机器人感染。

### 总结

通过以下措施避免成为他人互联网攻击的帮凶：

+   通过在您的域名记录中实施 SPF 和 DKIM 头部来保护您发送的电子邮件。

+   确保您的网站没有开放的重定向。

+   通过设置内容安全策略，防止您的网站被托管在 `<iframe>` 标签中。

+   审计您的代码，以确保服务器不能被欺骗，向攻击者选择的外部 URL 发送 HTTP 请求，并将外部网络访问列入白名单，以避免在服务器端请求伪造攻击中被利用。

+   使用虚拟化服务器、病毒扫描程序或漏洞扫描工具来检查并移除机器人。

在下一章中，您将了解黑客可能使用的暴力破解技术，该技术可能使您的 web 服务器离线：拒绝服务攻击。
