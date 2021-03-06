#《UNIX编程艺术》读书笔记
K.I.S.S(Keep It Simple, Stupid)

### Unix哲学整体概括如下：

1. 模块原则：使用简洁的接口拼合简单的部件。Brian Kernighan 曾经说过的：“计算机编程的本质就是控制复杂度”。要编制复杂软件而又不至于一败涂地的唯一方法就是降低其整体复杂度，用清晰的接口把若干简单的模块组合成一个复杂软件。如此一来，多数问题只会局限于某个局部，那么就还有希望对局部进行改进而不至牵动全身。
2. 清晰原则：清晰胜于机巧。在写程序时，要想到你不是写给执行代码的计算机看的，而是给人，将来阅读维护源码的人，尤其是说不定若干年后回过头来修改这些代码的人可能恰恰就是你自己。就算你将永远不再修改这些代码，也应该尽量做到不让替你维护代码的人因这些代码而骂你。
3. 组合原则：设计时考虑拼接组合。在输入输出方面，Unix传统极力提倡采用简单、文本化、面向流、设备无关的格式。每个部分单独成为一块，然后用一个简单的命令流或者是应用协议将其组合在一起。
4. 分离原则：策略同机制分享，接口同引擎分享。把策略同机制揉成一团有两个负面影响：一来会使策略变得死板，难以适应用户需求的改变；二来也意味着任何策略的改变都极有可能动摇机制；实现方法：一是，逻辑控制->用脚本语言来撰写。功能实现->用编译语言来撰写。二是，将应用程序分成可以协作的前端进程(实现策略) 和 后端进程(实现机制)， 通过套接字上层的专用应用协议进行通讯。以上两个方法，层次化分相同，交互方式不同而已。
5. 简洁原则：设计要简洁，复杂度能低则低。恶性循环陷阱：比别人花哨的方法就是把自己变得更花哨。要避免如此陷阱，唯一的方法就是鼓励以简洁为美，人人对庞大复杂的东西群起而攻之，这是一个非常看重简单解决方案的工程传统，总是设法将程序系统分解为几个能够协作的小部分，并本能地抵制任何用过多噱头来粉饰程序的企图。
6. 吝啬原则：除非确无它法，不要编写庞大的程序。‘大’有两重含义：一曰：体积大；长篇幅的代码本身就给维护者很大的心理压力，且定位、阅读、理解均有不便。二曰：复杂程度高。说出的话，写出的语，有时还不能让人尽解，更何况非母语的专业程序语言了！非常规的逻辑处理技巧，无异于是给你的代码加了壳，让维护者无从下手。
7. 透明原则：设计要可见，以便审查和调试。一个特别有效的减少调试工作量的方法就是设计时充分考虑：透明性和显见性。
	1. 透明性：是指你一眼就能够看出软件是在做什么以及怎样做的。
    2. 显见性：是指程序带有监视和显示内部状态的功能。
    这样程序不仅能够运行良好，而且还可以看得出它以何种方式运行。调试选项的设置应该尽量不要在事后，而应该在设计之初便考虑进去。这是考虑到程序不但应该能够展示其正确性，也应该能够把原开发者解决问题的思维模型告诉后来者。还应该提倡接口简洁，以方便其它程序对其进行操作。
8. 健壮原则：健壮源于透明与简洁。软件的健壮性指软件不仅能在正常情况下运行良好，而且在超出设计者设想的意外条件下也能够运行良好。因为过于复杂，很难通盘考虑，不能够正确理解一个程序的逻辑，也就不能确信其是否正确，所以禁不起磕碰，毛病多，不能在出错时修复它。程序的内部逻辑更易于理解带来了让程序健壮的两种方法：透明化和简洁化。
 
 	*  透明化：就是指一眼就能够看出来是怎么回事。
    * 简洁化：即人们不需要绞尽脑汁就能够推断出所有可能的情况。
		
	避免在代码中出现特例，BUG通常隐藏在处理特例的代码以及处理不同特殊情况的交互操作部分的代码中。
    模块性（代码简朴，接口简洁）是组织程序以达到更简洁目地的方法之一。
