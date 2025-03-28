

# 第二部分 系统监控



到目前为止，我已经介绍了收集数据以生成系统状态快照的编程方法，然后分析这些快照以发现恶意活动的症状。然而，这种方法将分析限制在单一的时间点。简单的防病毒程序通常提供这种功能，通过“立即扫描”选项来实现，这对于确定系统是否已经感染以及创建已知良好状态的基准非常有用。这种方法的明显缺点是它是反应式的，最糟糕的是，可能完全错过感染。例如，勒索病毒可能在两个快照之间的时间窗口内感染系统，并使其无法操作。

解决方案是扩展第一部分中提出的方法，以提供实时监控功能。在第二部分中，我将解释如何实时监控系统日志、网络、文件系统和进程事件。在某些情况下，我们需要编写特定于监控目标的代码；而在其他情况下，Apple 的端点安全框架可以作为监控的基础，支持文件系统、进程及其他许多重要事件的监控。为了全面理解端点安全的能力，我将花费一整章来重点介绍它的高级功能，包括授权和静音。最全面的恶意软件检测解决方案将包括第一部分中介绍的方法，以及第二部分中我将涵盖的技术。

此外，监控代码可以应用第一部分中讲解的策略来识别异常。例如，我们在第二章中编写的逻辑，用于检测运行进程的二进制文件是否被打包，可以实时识别可疑的二进制文件，比如当进程监控器拦截到一个新启动的进程时。
