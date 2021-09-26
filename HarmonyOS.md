## 什么是HarmonyOS?

### 特性

- 分布式架构首次用于终端OS，实现跨终端无缝协同体验
- 确定时延引擎和高性能IPC技术实现系统天生流畅
- 基于微内核架构重塑终端设备可信安全
- 通过统一IDE支撑一次开发，多端部署，实现跨终端生态共享

### 发展历史

- 2017年，鸿蒙内核 1.0
- 2018年，鸿蒙内核 2.0
- 2019年，鸿蒙OS 1.0
- 2020年，鸿蒙OS 2.0

### 架构

- 内核
- 基础
- 应用

### HarmonyOS VS Android

- GMS VS HMS
    - GMS 全称Google Mobile Services。这里面有两部分，一部分是包括谷歌地图，谷歌Play商店等等几十种APP的“全家桶”，另外一部分则是提供给第三方APP开发者使用的GMS
      Core功能，包括许多服务的编程接口API
    - HMS 众所周知，2019年下半年，Google的GMS就被禁止在华为手机上使用，于是华为全球发布了HMS，以对标谷歌的GMS

- AOSP VS OpenHarmony
    - AOSP Android Open Source Project,中文意为Android 开放源代码项目
    - OpenHarmony
      OpenHarmony是开放原子开源基金会上的一个孵化项目，目标是支持可在多种终端设备上运行。既可运行在百KB级别的资源受限设备和穿戴类设备上，也可运行在百MB级别的智能家用摄像头、行车记录仪等相对资源丰富的设备上，以及GB级别的智能电视等设备上。第一个版本支持
      128KB-128MB 的内存设备

- HarmonyOS
    - 是华为基于开源项目OpenHarmony 开发的面向多种全场景智能设备的商用版本。
    - 应用开发 [link]("https://developer.harmonyos.com/cn/home/")
    - 设备开发---为不同设备的智能化、互联与协同提供了统一的语言，带来简捷、流畅、连续、安全可靠的全场景交互体验。 [link]("https://device.harmonyos.com/cn/home/")
        - WLAN连接类产品。与WLAN信道协同，通过碰一碰即可完成设备配网注册并拉起 FA 服务，实现服务一步直达。
        - 摄像头类产品。全栈轻量化设计，包括内核、UI、媒体、JS 开发框架等，支持丰富的 UI 控件，完备的图形栈和多媒体能力、分布式调度能力，提供 DevEco Studio IDE 开发环境。
        - 摄像头+屏幕类产品。全栈轻量化设计，包括内核、UI、媒体、JS 开发框架等，支持丰富的 UI 控件，完备的图形栈和多媒体能力、分布式调度能力，提供 DevEco Studio IDE 开发环境。

- HarmonyOS 四大组件 VS Android 四大组件
    - Ability是应用所具备能力的抽象，也是应用程序的重要组成部分。一个应用可以具备多种能力（即可以包含多个Ability），HarmonyOS支持应用以Ability为单位进行部署。Ability可以分为FA（Feature
      Ability）和PA（Particle Ability）两种类型，每种类型为开发者提供了不同的模板，以便实现不同的业务功能。(类似于Android的Activity)
    - AbilitySlice (类似Android的Fragment)
    - Service
      Ability是基于Service模板的Ability主要用于后台运行任务（如执行音乐播放、文件下载等），但不提供用户交互界面。Service可由其他应用或Ability启动，即使用户切换到其他应用，Service仍将在后台继续运行。（类型于Android的Service）
    - Data Ability
      使用Data模板的Ability（以下简称“Data”）有助于应用管理其自身和其他应用存储数据的访问，并提供与其他应用共享数据的方法。Data既可用于同设备不同应用的数据共享，也支持跨设备不同应用的数据共享。（类型于Android的Content
      Provider)
    - CES（Common Event Service，公共事件服务）,ANS（Advanced Notification Service，即通知增强服务。（类似Android的广播）

- 线程及线程间通信

- UI
    - Java UI(类型于Android View和ViewGroup体系)
        - Component
        - ComponentContainer
    - JS UI

- 开发工具（DevEco Studio）

