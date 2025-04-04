# 第五章：**程序员如何工作**

![image](img/common01.jpg)

构建和维护一个网站是一个迭代过程，而非最终目标。很少有网页开发人员能够在第一次构建时就完全做好所有功能。（除非你是我的朋友 Dave；别再让我们看起来像个失败者，*Dave*。）在网页开发中，产品会不断发展，代码库变得越来越复杂，要求开发人员不断添加新功能、修复 BUG 并重构代码。重新设计是必然发生的事情。

作为一名网页开发人员，你需要以有序且规范的方式对代码库进行更改和发布。由于在面对截止日期时采取了快捷方式，安全漏洞和 BUG 常常随着时间的推移悄然出现。大多数安全漏洞的产生，并非因为缺乏开发知识，而是因为忽视了细节。

本章重点讲解如何*正确*编写安全的代码，通过遵循*软件开发生命周期（SDLC）*这一术语来描述开发团队在设计新网站功能、编写代码、测试以及发布更改时所遵循的过程。一个混乱且杂乱无章的 SDLC 将无法追踪你运行的代码及其漏洞，最终导致一个存在 Bug 和不安全的网站。然而，一个结构合理的 SDLC 能够帮助你在早期阶段就根除 Bug 和漏洞，从而保护你的最终产品免受攻击。

我们将介绍 SDLC 的五个阶段：设计与分析、编写代码、预发布测试、发布过程以及发布后的测试和观察。我们还将简要讨论如何保护*依赖项*，即我们在网站中使用的第三方软件。

### 阶段 1：设计与分析

SDLC（软件开发生命周期）并不是从编写代码开始的；它是从思考你*应该*编写什么样的代码开始的。我们将这一初始阶段称为*设计与分析*阶段：你需要分析要添加的功能，并设计其实现方式。在项目开始时，这可能仅仅是简要的设计目标草图。但当你的网站上线并运行时，你需要对更改进行更多的深思熟虑，因为你不想破坏现有用户的功能。

该阶段最重要的目标是识别代码试图解决的需求。一旦开发团队完成了代码，所有人应该能够判断新的代码更改是否正确地解决了这些需求。如果你是在为客户编写代码，这一阶段意味着与利益相关者会面，并让他们达成一致的目标清单。而对于公司或组织内部开发，主要是开发并记录你正在构建的内容的共享愿景。

*问题追踪软件*在设计和分析中非常有帮助，尤其是在你诊断和修复现有网站的 bug 时。（问题追踪器因此也被称为*bug 追踪器*。）问题追踪器将每个开发目标描述为*问题*——例如“构建客户结账页面”或“修复首页的拼写错误”。这些问题会被分配给具体的开发人员，开发人员可以根据优先级对问题进行排序，编写代码修复问题，并标记为完成。开发人员还可以将特定的代码更改与问题关联，目的是修复 bug 或添加描述在问题中的功能。对于大团队来说，经理可以使用项目管理软件对问题进行调度，以便于报告。

在写代码之前，你应该在纸上花费多少时间来解决问题是有差异的。为固件设备或核反应堆等关键系统编写软件的团队不出所料会在设计阶段花费*大量*时间，因为他们很少有机会在部署后修复代码。而网页开发人员则通常会更快地推进进度。

### 第二阶段：编写代码

完成设计和分析后，你可以进入软件开发生命周期（SDLC）的第二阶段：编写代码。你可以使用许多工具来编写代码，但应该始终将任何非一次性脚本的代码保存在*版本控制软件*（也称为*源代码管理*）中，这可以让你存储代码库的备份副本、浏览代码库的历史版本、跟踪更改，并注释你所做的代码更改。你可以通过将代码更改推送到*代码仓库*，通常通过命令行工具或其他开发工具的插件，来与团队的其他成员共享更改，然后再将它们发布到世界上。将代码更改*推送*到集中式仓库，使其他团队成员可以审查这些更改。*发布*更改意味着将它们部署到你的*生产*网站——也就是你的真实用户将看到的网站。

使用版本控制还允许你浏览当前在生产网站上运行的代码版本，这对于诊断漏洞以及调查和解决发布后发现的安全问题至关重要。当开发团队识别并解决安全问题时，他们应该检查引入漏洞的代码更改，查看这些更改是否影响了网站的其他部分。

