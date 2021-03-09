[#]: collector: (lujun9972)
[#]: translator: (stevenzdg988)
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Teach a virtual class with Moodle on Linux)
[#]: via: (https://opensource.com/article/20/10/moodle)
[#]: author: (Don Watkins https://opensource.com/users/don-watkins)

Teach a virtual class with Moodle on Linux
基于 Linux 的 Moodle 虚拟课堂教学
======
Teach school remotely with the Moodle learning management system on Linux.
基于 Linux 的 Moodle 学习管理系统远程学校教学。

![Digital images of a computer desktop][1]
![计算机桌面的数字图像][1]

The pandemic has created a greater need for remote education than ever before. This makes a learning management system (LMS) like [Moodle][2] more important than ever for ensuring that education stays on track as more and more schooling is delivered virtually.
远程教育创造的需求大流行比以往任何时候都更大。像 [Moodle][2] 这样的学习管理系统（LMS）变得比以往任何时候都重要，越来越多的借助虚拟现实技术提供教育的学校确保教育步入正轨。

Moodle is a free LMS written in PHP and distributed under the open source [GNU Public License][3] (GPL). It was developed by [Martin Dougiamas][4] and has been under continuous development since its release in 2002. Moodle can be used for blended learning, distance learning, flipped classrooms, and other forms of e-learning. There are currently over [190 million users][5] and 145,000 registered Moodle sites worldwide.
Moodle 是用 PHP 编写的免费 LMS，并以开源 [GNU Public License(GNU 公共许可)][3]（GPL）分发。它是由[Martin Dougiamas][4] 开发的，自 2002 年发布以来一直在不断发展。Moodle 可用于混合学习，远程学习，翻转课堂和其他形式的在线学习。目前，全球有超过 [1.9 亿用户][5] 和 145,000 个注册的 Moodle 网站。

I have used Moodle as an administrator, teacher, and student, and in this article, I'll show you how to set it up and get started using it.
我已经使用 Moodle 作为管理员，教师和学生等角色，在本文中，我将向您展示如何设置并开始使用它。

### Install Moodle on Linux
在 Linux 系统上安装 Moodle

Moodle's [system requirements][6] are modest, and there is plenty of documentation to help you. My favorite installation method is by downloading it as an ISO from [Turnkey Linux][7] and installing a Moodle site in VirtualBox.
Moodle 对 [系统要求][6] 适中，并且有大量文档可为您提供帮助。我最喜欢的安装方法是从 [Turnkey Linux][7] 下载并制作 ISO 在 VirtualBox 中安装 Moodle 站点。

First, download the [Moodle ISO][8] and save it to your computer.
首先，下载 [Moodle ISO][8] 保存到电脑中。

Next, install VirtualBox from the Linux command line with
下一步，安装 VirtualBox 的 Linux 命令行如下

```
$ sudo apt install virtualbox
```

or
或

```
$ sudo dnf install virtualbox
```

Once the download completes, start VirtualBox and select the **New** button on the console.
当下载完成后，启动 VirtualBox 并在控制台中选择 **New** 按钮。

![Create a new VirtualBox][9]
![创建一个新的 VirtualBox(虚拟机)][9]

(Don Watkins, [CC BY-SA 4.0][10])

Choose a name for your virtual machine, your operating system (Linux), and the type of Linux you're using (e.g., Debian 64-bit).
选择使用的虚拟机的名称，操作系统（Linux）和 Linux 类型（例如 Debian 64 位）。

![Naming the VirtualBox VM][11]
![命名 VirtualBox VM(虚拟机)][11]

(Don Watkins, [CC BY-SA 4.0][10])

Next, set your virtual machine (VM) memory size—use the default 1024MB. Then, choose a **dynamically allocated** virtual disk and attach the Moodle.iso to your virtual machine.
下一步，配置虚拟机(VM)内存大小-使用默认值 1024 MB。接下来选择 **dynamically allocated** (动态分配)虚拟磁盘并在虚拟机中添加 `Moodle.iso` 镜像。

![Attaching Moodle.iso to VM][12]
![添加 Moodle.iso 到 VM(虚拟机)][12]

(Don Watkins, [CC BY-SA 4.0][10])

Change your network settings from NAT to **Bridged adapter**. Then start the machine and install the ISO to create the Moodle virtual machine. During installation, you will be prompted to create passwords for the root account, MySQL, and Moodle. The Moodle password must include at least eight characters, one upper case letter, and one special character.
将您的网络设置从 NAT 更改为 **Bridged adapter**(桥接模式)。然后启动虚拟机并安装 ISO 以创建 Moodle 虚拟机。在安装过程中，系统将提示为 root 帐户，MySQL 和Moodle 创建密码。 Moodle 密码必须至少包含八个字符，至少一个大写字母和至少一个特殊字符。

Reboot the virtual machine. When the installation finishes, be sure to record your Moodle appliance settings somewhere safe. (After the installation, you can delete the ISO file if you want.)
重启虚拟机。安装完成后，请确保将 Moodle 应用配置内容记录在安全的地方。（安装后，可以根据需要删除ISO文件。）

![Moodle appliance settings][13]
![Moodle 应用配置][13]

(Don Watkins, [CC BY-SA 4.0][10])

It's important to note that your Moodle instance isn't visible by anyone on the Internet yet. It only exists in your local network: only people in your building who are connected to the same router or wifi access point as you can access your site right now. The worldwide Internet can't get to it because you're behind a firewall (embedded in your router, and possibly also in your computer). For more information on configuring your network, read Seth Kenlon's article on [opening ports and routing traffic through your firewall.][14]
重要提示 在 Internet(互联网)上的任何人还看不到你的 Moodle 实例。它仅存在于你的本地网络中：现在只有建筑物中与您连接到相同的路由器或 wifi 接入点的人可以访问您的站点。世界范围的 Internet(互联网)无法连接到它，因为您位于防火墙（嵌入在路由器中，还可能嵌入在计算机中）的后面。有关网络配置的更多信息，请阅读 Seth Kenlon 在 [打开端口并选择路由通信通过防火墙。][14] 上的文章。

### Start using Moodle
开始使用 Moodle

Now you are ready to log into your Moodle machine and get familiar with the software. Log into Moodle using the default login username, **admin**, and the password you set when you created the Moodle VM.
现在您可以登录到 Moodle 机器并熟悉该软件了。使用默认的用户名 **admin** 和创建 Moodle VM 时设置的密码登录 Moodle。

![Moodle login screen][15]
![Moodle 登录界面][15]

(Don Watkins, [CC BY-SA 4.0][10])

After logging in for the first time, you'll see your new Moodle site's main Dashboard.
首次登录后，您将看到初始的 Moodle 网站的主仪表盘。

![Moodle admin dashboard][16]
![Moodle 管理员仪表盘][16]

(Don Watkins, [CC BY-SA 4.0][10])

The default appliance name is **Turnkey Moodle**, but it's easy to change it to suit your school, classroom, or other needs and preferences. To personalize your Moodle site, in the menu on the left-hand side of the user interface, select **Site home**. Then click on the **Settings** icon on the right side of the display, and choose **Edit settings**.
默认的应用名称是 **Turnkey Moodle**，但是可以很容易地对其进行更改以适合您的学校，课堂或其他需要和选择。要使您的Moodle网站个性化，请在用户界面左侧的菜单中，选择 **Site home** (站点首页)。然后，点击屏幕右侧的 **Settings** (设置)图标，然后选择 **Edit settings**(编辑设置)。

![Moodle settings][17]
![Moodle 设置][17]

(Don Watkins, [CC BY-SA 4.0][10])

You can change your site's name and add a short name and site description if you'd like.
您可以根据需要更改站点名称，并添加简短名称和站点描述。

![Name Moodle site][18]
![Moodle 网站名][18]

(Don Watkins, [CC BY-SA 4.0][10])

Be sure to scroll to the bottom and save your changes. Now your site is personalized.
确保滚动到底部并保存更改。现在，您的网站已个性化。

![Moodle changes saved][19]
![Moodle 保存更改][19]

(Don Watkins, [CC BY-SA 4.0][10])

The default category is Miscellaneous, which won't help people identify your site's purpose. To add a category, return to the main Dashboard and select **Site administration** from the left-hand menu. Under **Courses**, select **Add a category** and enter details about your site.
默认类别为其他，这不会帮助人们识别您网站的目的。要添加类别，请返回主仪表盘，然后从左侧菜单中选择 **Site administration** (站点管理)。 在 **Courses**(**课程**)下，选择 **Add a category**(**添加类别**)并输入有关您的网站的详细信息。

![Add category option in Moodle][20]
![在 Moodle 中添加类别选项][20]

(Don Watkins, [CC BY-SA 4.0][10])

To add a course, return to **Site administration**, and click **Add a new course**. You will see a series of options, such as naming your course, providing a short name, assigning a category, and setting the course start and end dates. You can also set options for the course's format, such as social, weekly, and topic, as well as its appearance, file upload size, completion tracking, and more.
要添加课程，请返回 **Site administration**(**站点管理**)，然后单击 **Add a new course**(**添加新课程**)。您将看到一系列选项，例如为课程命名，提供简短名称，设定类别以及设置课程的开始和结束日期。您还可以为课程格式设置选项，例如社交，每周的和主题，以及其外观，文件上传大小，完成情况跟踪等等。

![Add course option in Moodle][21]
![在 Moodle 中添加课程选项][21]

(Don Watkins, [CC BY-SA 4.0][10])

### Add and manage users
添加和管理用户

Now that you have set up a course, you can add users. There are a variety of ways to do this. Manual entry is a good place to start if you are a homeschooler. Moodle supports email-based registration, [LDAP][22], [Shibboleth][23], and many others. School districts and other larger installations can upload users with a comma-delimited file. Passwords can be added in bulk, too, with a forced password change at first login. For more information, be sure to consult Moodle's [documentation][24].
现在，您已经设置了课程，您可以添加用户。有多种方法可以做到这一点。如果您是自学者，则手动入门是一个不错的开始。Moodle 支持基于电子邮件的注册，[LDAP][22]，[Shibboleth(口令或暗语)][23]等。学区和其他较大的装置支持用逗号分隔的文件上传用户。也可以批量添加密码，并在首次登录时强制更改密码。有关更多信息，请确保查阅 Moodle [文档][24]。

Moodle is a very granular, permission-oriented environment. It is easy to assign policies and roles to users and enforce those assignments using Moodle's menus.
Moodle是一个非常细化的，面向许可的环境。使用 Moodle 的菜单将策略和角色分配给用户并执行这些分配很容易。

There are many roles within Moodle, and each has specific privileges and permissions. The default roles are manager, course creator, teacher, non-editing teacher, student, guest, and authenticated user, but you can add other ones.
Moodle 中有许多角色，每个角色都有特定的特权和许可。 默认角色是管理员，课程创建者，教师，非编辑教师，学生，来宾和经过身份验证的用户，但您可以添加其他角色。

### Add content to your course
为课程添加内容

Once you have your Moodle site and a course set up, you can add content to the course. Moodle has all the tools you need to create great content, and it's built on solid pedagogy that emphasizes a [social constructionist][25] view.
一旦建立了 Moodle 网站并设置了课程，就可以向课程中添加内容。Moodle 具有创建出色内容所需要的所有工具，并且它以强调 [社会建构主义][25] 观点的扎实的教学法为基础。

I created a sample course called Code with [Mu][26]. It is in the **Programming** category and **Python** subcategory.
我用 [Mu][26] 创建了一个名为 Code 的示例课程。 它在 **Programming**(**编程**)类别和 **Python** 子类别中。

![Moodle course list][27]
![Moodle 课程列表][27]

(Don Watkins, [CC BY-SA 4.0][10])

I chose a weekly format for my course with the default of four weeks. Using the editing tools, I hid all but the first week of the course. This ensures my students stay focused on the material.
我为课程选择了每周格式，默认为四个星期。使用编辑工具，我隐藏了除课程第一周以外的所有内容。这样可以确保我的学生始终专注于材料。

As the teacher or Moodle administrator, I can add activities to each week's instruction by clicking **Add an activity** **or resource**.
作为教师或 Moodle 管理员，我可以通过单击 **Add an activity**(**添加活动**) **or resource**(**或资源**)来将活动添加到每周的教学中。

![Add activity in Moodle][28]
![在 Moodle 中添加活动][28]

(Don Watkins, [CC BY-SA 4.0][10])

I get a pop-up window with a variety of activities I can assign to my students.
我会看到一个弹出窗口，其中包含可以分配给我的学生的各种活动。

![Moodle activities menu][29]
![Moodle 活动菜单][29]

(Don Watkins, [CC BY-SA 4.0][10])

Moodle's tools and activities make it easy for me to create learning materials and cap off the week with a short quiz.
Moodle 的工具和活动使我可以轻松地创建学习材料并进行简短的测验来结束一周的学习。

![Moodle activities checklist][30]
![Moodle 活动清单][30]

(Don Watkins, [CC BY-SA 4.0][10])

There are more than 1,600 plugins you can use to extend Moodle with new activities, question types, integrations with other systems, and more. For example, the [BigBlueButton][31] plugin supports slide sharing, a whiteboard, audio and video chat, and breakout rooms. Others to consider include the [Jitsi][32] plugin for videoconferencing, a [plagiarism checker][33], and an [Open Badge Factory][34] for awarding badges.
您可以使用 1,600 多个插件来扩展 Moodle 的新活动，问题类型，与其他系统的集成等等。例如，[BigBlueButton][31] 插件支持幻灯片共享，白板，音频和视频聊天以及小组讨论室。其他需要考虑的包括用于视频会议的 [Jitsi][32] 插件，用于复制徽章的 [抄袭检查器][33] 和 [开放徽章工厂][34]。

### Keep exploring Moodle
继续探索 Moodle

Moodle is a powerful LMS, and I hope this introduction whets your appetite to learn more. There are excellent [tutorials][35] to help you improve your skills, and you can see Moodle in action on its [demonstration site][36] or access [Moodle's source code][37] if you want to see what's under the hood or [contribute][38] to development. Moodle also has a great [mobile app][39] for iOS and Android, if you like to work on the go. Follow Moodle on [Twitter][40], [Facebook][41], and [LinkedIn][42] to stay up to date on what's new.
Moodle 是功能强大的 LMS，我希望此介绍能引起你的兴趣，以了解更多信息。有很多出色的 [指南][35] 可以帮助您提高技能，如果想要查看 Moodle 的内容，可以在其 [演示站点][36] 上查看运行中的 Moodle，或访问 [Moodle的源代码][37] 查看罩或对发展作出 [贡献][38]。如果您喜欢在旅途中工作，Moodle 也有一款出色的 [移动应用][39]，适用于 iOS 和 Android。在[Twitter][40]，[Facebook][41] 和 [LinkedIn][42] 上关注 Moodle，以了解最新消息。

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/10/moodle

作者：[Don Watkins][a]
选题：[lujun9972][b]
译者：[stevenzdg988](https://github.com/stevenzdg988)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/don-watkins
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/computer_desk_home_laptop_browser.png?itok=Y3UVpY0l (Digital images of a computer desktop)
[2]: https://moodle.org/
[3]: https://docs.moodle.org/19/en/GNU_General_Public_License
[4]: https://dougiamas.com/about/
[5]: https://docs.moodle.org/39/en/History
[6]: https://docs.moodle.org/39/en/Installation_quick_guide#Basic_Requirements
[7]: https://www.turnkeylinux.org/
[8]: https://www.turnkeylinux.org/download?file=turnkey-moodle-16.0-buster-amd64.iso
[9]: https://opensource.com/sites/default/files/uploads/virtualbox_new.png (Create a new VirtualBox)
[10]: https://creativecommons.org/licenses/by-sa/4.0/
[11]: https://opensource.com/sites/default/files/uploads/virtualbox_namevm.png (Naming the VirtualBox VM)
[12]: https://opensource.com/sites/default/files/uploads/virtualbox_attach-iso.png (Attaching Moodle.iso to VM)
[13]: https://opensource.com/sites/default/files/uploads/moodle_appliance.png (Moodle appliance settings)
[14]: https://opensource.com/article/20/9/firewall
[15]: https://opensource.com/sites/default/files/uploads/moodle_login.png (Moodle login screen)
[16]: https://opensource.com/sites/default/files/uploads/moodle_dashboard.png (Moodle admin dashboard)
[17]: https://opensource.com/sites/default/files/uploads/moodle_settings.png (Moodle settings)
[18]: https://opensource.com/sites/default/files/uploads/moodle_name-site.png (Name Moodle site)
[19]: https://opensource.com/sites/default/files/uploads/moodle_saved.png (Moodle changes saved)
[20]: https://opensource.com/sites/default/files/uploads/moodle_addcategory.png (Add category option in Moodle)
[21]: https://opensource.com/sites/default/files/uploads/moodle_addcourse.png (Add course option in Moodle)
[22]: https://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol
[23]: https://www.shibboleth.net/
[24]: https://docs.moodle.org/39/en/Main_page
[25]: https://docs.moodle.org/39/en/Pedagogy#How_Moodle_tries_to_support_a_Social_Constructionist_view
[26]: https://opensource.com/article/20/9/teach-python-mu
[27]: https://opensource.com/sites/default/files/uploads/moodle_choosecourse.png (Moodle course list)
[28]: https://opensource.com/sites/default/files/uploads/moodle_addactivity_0.png (Add activity in Moodle)
[29]: https://opensource.com/sites/default/files/uploads/moodle_activitiesmenu.png (Moodle activities menu)
[30]: https://opensource.com/sites/default/files/uploads/moodle_activitieschecklist.png (Moodle activities checklist)
[31]: https://moodle.org/plugins/mod_bigbluebuttonbn
[32]: https://moodle.org/plugins/mod_jitsi
[33]: https://moodle.org/plugins/plagiarism_unicheck
[34]: https://moodle.org/plugins/local_obf
[35]: https://learn.moodle.org/
[36]: https://school.moodledemo.net/
[37]: https://git.in.moodle.com/moodle/moodle
[38]: https://git.in.moodle.com/moodle/moodle/-/blob/master/CONTRIBUTING.txt
[39]: https://download.moodle.org/mobile/
[40]: https://twitter.com/moodle
[41]: https://www.facebook.com/moodle
[42]: https://www.linkedin.com/company/moodle/