### HarmonyOS 跨平台 和 Java(jvm)跨平台

以上，我们提到HarmonyOS具有通过统一IDE支撑一次开发，多端部署，实现跨终端生态共享的特性，同时我们也知道Java同样也具有跨平台的能力，那么这两 者的跨平台有什么区别呢。首先我们需要知道的是，什么是跨平台?

#### 什么是跨平台

在以前，平台 ≈ 操作系统。所有传统意义上的跨平台即不依赖于操作系统，也不依赖硬件环境。就比如在windows开发的java应用，放在linux系统下同样也能运行。

但是，随着现代科技的发展，平台 ≈ 操作系统已经不成立了，就像华为推出的HarmonyOS一样，他支持多种设备，手机、手表、电脑、汽车、智能家居等。

因此，当前我们谈的跨平台，指的是跨设备。即平台 ≈ 设备

所以，华为希望鸿蒙能够运行在各种各样的设备上，即鸿蒙必然需要具备跨平台的能力。

不仅仅是操作系统的跨平台，重要的是要让用户和开发者真正地感受到跨平台。所以跨平台操作系统鸿蒙的目的是:
使开发者能够着重处理业务逻辑，像开发同一终端一样去开发跨终端分布式应用，也使最终消费者感受到强大的跨终端业务协同能力为各使用场景带来的无缝体验。

#### Java的跨平台

Java对于跨平台的支持，就像对安全性和网络移动性的支持一样，是分布在整个Java体系结构中的。其中扮演者重要的角色的有Java语言规范、Class文件、Java虚拟机（JVM）等。

首先，在Java语言规范中，规定了Java语言中基本数据类型的取值范围和行为。其次，所有Java文件要编译成统一的Class文件。最后，通过Java虚拟机将Class文件转成对应平台的二进制文件。
Java的平台无关性是建立在Java虚拟机的平台有关性基础之上的，是因为Java虚拟机屏蔽了底层操作系统和硬件的差异。

想要运行一段Java代码，要经过多个步骤，将Java源代码转换成机器可以执行的机器代码，这个过程主要由虚拟机来完成。

在著名的HotSpot虚拟机中，主要有解释执行和即时编译两种形式：

- 解释执行

        逐条将字节码翻译成机器码并执行

- 即时编译（Just-in-time ，JIT）

        将一个方法中包含的所有字节码编译成机器码后再执行。

HotSpot 默认采用混合模式，综合了解释执行和即时编译两者的优点。它会先解释执行字节码，而后将其中反复执行的热点代码（热点检测），以方法为单位进行即时编译。

#### Android实现跨平台

Android基于Java语言，所以同理，需要经过多个步骤将Android源代码转换成功机器可以执行的机器代码。这个转换过程在Android不同版本中实现不尽相同:

- Android 1.0（2008 年）：采用一个名为 Dalvik 的虚拟机，并且集成了一个解释器。当 App 运行时，就会调用这个解释器，对代码进行逐句解释，速度很慢。

- Android 2.2（2010 年）：引入 JIT（Just In Time）即时编译机制，当 App 运行时，会将用户经常使用的功能编译为机器能直接执行的 010101
  机器码，不用一句一句地去翻译。当出现不常用的功能时，再调用解释器来翻译；这样速度加快，但每次启动 App 都要重新编译一次，不能一劳永逸。

- Android 5.0（2014 年 10 月）：将虚拟机 Dalvik 换成 ART（Android Run Time），将 JIT 的编译器替换成 AOT（Ahead of Time）。如此，App
  在下载后安装到手机上时同时把能编译的代码先编译成机器听得懂的 101010；剩下不太好翻译的代码，就在用户使用时再叫醒解释器来翻译。如此，不用每次打开 App 都需要编译，但安装 App 的时间有点长，而且占用手机空间。

- Android 7.0（2016 年）：采用混合编译机制，安装时先不编译中间代码，而是在用户空闲时将能够编译成机器码的那部分代码，通过 AOT 编译器先静态编译了。如果 AOT 还没来得及编译或者不能编译，再调用 JIT+
  解释器。这种机制，相当于用时间换空间，既缩短了用户安装 APP 的等待时间，又将虚拟机里编译器和解释器能做的优化提升到最大效率了。