版本控制是所有开发团队都需要使用的首要工具。（即使是只有一个开发人员的团队！）大公司通常会运行自己的版本控制服务器，而小公司和开源开发者则通常使用第三方托管服务。

#### *分布式版本控制 vs. 集中式版本控制*

存在多种源代码管理软件，每种软件的语法和功能不同。目前最流行的工具是 Git，它最初由 Linux 创始人**林纳斯·托瓦兹**（Linus Torvalds）创建，旨在帮助组织 Linux 内核的开发。Git 是一个*分布式版本控制系统*，这意味着在 Git 管理下的每一个代码副本都是一个完整的代码库。当一个新开发者第一次从团队代码库中`拉取`（下载）代码的本地副本时，他们不仅获得了代码库的最新版本，还得到了代码库的完整历史记录。

分布式源代码管理工具会跟踪开发者所做的更改，并在开发者推送代码时仅传输这些更改。这种源代码管理模型与旧的软件有所不同，后者实施了一个*集中式*服务器，开发者从中下载并向其上传整个文件。

Git 的流行，部分原因是*GitHub*，一个使得设置在线 Git 代码库并邀请团队成员变得简单的网站。用户可以在浏览器中查看存储在 GitHub 中的代码，并且可以轻松地用 Markdown 语言对其进行文档化。GitHub 还包括自己的问题跟踪器和管理竞争代码更改的工具。

#### *分支与合并代码*

源代码管理软件允许你精确控制每次更新网站时推送的代码更改。通常，代码发布是通过分支来管理的。一个*分支*是代码库的逻辑副本，可以存储在源代码控制服务器或开发者的本地代码库中。开发者可以在自己的分支上做本地更改，而不影响*主*代码库，然后在完成他们正在开发的功能或修复的 bug 后，*合并*该分支回主代码库。

**注意**

*较大的开发团队可能会有更复杂的分支方案。源代码管理软件允许你从分支中创建更多的分支，因为分支操作是廉价的。一个大团队可能会有多个开发者为同一个*功能分支*贡献代码，以进行复杂的代码更新。*

在发布之前，多个开发者可能会将不同的分支合并到主代码库中。如果他们对同一个文件做了不同的编辑，源代码管理软件会自动尝试合并这些更改。如果不同的更改无法自动合并，就会发生*合并冲突*，这时开发团队需要手动完成合并过程，一行一行地选择如何应用相互竞争的代码更改。解决合并冲突是开发者的痛苦来源：这是一项额外的工作，通常发生在你以为已经解决了一个问题之后。而通常情况下，这个问题是因为 Dave 决定在几千个 Python 文件中修改格式。（谢谢你，Dave。）

合并时机是进行*代码审查*的绝佳时机，在这期间一个或多个团队成员会检查代码更改并提供反馈。一个很好的方式来发现潜在的安全漏洞是遵循*四眼原则*，即要求两个人在发布之前查看每个代码更改。通常，一个新视角的审查者可以看到原作者没有预料到的问题。（独眼巨人是糟糕的编码者，因此建议你对他们的审查进行双重确认。）

基于 Git 的工具可以通过使用拉取请求来规范代码审查。*拉取请求*是开发者请求将代码合并到主代码库中的请求，这允许像 GitHub 这样的工具在合并发生之前确保其他开发者批准更改。（源代码管理软件通常会使拉取请求的批准取决于所有测试在持续集成系统中通过，这一点我们将在下一节讨论。）

### 阶段 3：发布前测试

SDLC 的第三个阶段是测试。只有在彻底测试并捕获所有潜在的错误，确保代码正确运行后，你才应该发布代码。一个好的测试策略是捕获软件缺陷，尤其是安全漏洞的关键，它能确保用户体验之前或黑客利用漏洞之前发现问题。任何进行代码更改的人都应该在合并或发布代码之前手动测试网站功能。这是你应当对团队所有成员期待的基本尽责行为。

在开发生命周期的早期捕获软件缺陷可以节省大量时间和精力，因此你应该用单元测试来补充手动测试。*单元测试*是代码库中的小脚本，通过执行代码库的不同部分并测试输出，来进行基本的验证。你应该在构建过程中运行单元测试，并为代码中特别敏感或频繁更改的部分编写单元测试。

