[#]: collector: (lujun9972)
[#]: translator: (stevenzdg988)
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Get started with Bash programming)
[#]: via: (https://opensource.com/article/20/4/bash-programming-guide)
[#]: author: (Seth Kenlon https://opensource.com/users/seth)

Get started with Bash programming
开始使用 Bash 编程
======
Learn how to write custom programs in Bash to automate your repetitive
tasks. Download our new eBook to get started.
![Command line prompt][1]
了解如何在 Bash 中编写定制程序以自动执行重复性操作任务。下载我们的新电子书以开始使用。
![命令行提示符][1]

One of the original hopes for Unix was that it would empower everyday computer users to fine-tune their computers to match their unique working style. The expectations around computer customization have diminished over the decades, and many users consider their collection of apps and websites to be their "custom environment." One reason for that is that the components of many operating systems are not open, so their source code isn't available to normal users.
对 Unix 的最初希望之一是授权给日常的计算机用户能够调整其计算机以适应其独特的工作风格。在过去的几十年中，对计算机定制的期望已经降低，许多用户考虑将他们收集的应用程序和网站作为他们的 “定制环境”。 原因之一是许多操作系统的组件未打开，因此普通用户无法使用其源代码。

But for Linux users, custom programs are within reach because the entire system is based around commands available through the terminal. The terminal isn't just an interface for quick commands or in-depth troubleshooting; it's a scripting environment that can reduce your workload by taking care of mundane tasks for you.
但是对于Linux用户而言，定制程序是可以实现的，因为整个系统都基于可通过终端获得的命令。终端不仅是用于快速命令或彻底排除故障的接口；也是一个脚本环境，可以通过为您处理日常任务来减少您的工作量。

### How to learn programming
如何学习编程

If you've never done any programming before, it might help to think of it in terms of two different challenges: one is to understand how code is written, and the other is to understand what code to write. You can learn _syntax_—but you won't get far without knowing what words are available to you in the _language_. In practice, you start learning both concepts all at once because you can't learn syntax without words to arrange, so initially, you write simple tasks using basic commands and basic programming structures. Once you feel comfortable with the basics, you can explore more of the language so you can make your programs do more and more significant things.
如果您以前从未进行过任何编程，可能面临考虑两个不同的挑战：一个是了解怎样编写代码，另一个是了解编写的代码是什么。您可以学习 _语法_，但是如果您不知道 _语言_ 中有哪些可用的关键字，您将无法继续。在实践中，同时开始学习这两个概念，是因为如果没有关键字的整理就无法学习语法，因此，最初您将使用基础命令和基础编程结构编写简单的任务。一旦熟悉基础，就可以探索更多编程语言的内容，从而使您的程序能够做越来越重要的事情。

In [Bash][2], most of the _words_ you use are Linux commands. The _syntax_ is Bash. If you already use Bash on a frequent basis, then the transition to Bash programming is relatively easy. But if you don't use Bash, you'll be pleased to learn that it's a simple language built for clarity and simplicity.
在 [Bash][2] 中，您使用的大多数 _关键字_ 是 Linux 命令。 _syntax_ 是 Bash。如果您已经频繁使用 Bash，则向 Bash 编程的过渡相对容易。但是，如果您不曾使用过 Bash，您会很高兴地学习到它是为清晰和简单而构建的简单语言。

### Interactive design
交互设计

Sometimes, the hardest thing to figure out when learning to program is what a computer can do for you. Obviously, if a computer on its own could do everything you do with it, then you wouldn't have to ever touch a computer again. But the reality is that humans are important. The key to finding something your computer can help you with is to take notice of tasks you repeatedly do throughout the week. Computers handle repetition particularly well.
有时，学习编程时最难解决的事情就是计算机可以为您做些什么。显然，如果一台计算机可以自己完成你要做的所有操作，那么您就不必再触摸计算机了。但是现实是人类很重要。找到您的计算机可以帮助您的事情的关键是通知整个星期重复执行的任务。计算机对重复的处理特别好。

But for you to be able to tell your computer to do something, you must know how to do it. This is an area Bash excels in: interactive programming. As you perform an action in the terminal, you are also learning how to script it.
但是，为了能让(告诉)计算机为你做某事(执行某项操作)，您必须知道怎么做。这是 Bash 擅长的领域：交互式编程。在终端中执行(命令)时，您还将学习如何编写脚本。

For instance, I was once tasked with converting a large number of PDF books to versions that would be low-ink and printer-friendly. One way to do this is to open the PDF in a PDF editor, select each one of the hundreds of images—page backgrounds and textures counted as images—delete them, and then save it to a new PDF. Just one book would take half a day this way.
例如，我曾经负责将大量 PDF 书籍转换为低墨和友好打印的版本。一种方法是在 PDF 编辑器中打开 PDF ，从数百张图像（算作图像的页面背景和纹理）中选择每张图像，然后删除它们，然后将其保存到新的PDF中。这样一本书只需要半天。从数百张图像中选择每张图像-页面背景和纹理记做图像-删除它们，然后将其保存到一个新的 PDF 文件中。这样一本书就要花半天时间。

My first thought was to learn how to script a PDF editor, but after days of research, I could not find a PDF editing application that could be scripted (outside of very ugly mouse-automation hacks). So I turned my attention to finding out to accomplish the task from within a terminal. This resulted in several new discoveries, including GhostScript, the open source version of PostScript (the printer language PDF is based on). By using GhostScript for the task for a few days, I confirmed that it was the solution to my problem.
我的第一个想法是学习如何编写 PDF 编辑器脚本，但是经过数天的研究，我找不到可以编写编辑 PDF 应用程序的脚本（鼠标自动化的外部技巧）。因此，我将注意力转向了从终端内部找出完成任务的方法。这导致了几个新发现，包括 GhostScript，PostScript 的开源版本（基于 PDF 的打印机语言）。通过使用 GhostScript 处理了几天的任务，我确认这是解决我的问题的方法。

Formulating a basic script to run the command was merely a matter of copying the command and options I used to remove images from a PDF and pasting them into a text file. Running the file as a script would, presumably, produce the same results.
制定基本的脚本来运行命令仅仅是关于复制命令和我用来从 PDF 中删除图像并将其粘贴到文本文件中的选项的问题。据推测，将文件作为脚本运行会产生相同的结果。

### Passing arguments to a Bash script
向 Bash 脚本传参数

The difference between running a command in a terminal and running a command in a shell script is that the former is interactive. In a terminal, you can adjust things as you go. For instance, if I just processed **example_1.pdf** and am ready to process the next document, to adapt my command, I only need to change the filename.
在终端中运行命令与在 Shell 脚本中运行命令之间的区别在于前者是交互式的。在终端中，您可以随时进行调整。例如，如果我刚刚处理 **example_1.pdf** 并准备处理下一个文档，以适应我的命令，则只需要更改文件名即可。

A shell script isn't interactive, though. In fact, the only reason a shell _script_ exists is so that you don't have to attend to it. This is why commands (and the shell scripts that run them) accept arguments.
Shell 脚本不是交互式的。实际上，Shell _脚本_ 存在的唯一原因是不必亲自参与。这就是为什么命令（以及运行它们的 Shell 脚本）接受参数的原因。

In a shell script, there are a few predefined variables that reflect how a script starts. The initial variable is **$0**, and it represents the command issued to start the script. The next variable is **$1**, which represents the first "argument" passed to the shell script. For example, in the command **echo hello**, the command **echo** is **$0,** and the word **hello** is **$1**. In the command **echo hello world**, the command **echo** is **$0**, **hello** is **$1**, and **world** is **$2**.
在 Shell 脚本中，有一些预定义的可以反映脚本启动方式的变量。初始变量是 **$0**，它代表发出的启动脚本的命令。下一个变量是 **$1** ，它表示传递给 Shell 脚本的第一个 “参数”。例如，在命令 **echo hello** 中，命令 **echo** 为 **$0,**，关键字 **hello** 为 **$1**。在命令 **echo hello world** 中，命令 **echo** 为 **$0,**，关键字 **hello** 为 **$1**，而 **world** 是 **$2**。

In an interactive shell:
在 Shell 中交互如下所示：

```
$ echo hello world
hello world
```

In a non-interactive shell script, you _could_ do the same thing in a very literal way. Type this text into a text file and save it as **hello.sh**:
在非交互式 Shell 脚本中，您 _可以_ 以非常直观的方式执行相同的操作。将此文本输入文本文件并将其另存为**hello.sh**：

```
`echo hello world`
```

Now run the script:
执行这个脚本：

```
$ bash hello.sh
hello world
```

That works, but it doesn't take advantage of the fact that a script can take input. Change **hello.sh** to this:
同样可以，但是并没有利用脚本可以接受输入这一优势。将 **hello.sh** 更改为：

```
`echo $1`
```

Run the script with two arguments grouped together as one with quotation marks:
运行带有用引号将两个参数组合在一起的脚本：

```
$ bash hello.sh "hello bash"
hello bash
```

For my PDF reduction project, I had a real need for this kind of non-interactivity, because each PDF took several minutes to condense. But by creating a script that accepted input from me, I could feed the script several PDF files all at once. The script processed each one sequentially, which could take half an hour or more, but it was a half-hour I could use for other tasks.
对于我的 PDF 缩减项目，我真的需要这种非交互性，因为每个 PDF 都花了几分钟来压缩。但是通过创建一个接受我的输入的脚本，我可以一次将几个 PDF 文件全部提交给脚本。该脚本按顺序处理了每个文件，这可能需要半小时或稍长一点时间，但是我可以用半小时来完成其他任务。

### Flow control
流控制

It's perfectly acceptable to create Bash scripts that are, essentially, transcripts of the exact process you took to achieve the task you need to be repeated. However, scripts can be made more powerful by controlling how information flows through them. Common methods of managing a script's response to data are:
创建 Bash 脚本是完全可以接受的，从本质上讲，是你开始实现需要重复执行任务的准确过程的副本。但是，可以通过控制信息流的方式来使脚本更强大。管理脚本对数据响应的常用方法是：

  * if/then
  * for loops
  * while loops
  * case statements

  * if/then 选择结构语句
  * for 循环结构语句
  * while 循环结构语句
  * case 语句

Computers aren't intelligent, but they are good at comparing and parsing data. Scripts can feel a lot more intelligent if you build some data analysis into them. For example, the basic **hello.sh** script runs whether or not there's anything to echo:
计算机不是智能的，但是它们擅长比较和分析数据。如果您在脚本中构建一些数据分析，则脚本会变得更加智能。例如，基本的 **hello.sh** 脚本运行后不管有没有内容都会显示：

```
$ bash hello.sh foo
foo
$ bash hello.sh

$
```

It would be more user-friendly if it provided a help message when it receives no input. That's an if/then statement, and if you're using Bash in a basic way, you probably wouldn't know that such a statement existed in Bash. But part of programming is learning the language, and with a little research you'd learn about if/then statements:
如果在没有接收输入的情况下提供帮助消息，将会更加容易使用。如下是一个 `if/then` 语句，如果您以一种基本的方式使用 Bash，则您可能不知道 Bash 中存在这样的语句。但是编程的一部分是学习语言，通过一些研究，您将了解 `if/then` 语句：

```
if [ "$1" = "" ]; then
        echo "syntax: $0 WORD"
        echo "If you provide more than one word, enclose them in quotes."
else
        echo "$1"
fi
```

Running this new version of **hello.sh** results in:
运行新版本的 **hello.sh** 输出如下：

```
$ bash hello.sh
syntax: hello.sh WORD
If you provide more than one word, enclose them in quotes.
$ bash hello.sh "hello world"
hello world
```

### Working your way through a script
通过脚本工作

Whether you're looking for something to remove images from PDF files, or something to manage your cluttered Downloads folder, or something to create and provision Kubernetes images, learning to script Bash is a matter of using Bash and then learning ways to take those scripts from just a list of commands to something that responds to input. It's usually a process of discovery: you're bound to find new Linux commands that perform tasks you never imagined could be performed with text commands, and you'll find new functions of Bash to make your scripts adaptable to all the different ways you want them to run.
无论您从PDF文件中查找要删除的图像，还是要管理混乱的 Downloads (下载)文件夹，还是要创建和提供 Kubernetes 镜像，学习编写 Bash 脚本都需要先使用 Bash，然后再学习采用这些从命令列表到响应输入内容的脚本的方法。通常这是一个发现的过程：您一定会找到新的 Linux 命令来执行您无法想象的可以通过文本命令执行的任务，并且您将找到 Bash 的新功能以使您的脚本适应您想要的所有不同方式来执行。

One way to learn these tricks is to read other people's scripts. Get a feel for how people are automating rote commands on their systems. See what looks familiar to you, and look for more information about the things that are unfamiliar.
学习这些技巧的一种方法是阅读其他人的脚本。了解人们如何在其系统上自动化死记硬背的命令。查看您熟悉的，并查找有关陌生事物的更多信息。

Another way is to download our [introduction to programming with Bash][3] eBook. It introduces you to programming concepts specific to Bash, and with the constructs you learn, you can start to build your own commands. And of course, it's free to download and licensed under a [Creative Commons][4] license, so grab your copy today.
另一种方法是下载我们的 [Bash 编程入门][3] 电子书。它向您介绍了特定于 Bash 的编程概念，并且通过学习的构造，您可以开始构建自己的命令。当然，它是免费的，并根据 [创建共享][4] 许可证进行下载和分发许可，因此，请立即获取副本。

### [Download our introduction to programming with Bash eBook!][3]
[下载我们介绍利用 Bash 编程的电子书！][3]

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/4/bash-programming-guide

作者：[Seth Kenlon][a]
选题：[lujun9972][b]
译者：[stevenzdg988](https://github.com/stevenzdg988)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/seth
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/command_line_prompt.png?itok=wbGiJ_yg (Command line prompt)
[2]: https://opensource.com/resources/what-bash
[3]: https://opensource.com/downloads/bash-programming-guide
[4]: https://opensource.com/article/20/1/what-creative-commons
