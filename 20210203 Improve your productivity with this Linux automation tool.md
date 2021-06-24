[#]: collector: (lujun9972)
[#]: translator: (stevenzdg988)
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Improve your productivity with this Linux automation tool)
[#]: via: (https://opensource.com/article/21/2/linux-autokey)
[#]: author: (Matt Bargenquast https://opensource.com/users/mbargenquast)

Improve your productivity with this Linux automation tool
使用 Linux 自动化工具提高生产率
======
Configure your keyboard to correct common typos, enter frequently used
phrases, and more with AutoKey.
![Linux keys on the keyboard for a desktop computer][1]
配置键盘(按键)以纠正常见的打字排版错误，输入常用的短语，以及更多的使用 AutoKey (功能)。
![台式机键盘上的Linux键][1]

[AutoKey][2] is an open source Linux desktop automation tool that, once it's part of your workflow, you'll wonder how you ever managed without. It can be a transformative tool to improve your productivity or simply a way to reduce the physical stress associated with typing.
[AutoKey][2]是一个开源的 Linux 桌面自动化工具，一旦它成为你工作流程的一部分，你会想知道没有它究竟将如何管理。它可以成为一种提高生产率的有改革能力的工具或者仅仅是减少与打字有关的物理压力的一种方式。

This article will look at how to install and start using AutoKey, cover some simple recipes you can immediately use in your workflow, and explore some of the advanced features that AutoKey power users may find attractive.
本文将研究如何安装和开始使用 AutoKey ，介绍一些可以立即在工作流程中使用的简单方法，并探讨 AutoKey 高级用户可能会感兴趣的一些高级功能。

### Install and set up AutoKey安装并设置 AutoKey

AutoKey is available as a software package on many Linux distributions. The project's [installation guide][3] contains directions for many platforms, including building from source. This article uses Fedora as the operating platform.
AutoKey 在许多 Linux 发行版中作为一个可用软件包。该项目的[安装指南][3]包含许多平台的说明，包括从源代码进行构建。本文使用 Fedora 作为操作平台。

AutoKey comes in two variants: autokey-gtk, designed for [GTK][4]-based environments such as GNOME, and autokey-qt, which is [QT][5]-based.
AutoKey 有两个变体：为像 GNOME 等基于 [GTK][4] 环境而设计的 autokey-gtk 和基于 [QT][5] 的 autokey-qt。

You can install either variant from the command line:
您可以从命令行安装任一变体：

```
`sudo dnf install autokey-gtk`
```

Once it's installed, run it by using `autokey-gtk` (or `autokey-qt`).
安装完成后，使用 `autokey-gtk`（或 `autokey-qt`）运行它。

### Explore the interface探究界面

Before you set AutoKey to run in the background and automatically perform actions, you will first want to configure it. Bring up the configuration user interface (UI):
在将 AutoKey 设置为在后台运行并自动执行操作之前，您首先需要对其进行配置。调出用户界面（UI）配置：

```
`autokey-gtk -c`
```

AutoKey comes preconfigured with some examples. You may wish to leave them while you're getting familiar with the UI, but you can delete them if you wish.
AutoKey 提供了一些预设配置的示例。您可能希望在熟悉 UI 时将他们留作备用，但是可以根据需要删除它们。

![AutoKey 用户界面][6]

(Matt Bargenquast, [CC BY-SA 4.0][7])

The left pane contains a folder-based hierarchy of phrases and scripts. _Phrases_ are text that you want AutoKey to enter on your behalf. _Scripts_ are dynamic, programmatic equivalents that can be written using Python and achieve basically the same result of making the keyboard send keystrokes to an active window.
左侧窗格包含基于层次结构的短语和脚本的文件夹。_Phrases_ 代表要让 AutoKey 输入的文本。_Scripts_ 是动态的有计划的等效项，可以使用 Python 编写，并且获得与键盘击键发送到活动窗口基本相同的结果。

The right pane is where the phrases and scripts are built and configured.
右侧窗格构建和配置短语和脚本。

Once you're happy with your configuration, you'll probably want to run AutoKey automatically when you log in so that you don't have to start it up every time. You can configure this in the **Preferences** menu (**Edit -&gt; Preferences**) by selecting **Automatically start AutoKey at login**.
对配置满意后，您可能希望在登录时自动运行 AutoKey，这样就不必每次都启动它。您可以通过在 **Preferences**(首选)菜单(**Edit -&gt; Preferences**(编辑 -&gt; 首选项))中勾选 **Automatically start AutoKey at login**(登录时自动启动 AutoKey)进行配置。

![登录时自动启动 AutoKey][8]

(Matt Bargenquast, [CC BY-SA 4.0][7])

### 使用 AutoKey 纠正常见的打字排版错误

Fixing common typos is an easy problem for AutoKey to fix. For example, I consistently type "gerp" instead of "grep." Here's how to configure AutoKey to fix these types of problems for you.
修复常见的打字排版错误对于 AutoKey 来说是一个容易解决的问题。例如，我始终键入 "gerp" 来代替 "grep"。这里是如何配置 AutoKey 为您解决这些类型问题。

Create a new subfolder where you can group all your "typo correction" configurations. Select **My Phrases** in the left pane, then **File -&gt; New -&gt; Subfolder**. Name the subfolder **Typos**.
创建一个新的子文件夹，可以在其中将所有“打字排版错误校正”配置分组。在左侧窗格中选择 **My Phrases** ，然后选择 **File -&gt; New -&gt; Subfolder**。将子文件夹命名为 **Typos**。

Create a new phrase in **File -&gt; New -&gt; Phrase**, and call it "grep."
在 **File -&gt; New -&gt; Phrase** 中创建一个新短语。并将其称为 "grep"。

Configure AutoKey to insert the correct word by highlighting the phrase "grep" then entering "grep" in the **Enter phrase contents** section (replacing the default "Enter phrase contents" text).
通过高亮显示短语 "grep"，然后在 **Enter phrase contents**(输入短语内容)部分（替换默认的“输入短语内容”文本）中输入 "grep" ，配置 AutoKey 插入正确的关键词。

Next, set up how AutoKey triggers this phrase by defining an Abbreviation. Click the **Set** button next to **Abbreviations** at the bottom of the UI.
接下来，通过定义缩写来设置 AutoKey 如何触发此短语。 点击用户界面底部紧邻 **Abbreviations**(缩写)的 **Set**(设置)按钮("gerp")。

In the dialog box that pops up, click the **Add** button and add "gerp" as a new abbreviation. Leave **Remove typed abbreviation** checked; this is what instructs AutoKey to replace any typed occurrence of the word "gerp" with "grep." Leave **Trigger when typed as part of a word** unchecked so that if you type a word containing "gerp" (such as "fingerprint"), it _won't_ attempt to turn that into "fingreprint." It will work only when "gerp" is typed as an isolated word.
在弹出的对话框中，单击 **Add** 按钮，然后将 "gerp" 添加为新的缩写。勾选 **Remove typed abbreviation**(**删除键入的缩写**)；此选项是命令 AutoKey 将出现 "gerp" 一词的任何键入替换为 "grep"。请不要勾选 **Trigger when typed as part of a word**(**在键入单词的一部分时触发**)，这样，如果您键入包含 "grep"(例如 "fingerprint"(指纹))的单词，就不会尝试将其转换为 "fingreprint"。仅当将 "grep" 作为独立的单词键入时，此功能才有效。

![在 AutoKey 中设置缩写][9]

(Matt Bargenquast, [CC BY-SA 4.0][7])

### Restrict corrections to specific applications限制对特定应用程序的更正

You may want a correction to apply only when you make the typo in certain applications (such as a terminal window). You can configure this by setting a Window Filter. Click the **Set** button to define one.
您可能希望仅在某些应用程序（例如终端窗口）中打字排版错误时才应用校正。您可以通过设置 Window Filter (窗口过滤器)进行配置。单击 **Set** 按钮来定义。

The easiest way to set a Window Filter is to let AutoKey detect the window type for you:

  1. Start a new terminal window.
  2. Back in AutoKey, click the **Detect Window Properties** button.
  3. Click on the terminal window.
设置 Window Filter (窗口过滤器)的最简单方法是让 AutoKey 为您检测窗口类型：

  1. 启动一个新的终端窗口。
  2. 返回 AutoKey，单击 **Detect Window Properties** (**检测窗口属性**)按钮。
  3. 单击终端窗口。

This will auto-populate the Window Filter, likely with a Window class value of `gnome-terminal-server.Gnome-terminal`. This is sufficient, so click **OK**.
这将自动填充 Window Filter，可能窗口类值为 `gnome-terminal-server.Gnome-terminal`。这足够了，因此单击 **OK**。

![AutoKey Window Filter][10]

(Matt Bargenquast, [CC BY-SA 4.0][7])

### Save and test保存并测试

Once you're satisfied with your new configuration, make sure to save it. Click **File** and choose **Save** to make the change active.
对新配置满意后，请确保将其保存。 单击 **File** ，然后选择 **Save** 以使更改生效。

Now for the grand test! In your terminal window, type "gerp" followed by a space, and it should automatically correct to "grep." To validate the Window Filter is working, try typing the word "gerp" in a browser URL bar or some other application. It should not change.
现在进行重要的测试！在您的终端窗口中，键入 "gerp" 紧跟一个空格，它将自动更正为 "grep"。要验证 Window Filter 是否正在运行，请尝试在浏览器 URL 栏或其他应用程序中键入单词 "gerp"。它并没有变化。

You may be thinking that this problem could have been solved just as easily with a [shell alias][11], and I'd totally agree! Unlike aliases, which are command-line oriented, AutoKey can correct mistakes regardless of what application you're using.
您可能会认为，使用 [shell 别名][11]可以轻松解决此问题，我完全赞成！与别名不同，只要是面向命令行，无论您使用什么应用程序，AutoKey 都可以按规则纠正错误。

For example, another common typo I make is "openshfit" instead of "openshift," which I type into browsers, integrated development environments, and terminals. Aliases can't quite help with this problem, whereas AutoKey can correct it in any occasion.
例如，我在浏览器，集成开发环境和终端中输入的另一个常见打字排版错误 "openshfit" 替代为 "openshift"。别名不能完全解决此问题，而 AutoKey 可以在任何情况下纠正它。

### Type frequently used phrases with AutoKey使用 AutoKey 键入常用短语

There are numerous other ways you can invoke AutoKey's phrases to help you. For example, as a site reliability engineer (SRE) working on OpenShift, I frequently type Kubernetes namespace names on the command line:
您可以通过许多其他方法来调用 AutoKey 的短语来帮助您。例如，作为从事 OpenShift 的站点可靠性工程师（SRE），我经常在命令行上输入 Kubernetes 命名空间名称：

```
`oc get pods -n openshift-managed-upgrade-operator`
```

These namespaces are static, so they are ideal phrases that AutoKey can insert for me when typing ad-hoc commands.
这些名称空间是静态的，因此它们是键入特定命令时 AutoKey 可以为我插入的理想短语。

For this, I created a phrase subfolder named **Namespaces** and added a phrase entry for each namespace I type frequently.
为此，我创建了一个名为 **Namespaces** 的短语子文件夹，并为我经常键入的每个命名空间添加了一个短语条目。

### 分配热键

Next, and most crucially, I assign the subfolder a **hotkey**. Whenever I press that hotkey, it opens a menu where I can select (either with **Arrow key**+**Enter** or using a number) the phrase I want to insert. This cuts down on the number of keystrokes I need to enter those commands to just a few keystrokes.
接下来，也是最关键的一点，我为子文件夹分配了一个 **hotkey**。每当我按下该热键时，它都会打开一个菜单，我可以在其中选择(要么使用 **Arrow key(方向键)**+**Enter(键)** (组合键)要么使用数字(键))要插入的短语。这减少了我仅需几次击键就可以输入这些命令的击键次数。

AutoKey's pre-configured examples in the **My Phrases** folder are configured with a **Ctrl**+**F7** hotkey. If you kept the examples in AutoKey's default configuration, try it out. You should see a menu of all the phrases available there. Select the item you want with the number or arrow keys.
 **My Phrases** 文件夹中 AutoKey 的预配置示例使用 **Ctrl**+**F7** 热键进行配置。如果您将示例保留在 AutoKey 的默认配置中，请尝试一下。您应该在此处看到所有可用短语的菜单。使用数字或箭头键选择所需的项目。

### Advanced AutoKeying高级自动键入

AutoKey's [scripting engine][12] allows users to run Python scripts that can be invoked through the same abbreviation and hotkey system. These scripts can do things like switching windows, sending keystrokes, or performing mouse clicks through supporting API functions.
AutoKey 的[脚本引擎][12]允许用户运行可以通过相同的缩写和热键系统调用的 Python 脚本。这些脚本可以通过支持 API 的功能来完成诸如切换窗口，发送按键或执行鼠标单击之类的操作。

AutoKey users have embraced this feature by publishing custom scripts for others to adopt. For example, the [NumpadIME script][13] transforms a numeric keyboard into an old cellphone-style text entry method, and [Emojis-AutoKey][14] makes it easy to insert emojis by converting phrases such as `:smile:` into their emoji equivalent.
AutoKey 用户已经欣然接受通过发布自定义脚本为其他用户采用的这项功能。例如，[NumpadIME 脚本][13]将数字键盘转换为旧的手机样式的文本输入方法，[Emojis-AutoKey][14] 可以通过将诸如: `:smile:` 之类的短语转换为他们等价的表情符号来轻松插入。

Here's a small script I set up that enters Tmux's copy mode to copy the first word from the preceding line into the paste buffer:
这是我设置的一个小脚本，该脚本进入 Tmux 的复制模式，以将前一行中的第一个单词复制到粘贴缓冲区中：

```
from time import sleep

# Send the tmux command prefix (changed from b to s)发送 Tmux 命令前缀（b更改为s）
keyboard.send_keys("&lt;ctrl&gt;+s")
# Enter copy mode
keyboard.send_key("[")
sleep(0.01)
# Move cursor up one line
keyboard.send_keys("k")
sleep(0.01)
# Move cursor to start of line
keyboard.send_keys("0")
sleep(0.01)
# Start mark
keyboard.send_keys(" ")
sleep(0.01)
# Move cursor to end of word
keyboard.send_keys("e")
sleep(0.01)
# Add to copy buffer
keyboard.send_keys("&lt;ctrl&gt;+m")
```

The sleeps are there because occasionally Tmux can't keep up with how fast AutoKey sends the keystrokes, and they have a negligible effect on the overall execution time.
睡眠之所以存在，是因为 Tmux 有时无法跟上 AutoKey 发送击键的速度，并且它们对整体执行时间的影响可忽略不计。

### Automate with AutoKey使用 AutoKey 自动化

I hope you've enjoyed this excursion into keyboard automation with AutoKey and it gives you some bright ideas about how it can improve your workflow. If you're using AutoKey in a helpful or novel way, be sure to share it in the comments below.
我希望您喜欢使用 AutoKey 进行键盘自动化的这次旅行，它为您提供了有关如何改善工作流程的一些好主意。如果使用 AutoKey 对您来说有帮助或是新颖的方式，请务必在下面的评论中分享。

--------------------------------------------------------------------------------

via: https://opensource.com/article/21/2/linux-autokey

作者：[Matt Bargenquast][a]
选题：[lujun9972][b]
译者：[stevenzdg988](https://github.com/stevenzdg988)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/mbargenquast
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/linux_keyboard_desktop.png?itok=I2nGw78_ (Linux keys on the keyboard for a desktop computer)
[2]: https://github.com/autokey/autokey
[3]: https://github.com/autokey/autokey/wiki/Installing
[4]: https://www.gtk.org/
[5]: https://www.qt.io/
[6]: https://opensource.com/sites/default/files/uploads/autokey-defaults.png (AutoKey UI)
[7]: https://creativecommons.org/licenses/by-sa/4.0/
[8]: https://opensource.com/sites/default/files/uploads/startautokey.png (Automatically start AutoKey at login)
[9]: https://opensource.com/sites/default/files/uploads/autokey-set_abbreviation.png (Set abbreviation in AutoKey)
[10]: https://opensource.com/sites/default/files/uploads/autokey-window_filter.png (AutoKey Window Filter)
[11]: https://opensource.com/article/19/7/bash-aliases
[12]: https://autokey.github.io/index.html
[13]: https://github.com/luziferius/autokey_scripts
[14]: https://github.com/AlienKevin/Emojis-AutoKey