保持单元测试简单，确保它们只测试代码中的独立功能。过于复杂的单元测试，一次性测试多个功能模块，往往*脆弱*，在代码变动时容易崩溃。一个好的单元测试，例如，可能会验证只有经过身份验证的用户才能访问网站的特定区域，或者密码必须满足最低复杂性要求。良好的单元测试同时也充当文档的角色，展示了代码在正确实现时应如何操作。

#### *覆盖率与持续集成*

当你运行单元测试时，它会调用你主代码库中的函数。当你运行所有单元测试时，它们执行的代码库百分比被称为你的*覆盖率*。虽然追求 100%的测试覆盖率值得称赞，但通常是不切实际的，因此在选择代码库中要编写单元测试的部分时要小心。（此外，完全的测试覆盖率并不能保证代码的正确性；仅仅因为每条代码路径都被执行了，并不意味着所有场景都已覆盖。）编写好的单元测试是一种判断力的体现，应该是更大风险评估策略的一部分。一个好的经验法则是：当你发现一个 bug 时，先编写一个单元测试来验证正确的行为，然后再修复 bug。这可以防止问题的再次发生。

一旦你有足够的测试覆盖率，你应该设置一个持续集成服务器。一个*持续集成服务器*连接到你的源代码管理库，每当代码发生变化时，它会检查出最新版本的代码，并在执行单元测试的同时运行构建过程。如果构建过程失败——可能是因为单元测试开始失败——你的开发团队会收到警报。持续集成确保你能早期发现软件缺陷并及时解决。

#### *测试环境*

一旦你完成了发布的所有代码更改，你应该将它们部署到测试环境中进行最终测试。一个*测试环境*（通常称为*预生产环境*、*预发布环境*或*质量保证环境*）应是一个完全可操作的网站副本，运行在专用服务器上。测试环境对于在发布之前发现软件缺陷（如安全漏洞）至关重要。大型开发团队通常会雇佣专门从事此类环境下软件测试的*质量保证（QA）*人员。如果你正在将不同的代码更改集成在一起，这有时被称为*集成测试*。

一个好的测试环境应尽可能与生产环境相似，以确保测试结果具有意义。你应该在相同的服务器和数据库技术上运行你的测试环境，唯一的区别应该是配置和运行的代码版本。（你仍然需要运用常识。例如，测试环境不应能够向真实用户发送电子邮件，因此根据需要对测试环境施加故意的限制。）

这个过程类似于一个戏剧演出团队在第一次面对真实观众之前进行彩排。他们在一个小型测试观众前，穿着全套戏服演出。这让他们能够在一个低风险的环境中解决演出中的最后一些问题，其中每个细节都尽可能地与真实的首演表现相似。

测试环境是安全发布的关键部分，但如果管理不当，它们本身也会带来安全风险。测试和生产环境需要在网络层面上适当*隔离*，意味着两个环境之间的通信是不可能的。你不能让攻击者通过允许他们从不安全的测试环境跳跃到生产环境，进而妥协你的网站。

测试环境通常有自己的数据库，这需要看起来真实的测试数据，以便全面测试网站的功能。生成良好测试数据的常见方法是从生产系统中复制数据。如果你这样做，要特别小心*清洗*这类数据复制，去除敏感信息，包括姓名、支付详情和密码。近年来，许多高调的数据泄露事件都是由于攻击者在测试环境中发现未完全清洗的数据而引发的。

### 阶段 4：发布过程

如果你编写的网站代码从未推送出去，那么它就没有多大意义，因此我们来讨论 SDLC 的第四阶段：发布过程。网站的*发布过程*涉及从源代码管理中提取代码，将其复制到 Web 服务器上，并（通常）重启 Web 服务器进程。实现这一过程的方式取决于你托管网站的方式以及所使用的技术。无论你采用什么方法，发布过程都需要可靠、可复现且可回滚。

*可靠的*发布过程意味着你可以确保在发布过程中部署的代码、依赖项、资源和配置文件是什么。如果发布过程不可靠，你可能并没有运行你认为正在运行的代码版本，这会构成严重的安全风险。为了确保网站能够可靠地部署文件，发布脚本通常会使用*校验和*—数字“指纹”，确保复制到服务器上的文件与源代码管理中的文件完全一致。