以上，Android同样依赖于虚拟机，只是编译过程不一样。由于移动设备限制较多，所以实现起来比java复杂的多

当前的 Android 采用的是解释执行 + JIT + AOT 的综合模式，在 空间占用+安装速度+运行速度 上已经达到了一个很好的平衡

但是Android的编译问题一直被诟病。尽管在后续的Android 8.0 上改进了解释器，解释模式执行效率大幅提升；Android 10.0 上提供了预先放置热点代码的方式，应用在安装的时候就能知道常用代码会被提前编译。

但是，目前来看，无论如何，Android都没能摆脱这样一个前提：即应用在被打包成 APK 的时候，采用的还是 Java 代码。换句话说，在 APK 变成用户可应用的过程中，还经历了一个在 Android
系统内部的编译过程，这是一个绕不过的坎。

那么，有没有一种机制可以想办法绕过虚拟机，同时也能实现跨平台？鸿蒙OS了解下。

#### HarmonyOS的跨平台

跨平台有一个最大的挑战，那就是各个平台的适配问题，尤其是目前各种设备类型越来越多，如何将同一个应用，在手机、手表、汽车、电视上面都可以适配的展示呢？这就是多终端开发IDE所做的事情。

##### 多终端IDE

使用华为提供的多终端IDE，多语言统一编译，分布式架构Kit提供屏幕布局控件以及交互的自动适配，支持控件拖拽，面向预览的可视化编程，从而使开发者可以基于同一工程高效构建多端自动运行App，实现真正的一次开发，多端部署，在跨设备之间实现共享生态。

有了IDE，开发可以方便的开发一套代码，这样可以自动适配到各种设备中，但是各种设备所执行的机器指令是不一样的，如何把这一套代码分别编译成各个设备需要的机器指令呢？

Android设备是由不同设备上内置的虚拟机进行编译的，所以编译之前就知道这个设备具体是什么了，那么，鸿蒙OS是怎么做的呢？这就是方舟编译器所干的事情了。

##### 方舟编译器

华为方舟编译器是首个取代Android虚拟机模式的静态编译器，可供开发者在开发环境中一次性将高级语言编译为机器码。此外，方舟编译器未来将支持多语言统一编译，可大幅提高开发效率。

未来，方舟编译器将支持多语言统一编译大幅提高开发效率（支持C/C++、Java,JS,Kotlin等）

##### HarmonyOS编译 VS Android编译

Android之所以"慢"，是因为他的编译过程是在终端进行的，也就是说需要在用户的手机上，通过虚拟机进行编译成可执行的机器代码。

而鸿蒙OS使用的方舟编译器，可以将高级语言（Java）直接变成机器码，从而绕过了虚拟机。并且这个编译过程并不是在用户的手机上完成的，而是在应用开发阶段就完成了。

通过方舟编译器，开发者的应用在下载之前就已经转化成为机器可以识别的代码，因而可以在手机上快速安装、启动和运行，而无需在经过 VM 的编译——某种程度上，方舟编译器是将编译过程提前到应用开发阶段，从而大幅度减少了智能手机和操作系统的运行负担。

华为官方介绍，方舟编译器是首家完全替代语言虚拟机的静态编译器，完全不需要解释器。兼顾Java开发效率和C语言运行效率的编译器。

除了代码编译，方舟编译器也提供了更高效的内存机制，它与 Android 内存回收的不同之处在于：

Android 在内存回收上采用集中回收机制，发声全局回收时更需要暂停应用，这也是随机卡顿的根因之一。而方舟编译器采用了引用计数法来进行内存的实时回收，并且配合使用了专门的消除环算法（消除对象互相引用带来的无法回收问题），来避免 GC
集中式回收带来的系统卡顿。相比 GC，方舟的内存回收是实时的而非集中式的，且不需要暂停应用进程，这样便大大消除了卡顿。

另外，就像JVM其实也是支持多种语言一样，华为表示，方舟编译器未来也会支持更过的开发语言。换句话说，其他语言的开发者，日后也能开发基于鸿蒙OS的应用。
     
   