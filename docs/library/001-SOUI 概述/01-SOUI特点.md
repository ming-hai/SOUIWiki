原文链接：[《UI神器-SOUI》](http://www.cnblogs.com/setoutsoft/p/4996870.html)

- **使用层**：高速，稳定，美观，可配置

- **代码层**：精心设计，模块低耦合，插件化设计，对象可靠的命令周期管理，类似WTL的编码方式，现代化的事件处理模型及优异的扩展能力。

- **代码量**：核心模块代码量4W+，编译后DLL Release版本在900K左右。得益于精心组织的代码框架，虽然代码量较Duilib这样的UI库有比较大的提高（核心框架更完善，控件更多，注释量更大），但是阅读代码还是很轻松的（大量实际用户的亲身体验）。

- **高速**：主要体现在**3**个方面：

>[1] 框架设计扁平化，层次简单（和QT相比）：从宿主窗口收到消息到控件响应消息只有一个中间层。

>[2] 简单有效的刷新策略：通过对剪裁区及刷新时机的有较控制， 能有效的提高刷新效率。

>[3] 高效的渲染引擎：通过 将渲染引擎接口化，成功的将skia渲染引擎引入到SOUI中，Skia是Google的Chrome的渲染引擎，Chrome比IE渲染速度快，Skia功不可没。

- **稳定性**：SOUI脱胎于Bkwin，再经过本人的不断精心重构，已经在多个大量用户的产品中应用，包括最近开发的瑞雪医生客户端，多玩魔盒2.0, Dota2游戏盒子及多玩多个游戏盒子中使用， 及百度云管家的大部分界面。
百度云管家据说最初使用的是腾讯QQ界面库的早期版本（无从考证），然而QQ界面库大量使用COM技术，扩展非常麻烦，使用很是不便，在后续的UI需求中开始大量使用SOUI的前身DuiEngine。

- **美观**：SOUI原生支持Alpha通道，能够实现各种半透明效果，包括主窗体半透明，DUI窗口半透明，DUI窗口模仿LayeredWindow（分层窗口）效果等，轻松实现各种异形效果。

- **可配置**：SOUI中所有UI资源都采用XML描述，调整UI效果一般只需要修改XML资源即可完成。

>说到代码层的设计很难用语言描述，只有亲自阅读代码方能理解。为大部分需要在外部（APP层）经常引用的UI相关对象提供引用计数设计能够有效减少C++开发中常见的野指针问题，这一点还是很好体会，同时系统中也重点解决了如消息分发的分层设计，窗口对象的消息重入等影响UI使用体验的关键性问题。