*可复现的*发布过程是指你可以在不同的环境中或使用不同版本的代码时重新运行，并且得到相同的结果。可复现性意味着在发布过程中减少人为错误的空间。如果发布过程需要管理员按正确的顺序完美地执行 24 个步骤，你可以预见到他们会犯错误。尽可能编写脚本并自动化发布过程！可复现的过程对于设置良好的测试环境也至关重要。

*可回退*的发布流程允许你*回滚*发布。有时，意外的突发情况会使你想要“撤销”最近的发布，并恢复到之前的版本。这个过程应该尽可能无缝。部分回滚的代码是灾难的根源，因为可能会留下不安全的配置或具有已知漏洞的软件依赖项。无论你选择什么发布流程，都需要能够可靠地回退到先前的代码版本，且操作尽量简便。

#### *发布期间标准化部署的选项*

托管公司发明了*平台即服务（PaaS）*解决方案，使得发布代码变得既简单又可靠。如果“云端”指的是在他人服务器上运行代码，那么使用“即服务”提供的解决方案指的是在他人服务器上运行代码，同时配备一些有用的自动化和管理网站。（托管公司在发明可怕的营销缩略语方面有着悠久的历史。）

Microsoft Azure、Amazon Web Services Elastic Beanstalk、Google App Engine 和 Heroku 都是 PaaS 提供商，允许开发者通过单一命令行调用发布代码。该平台几乎负责发布过程中所需的所有其他操作：设置虚拟化服务器、安装操作系统和虚拟机、运行构建过程（稍后详细介绍）、加载依赖项、将代码部署到磁盘以及重启 Web 服务器进程。你可以通过 Web 控制台或命令行监控和回滚发布，平台还会执行各种安全检查，以确保代码能顺利部署。使用基于 PaaS 的发布过程可以最小化站点的停机时间，确保代码的干净部署，并生成完整的审计日志。

PaaS 解决方案会施加一些限制。为了提供这种便利性和可靠性，它们只支持某些编程语言和操作系统。它们允许有限的服务器配置，并且不支持复杂的网络布局。因此，有时将传统应用程序调整为在这种平台上部署可能会遇到困难。

##### 基础设施即服务与 DevOps

如果你没有使用 PaaS，因为你的应用程序太复杂、太陈旧，或者成本过于高昂，通常会将代码部署到单独的服务器上。这些服务器可能是自托管的、托管在数据中心的，或者托管在*基础设施即服务（IaaS）*解决方案中，如 Amazon Elastic Compute Cloud (EC2)。在这种情况下，你需要负责编写自己的发布流程。

历史上，公司通常雇佣专职的系统管理员团队来设计和执行发布过程。然而，随着 *DevOps*（即 *开发运维*）工具的兴起，这些职责变得模糊，开发者也因此获得了更多的控制权来管理代码的部署方式。DevOps 工具（如 Puppet、Chef 和 Ansible 等具有富有表现力名字的工具）使得描述标准化的部署场景和模块化的发布脚本变得简单，从而赋予开发团队设计自己部署策略的能力。这种方法通常比编写自定义发布脚本来下载和复制文件到服务器上要可靠得多。DevOps 工具使得遵循最佳实践变得容易，因为大多数部署场景都有现成的“食谱”或脚本可供使用。

##### 容器化

另一种标准化部署的方法是使用容器化。*容器化* 技术如 Docker 允许你创建被称为 *镜像* 的配置脚本，这些脚本描述了服务器应该使用的操作系统、磁盘布局和第三方软件，以及应该在软件堆栈上部署的 Web 应用程序。你将镜像部署到 *容器* 中，容器抽象了底层操作系统的各种功能，以实现一致的部署；发布所需的一切都在镜像中进行描述，而容器则是一个完全通用的组件。

你可以以可重复的方式将 Docker 镜像部署到真实或虚拟化的服务器上，从而确保发布过程的可靠性。开发者在本地测试代码时，可以使用与生产环境完全相同的 Docker 镜像，这样在代码正式发布时就能减少意外情况。

