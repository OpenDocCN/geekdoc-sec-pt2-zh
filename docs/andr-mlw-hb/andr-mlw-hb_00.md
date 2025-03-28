## 前言

![Image](img/common.jpg)

安卓是全球最受欢迎的操作系统，影响着近一半的全球人口。但它的规模和功能常常吸引罪犯、诈骗犯和诈骗者，他们寻求从用户那里窃取金钱或通过其他方式非法获利。

本书的作者自 2011 年起便在安卓安全领域工作，不久后安卓平台上便发现了第一份恶意软件样本。我们三人——Sebastian、Salvador 和 Sai——作为 Google Android 安全团队的一部分，开发了针对安卓恶意软件的防御措施。此外，V.S.及其研究人员，包括 Qian 和 Yanhai，创造了一些最早的、坚固的机器学习方法，用于表征安卓恶意软件的行为。

多年来，我们目睹了安卓用户与勒索软件、网络钓鱼、诈骗及其他多种有害应用作斗争。我们还看到了恶意软件开发者变得越来越复杂，推出了许多有趣的恶意应用家族，这些家族已被全球的安全研究人员记录下来。

在观察并应对这些数字威胁超过十年后，我们决定记录下我们所了解的安卓恶意软件的过去，分析当今恶意软件的方法，以及利用机器学习检测未来可能出现的恶意软件。截至目前，本书是安卓恶意软件趋势的最全面概述。其目标是帮助读者培养在当今网络安全环境中至关重要的分析和检测技能。

当你开始研究安卓生态系统中广泛的恶意软件类别时，你很快会意识到它们是多么动态，以及恶意软件检测有多复杂。大多数安全书籍并未涉及机器学习技术，但在过去几年中，机器学习算法已被证明在加速恶意软件应用的识别和分类方面非常有效，使得防御者能更快地应对这种复杂性，并在更大规模上进行应对。发展这种以人工智能为驱动的自动化专业技能，是恶意软件分析师技能演变中的自然下一步。

### 本书适合谁阅读

本书适用于三类读者。首先，它是为那些希望了解移动恶意软件样本及如何检查它的人准备的。其次，它是为那些有经验的安卓恶意软件分析师提供的，他们希望获得关于安卓恶意软件生态系统的全面了解。我们覆盖了大量真实的安卓恶意软件样本，包括一些前所未有的恶意软件家族，这些家族从未在公开场合讨论过。

第三，本书是为那些希望了解如何利用机器学习检测恶意软件的安全专业人士准备的。通过考虑不同恶意软件类别的目标和功能，你将学会如何利用机器学习算法在大规模上检测新型恶意软件。

### 本书内容概览

本书介绍了使用手动分析和机器学习方法进行 Android 恶意软件样本分析与检测的基本知识。我们从 Android 恶意软件生态系统的概览开始，然后讲解恶意应用的手动分析。最后，我们考虑使用机器学习自动检测恶意软件的技术。尽管我们建议按顺序阅读各章节，但你也可以根据需要跳过任何部分。

在第 I 部分，我们首先介绍了 Android 安全模型以及针对该平台的恶意软件。我们重点介绍了许多恶意软件家族的有趣结构特征，特别是它们如何滥用操作系统功能或如何暴露其恶意功能。本节的章节如下：

**第一章：Android 安全基础** 介绍了 Android 操作系统的安全模型以及 Google Android 安全团队用于组织和追踪工作的恶意软件类别。

**第二章：Android 恶意软件的现状** 描述了自 2008 年以来我们观察到的最流行和最有趣的 Android 恶意软件家族。本章还向读者介绍了有助于理解当今 Android 恶意软件环境的历史趋势。

接下来，在第 II 部分，我们将通过手动分析两个近期真实的 Android 恶意软件应用，深入探讨逆向工程技术和常见的恶意软件行为。这些章节包括：

**第三章：静态分析** 通过分析一个实际的收费欺诈恶意软件样本，向读者介绍 Android 应用文件的分析。我们解释了如何使用常见的开源工具解剖应用，并分享理解其组件、结构和代码的最佳实践。

**第四章：动态分析** 讲解了如何分析当前正在执行的 Android 应用，通过分析一个真实的钓鱼恶意软件样本。我们还解释了如何使用开源工具全面了解 Android 恶意软件在运行时的行为。

最后，在第 III 部分，我们探索了使用机器学习进行 Android 恶意软件检测的自动化过程。你将接触到流行的机器学习算法，并学习如何在它们应用于 Android 恶意软件时解释其输出。以下是本节各章的大纲：

**第五章：机器学习基础** 解释了将机器学习应用于 Android 恶意软件分析与检测的方法，并介绍了机器学习的关键概念，包括分类器、特征和模型训练。

**第六章：机器学习特征** 讨论了如何利用静态分析和动态分析的结果来识别机器学习特征，随后介绍了如何创建更能识别试图规避检测的恶意软件的高级特征。本章还展示了根据机器学习模型的输出，评估一个应用程序是否应被视为恶意软件或良性软件的不同方法。

**第七章：Root 恶意软件** 描述了多个安卓 Root 恶意软件家族的行为，随后介绍了分类器如何检测这一恶意软件类别的应用程序。本章还分析了用于检测恶意 Root 应用程序的某些机器学习特征的预测能力。作为案例研究，回顾了平台上首次发现的 Root 恶意软件 DroidDream。

**第八章：间谍软件** 讨论了主要的间谍软件家族，分析了如何区分间谍软件与良性软件及其他恶意软件类别，并展示了这些应用程序的一些独特特征，包括与权限相关的特性。本章最后通过 2022 年发现的间谍软件案例研究进行了总结，这款恶意软件很可能是由某个国家级开发的。

**第九章：银行木马** 讨论了几个安卓银行木马家族，介绍了它们的运作方式，以及如何通过分类器进行识别。本章的案例研究——Marcher，突出了这一恶意软件类别的共同特征，包括权限滥用以及这些应用程序与指挥控制服务器之间的通信。

**第十章：勒索软件** 解释了安卓勒索软件的工作原理，讨论了勒索加密器和勒索锁定器之间的区别，并分析了机器学习分类器在检测勒索软件应用程序时的表现。本章的案例研究探讨了一个著名的勒索软件样本——Simplocker。

**第十一章：短信诈骗** 介绍了滥用高级短信服务执行欺诈操作的恶意软件，随后呈现了可以用来识别短信诈骗应用程序的分类器，并分析了它们的哪些特征具有较强的预测能力。本章的案例研究聚焦了 BeeKeeper，这是一个针对俄罗斯运营商的短信诈骗应用。

**第十二章：安卓恶意软件的未来** 本章总结了当前安卓恶意软件的趋势，并描述了这些威胁在未来几年可能如何演变。

了解安卓恶意软件并非易事。每天，安全分析师和工程师都必须应对恶意软件开发者的行为，这些开发者不断向安卓平台投掷“曲线球”，希望他们的恶意应用程序能够避开检测。我们必须不断调整以应对这些新威胁，确保安卓及其用户的安全。那么，让我们开始吧！

[*OceanofPDF.com*](https://oceanofpdf.com)