9. 表示原则：把知识叠入数据以求逻辑质朴而健壮。数据要比编程逻辑更容易驾驭。如果要在复杂数据和复杂代码中选择一个，宁愿选择复杂数据。在设计中，你应该主动将代码的复杂度转移到数据之中去。
10. 通俗原则：接口设计避免标新立异。(也称之为“最少惊奇原则”)。最易用的程序就是用户需要学习新东西最少的程序或者是最切合用户已有知识的程序。接口设计应该避免 毫无来由 的标新立异和自作聪明。尽量按照用户最可能熟悉的同样功能接口和相似应用程序来进行建模。关注目标受众，对于不同的人群，最少惊奇的意义也不同。关注传统惯例，缓和学习曲线，应该学会并使用这些惯例。避免表象相似而实际却略有不同，因为表象相似往往导致人们产生错误的假定。所以最好让不同事物有明显区别，而不要看起来几乎一模一样。
11. 缄默原则：如果一个程序没什么好说的，就保持沉默。
        重要信息不应该混杂在冗长的程序内部行为信息中。
        设计良好的程序将用户的注意力视为有限的宝贵资源，只有在必要时才要求使用。
12. 补救原则：出现异常时，马上退出并给出足够错误信息。软件要尽可能从容地应付各种错误输入和自身的运行错误(注：建议输出日志描述错误)，如做不到，也应尽可能的以一种容易诊断错误的方式终止(注：描述原因与运行环境各值)。悄无声息的埋下崩溃的隐患，直到很久以后才显现出来，这就是最坏的一种情况。Jonathan Postel谈网络服务程序的规定：“宽容地收，谨慎地发”，但是其含义可以广为适用。
13. 经济原则：宁花机器一分，不花程序员一秒。
14. 生成原则：避免手工处理，尽量编写程序去生成程序。众所周知，人类很不善于干辛苦的细节工作。程序中的任何手工处理都是滋生错误和延误的温床。
15. 优化原则：雕琢前先要有原型，跑之前先学会走。
        《计算机程序设计艺术》的作者 Donald Knuth 广为传播普及这样的观点：
        过早优化是万恶之源”。
        还不知道瓶颈所在就匆忙进行优化，这可能是唯一一个比乱加功能更损害设计的错误。
        过早的局部优化实际上会妨碍全局优化。
        “极限编程”宗师 Kent Beck 曾经说过：先求运行，再求正确，最后求快。
        先制作原型，再精雕细琢。优化之前先确保能用。
        先给你的设计做个未优化的、运行缓慢、很耗内存但是正确的实现，
        然后进行系统地调整，寻找那些可以通过牺牲最小的局部简洁性而获得较大性能提升的地方。
     
16. 多样原则：决不相信所谓“不二法门”的断言。Unix奉行的是广泛采用多种语言、开放的可扩展系统和用户定制机制。
17. 扩展原则：设计着眼未来，未来总比预想来得快。设计协议或是文件格式时，应使其具有充分的自描述性以便可以扩展。Unix经验告诉我们：稍微增加一点让数据部署具有自描述性的开销，就可以在无需破坏整体的情况下进行扩展，你的付出也就得到了成千倍的回报。设计代码时，要有很好的组织，让将来的开发者增加新功能时无需拆毁或重建整个架构。程序接合部要灵活，在代码中加入“如果你需要......”的注释。a设计为将来着眼，节省的有可能就是自己的精力。
 
18. Unix世界中来自于实践的具体规定：
     1. 只要可行，一切都应该做成与来源和目标无关的过滤器。
     2. 数据流应尽可能文本化（这样可以使用标准工具来查看和过滤）。
     3. 数据库部署和应用协议应尽可能文本化（让人可以阅读和编辑）。
     4. 复杂的前端（用户界面）和后端应该泾渭分明。
     5. 如果可能，用 C 编写前，先用解释性语言搭建原型。
     6. 当且仅当只用一门语言编程会提高程序复杂度时，混用语言编程才比单一语言编程来得好。
     6. 宽收严发（对接收的东西要包容，对输出的东西要严格）。
     8. 过滤时，不需要丢弃的信息决不丢。
     9. 小就是美，在确保完成任务的基础上，程序功能尽可能少。
	 10. 如果不能确定什么是对的，那么就只做最少量的工作，确保任务完成就行，至少直到明白什么是对的。‘
	 
### 模块性
#### 
	 