容器化是一项相对较新的技术，但它有望使复杂应用的部署更加可靠和标准化。一系列相关技术（例如 Docker Swarm 和 Kubernetes）使得可以通过机器可读的配置文件描述复杂的多服务器网络配置，这使得重新构建整个环境变得更加简单。举个例子，一个团队可以轻松启动一个全新的测试环境，其中包含多个 Web 服务器和一个数据库，因为这些单独的服务以及它们之间的通信方式都会在配置文件中描述，而该文件是托管服务可以理解的。

#### *构建过程*

大多数代码库都有一个 *构建过程*，通常通过命令行或开发工具触发，该过程将静态代码准备好以便部署。像 Java 和 C# 这样的语言在构建过程中将源代码编译成可部署的二进制格式，而使用包管理器的语言在执行构建过程时会下载并验证第三方代码，也就是所谓的 *依赖项*。

网站的构建过程通常会对客户端资源进行预处理，以便部署。许多开发者使用如 TypeScript 和 CoffeeScript 等语言，这些语言需要通过构建过程编译成 JavaScript。无论 JavaScript 是手写的还是生成的，构建过程通常会对 JavaScript 文件进行 *压缩* 或混淆，以生成一个压缩的、不可读性更高但功能上等效的 JavaScript 文件，从而使其在浏览器中加载更快。

网站的样式信息通常保存在 CSS 文件中，如 第三章 所述。管理大型网站的 CSS 文件可能是一项繁重的工作（因为样式信息通常在不同地方重复，并需要同步更新）。Web 开发人员通常使用 *CSS 预处理器*，例如 Sass 和 SCSS——这些语言旨在使样式表更易于管理，并需要在构建时将其预处理为 CSS 文件。

每种编程语言都有一个首选的构建工具，您的开发团队应该熟练掌握这个工具。您应该在将代码提交到源代码管理之前，在本地运行构建过程，这样您可以确保在发布过程中重新运行时构建过程能够正常工作。如前所述，使用持续集成服务器来确保这一过程。

#### *数据库迁移脚本*

为网站添加新功能通常需要新的数据库表格或现有表格的更新。数据库存储需要在发布之间保持持久的数据，因此您不能每次发布时都简单地清空并安装一个新的数据库。您需要创建并运行数据库 *迁移脚本*，以便在部署代码之前更新数据库结构；如果回滚代码，还需要撤销这些脚本。

一些技术（例如，Ruby on Rails）允许您将迁移脚本作为构建过程的一部分运行。如果您不能在构建过程中运行它们，您应该将脚本保存在源代码管理中，然后在发布窗口期间通过临时提升权限在数据库上运行它们。在一些公司，尤其是大型和复杂的数据库中，通常会有专门的 *数据库管理员（DBA）* 来管理此过程，并且他们通常不情愿地充当其所钟爱的数据库存储的守门人。

如果员工能够在发布之外更改数据库结构，那就是一种安全隐患。我们将在 第十一章 中讨论各种方法来锁定权限。

### 阶段 5：发布后测试与观察

一旦你部署了代码，你应该进行*发布后测试*，以确保代码正确部署，并验证你关于代码在生产环境中执行方式的假设是否正确。理论上，如果你有一个良好的测试环境和可靠的发布流程，这种发布后测试（通常称为*冒烟测试*）可以相当简单。不过，做每个阶段的测试时，最好关注直觉并避免冒险。有人说过，“继续测试，直到恐惧变成无聊。”这句话准确地表达了这一适当的心态。

#### *渗透测试*

安全专家和道德黑客经常进行*渗透测试*，它通过外部探测网站来检测安全漏洞。渗透测试对于发布前和发布后的测试都非常有用。此外，开发团队还可以使用复杂的自动化渗透测试工具，通过分析各种 URL 并尝试构造恶意 HTTP 请求来测试网站的常见安全漏洞。渗透测试可能非常昂贵且耗时，但它比被黑客攻击要便宜得多，*便宜得多*，因此强烈建议将其加入你的测试流程中。

#### *监控、日志记录和错误报告*

一旦你发布了代码，生产环境需要在运行时可观测。这有助于管理员发现异常或潜在的恶意行为，并在问题发生时进行诊断。发布后观察应通过三项活动进行：日志记录、监控和错误报告。

*日志记录*，即让代码在软件应用执行操作时写入日志文件，帮助管理员查看在任何特定时刻网站服务器的运行情况。你的代码应记录每个 HTTP 请求（包括时间戳、URL 和 HTTP 响应码），以及用户（例如，身份验证和密码重置请求）和站点本身（例如，发送电子邮件和调用 API）执行的重要操作。

你应该在运行时让管理员能够访问日志（通过命令行或 Web 控制台），并将其归档以供后续查看（以防需要进行事后分析）。在代码中添加日志语句有助于诊断网站上发生的问题，但要小心，不要将敏感信息（如密码和信用卡信息）写入日志，以防万一攻击者成功获取了日志。

*监控*是在网站运行时测量响应时间和其他指标的实践。监控你的 Web 服务器和数据库有助于管理员发现高负载场景或性能下降，并在网络速度变慢或数据库查询时间过长时发出警报。你应该将 HTTP 和数据库响应时间传递到监控软件中，这样当服务器和数据库响应时间超过某个阈值时，它会发出警报。许多云平台内置了监控软件，因此请花时间配置好错误条件和警报系统。

你应该使用*错误报告*来捕获并记录代码中的意外错误。你可以通过从日志中提取或在代码中捕获并记录它们来建立错误条件。然后，你可以将这些错误条件汇总到一个数据存储中，供管理员使用。许多安全入侵都会利用错误条件处理不当的漏洞，所以务必注意发生的意外错误。

第三方服务，如 Rollbar 和 Airbrake，提供插件，可以让你用几行代码收集错误信息。因此，如果你没有时间或兴趣自己设置错误报告系统，可以考虑使用这些服务。或者，像 Splunk 这样的日志抓取工具可以帮助你从日志文件中提取错误并理解它们。

### 依赖管理

你需要考虑的一个方面是依赖管理。现代 Web 开发的一个有趣事实是，你编写的代码可能只是你网站运行代码的少数部分。你的网站通常依赖于操作系统代码、编程语言运行时及其相关库，可能还有虚拟机，以及运行第三方代码库的 Web 服务器进程。所有这些你必须依赖的第三方工具被称为*依赖项*。（换句话说，*你的*软件运行所依赖的软件。）

每一个依赖项都是该领域的专家编写的，节省了你自己编写内存管理或低级 TCP 语义的负担。这些专家也有强烈的动力去保持对安全漏洞的关注，并在问题出现时发布补丁，所以你应该利用他们提供的资源！

使用他人的代码需要你自己付出努力。一个安全的 SDLC（软件开发生命周期）应该包括一个审查第三方库的过程，并确定何时需要应用补丁。这通常需要在常规开发周期之外进行，因为黑客不会等到你下次预定的发布日期才开始尝试利用安全漏洞。保持领先于安全公告并为他人的代码部署补丁和确保团队编写的代码一样重要。我们将在第十四章中讨论如何做到这一点。

### 总结

在本章中，您了解到了一个良好结构化的软件开发生命周期可以帮助您避免程序错误和软件漏洞。

+   您应当使用问题追踪软件来记录设计目标。

+   您应当将代码保存在源代码控制中，以便随时检查旧版本代码，并且便于组织代码审查。

+   在发布之前，您应当在一个专门的、隔离的测试环境中测试代码，该环境应当与生产环境相似，并且对您的数据给予最大程度的保护。

+   您应当拥有一个可靠、可重现且可回滚的发布流程。如果您有一个脚本化的构建过程来生成准备部署的资源，您应当定期运行它，并在持续集成环境中进行单元测试，以便及早发现开发生命周期中的潜在问题。

+   在发布之后，您应当使用渗透测试来检测网站漏洞，防止黑客利用这些漏洞。您还应当使用监控、日志记录和错误报告来检测和诊断运行中的站点问题。

+   您应当跟进您使用的任何第三方代码的安全建议，因为您可能需要在常规发布周期之外部署补丁。

在下一章中，您将（终于！）开始研究特定的软件漏洞以及如何防范这些漏洞。您将从一个网站面临的最大威胁开始：恶意输入，旨在将代码注入到您的网络服务器中。
