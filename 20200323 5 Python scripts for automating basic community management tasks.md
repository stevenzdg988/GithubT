[#]: collector: (lujun9972)
[#]: translator: (stevenzdg988)
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (5 Python scripts for automating basic community management tasks)
[#]: via: (https://opensource.com/article/20/3/automating-community-management-python)
[#]: author: (Rich Bowen https://opensource.com/users/rbowen)

5 Python scripts for automating basic community management tasks
用于基本社区管理任务自动化的 5 个 Python 脚本
======
If you have to do something three times, try to automate it.
![shapes of people symbols][1]

如果某些事情不得不重复做三遍，尝试使其自动化。
![人形符号][1]

I've [written before about what a community manager does][2], and if you ask ten community managers, you'll get 12 different answers. Mostly, though, you do what the community needs for you to do at any given moment. And a lot of it can be repetitive.

我 [之前写过关于社区管理员的工作][2]，如果您问 10 位社区管理员，您会得到 12 个不同的答案。你在任何给定的时刻都要做社区需要你做的事情。并且大多数可以重复。

Back when I was a sysadmin, I had a rule: if I had to do something three times, I'd try to automate it. And, of course, these days, with awesome tools like Ansible, there's a whole science to that.
当我成为系统管理员时，我遵循一个规则：如果某些事必须做三遍，我会尝试使其自动化。当然，如今，使用诸如 Ansible 这样的强大工具，这是一门完整的科学。

Some of what I do on a daily or weekly basis involves looking something up in a few places and then generating some digest or report of that information to publish elsewhere. A task like that is a perfect candidate for automation. None of this is [rocket surgery][3], but when I've shared some of these scripts with colleagues, invariably, at least one of them turns out to be useful.
我每天或每周要做的一些事情涉及在一些地方查找内容，然后生成摘要或该信息的报告发布到别处。这样的任务是自动化的理想选择。这些并不是 [难事][3]，当我与同事共享其中一些脚本时，总是至少有一个能证明这是有用的。

[On GitHub][4], I have several scripts that I use every week. None of them are complicated, but they save me a few minutes every time. Some of them are in Perl because I'm almost 50. Some of them are in Python because a few years ago, I decided I needed to learn Python. Here's an overview:
[在 GitHub][4] 上，我有几个每周都要使用的脚本。他们都不是很复杂的，但每次都为我节省几分钟。其中一些是用 Perl 写的是因为我快 50 岁了。其中一些使用 Python 就在几年前，我决定需要学习 Python。概述如下：

### **[tshirts.py][5]**

This simple script takes a number of Tshirts that you're going to order for an event and tells you what the size distribution should be. It spreads them on a normal curve (also called a bell curve), and, in my experience, this coincides pretty well with what you'll actually need for a normal conference audience. You might want to adjust the script to slightly larger if you're using it in the USA, slightly smaller if you're using it in Europe. YMMV.
这个简单的脚本将为你定制一定数量的活动 T恤，告诉你尺寸分布是什么。将它们分布在一条正常的曲线（也称为 “钟形曲线”）上，以我的经验，这和一个正常的会议观众的实际需求非常吻合。如果在美国使用，则可能需要将脚本(中的值)调整的稍大一些；如果在欧洲使用，则可能需要将脚本(中的值)稍稍缩小一些。 YMMV。

Usage:
用法：

```
[rbowen@sasha:community-tools/scripts]$ ./tshirts.py                                                                                                                                                          
How many shirts? 300
For a total of 300 shirts, order:

30.0 small
72.0 medium
96.0 large
72.0 xl
30.0 2xl
```

### **[followers.py][6]**

This script provides me with the follower count for Twitter handles I care about.
该脚本为我提供了我关心的 Twitter 账号的关注者数量。

This script is only 14 lines long and isn't exciting, but it saves me perhaps ten minutes of loading web pages and looking for a number.
该脚本只有 14 行，并不令人兴奋，但是它可能节省我十分钟的加载网页和查找数字的时间。

You'll need to edit the feeds array to add the accounts you care about:
您需要编辑 `feed` 数组以添加您关心的帐户：

```
feeds = [
        'centosproject',
        'centos'
        ];
```

NB: It probably won't work if you're running it outside of English-speaking countries, because it's just a simple screen-scraping script that reads HTML and looks for particular information buried within it. So when the output is in a different language, the regular expressions won't match.
注意：如果你在英语国家以外（的地区）运行它，则可能无法正常工作，因为它只是一个简单的屏幕抓取脚本，可读取 HTML 并查找其中包含的特定信息。因此，当输出使用其他语言时，正则表达式将不匹配。

Usage:
用法：

```
[rbowen@sasha:community-tools/scripts]$ ./followers.py                                                                                                                                                                          
centosproject: 11,479 Followers
centos: 18,155 Followers
```

### **[get_meetups][7]**

This script fits into another category—API scripts. This particular script uses the [meetup.com][8] API to look for meetups on a particular topic in a particular area and time range so that I can report them to my community. Many of the services you rely on provide an API so that your scripts can look up information without having to manually look through web pages. Learning how to use those APIs can be frustrating and time-consuming, but you'll end up with skills that will save you a LOT of time.
该脚本纳入另一种类别的脚本——API脚本。这个特定的脚本使用 [meetup.com][8]（网站）API 寻找在特定区域和时间范围内有关特定主题的聚会，以便我可以向社区报告。您所依赖的许多服务都提供了 API，因此您的脚本可以查找信息，而无需手动浏览网页。学习如何使用这些 API 既令人沮丧又耗时，但是最终将获得可以节省大量时间的技能。

_Disclaimer: [meetup.com][8] changed their API in August of 2019, and I have not yet updated this script to the new API, so it doesn't actually work right now. Watch this repo for a fixed version in the coming weeks._
_免责声明：[meetup.com][8] 已于2019年8月更改了他们的 API，目前为止已经不能为新的 API 更新此脚本了，因此它实际上暂时不起作用。在接下来的几周内关注此版本的修复版本。_

### **[centos-announcements.pl][9]**

This script is considerably more complicated and extremely specific to my use case, but you probably have a similar situation. This script looks at a mailing list archive—in this case, the centos-announce mailing list—and finds messages that are in a particular format, then builds a report of those messages. Reports come in a couple of different formats—one for my monthly newsletter and one for scheduling messages (via Hootsuite) for Twitter.
该脚本在我所使用的实例中是相当复杂的和非常明确的，但你可能有类似的情况。在本例中该脚本查看邮件列表存档（`centos-announce` 邮件列表），并查找具有特定格式的邮件，然后生成这些邮件的报告。报告有两种不同的格式——一种用于我的每月新闻通讯，另一种用于安排 Twitter 信息（借助于 Hootsuite）。

I use Hootsuite to schedule content for Twitter, and they have a convenient CSV (comma-separated value) format that lets you bulk-schedule a whole week of tweets in one go. Auto-generating that CSV from various data sources (i.e., mailing lists, blogs, other web pages) can save you a lot of time. Do note, however, that this should probably only be used for a first draft, which you then examine and edit yourself so that you don't end up auto-tweeting something you didn't intend to.
我使用 `Hootsuite` 为 Twitter 安排内容，它们具有便捷的 CSV（逗号分隔值）格式，你可以一次批量安排整整一周的推文。从不同数据源（比如：邮件列表，博客，其他网页）自动生成 CSV 格式可以节省大量时间。但是请注意，这可能仅应用于初稿，然后您可以对其进行检查和编辑，以便最终不会自动发布你不想要内容的推文。
### **[reporting.pl][10]**

This script is also fairly specific to my particular needs, but the concept itself is universal. I send out a monthly mailing to the [CentOS SIGs][11] (Special Interest Groups), which are scheduled to report in that given month. This script simply tells me which SIGs those are this month, and writes the email that needs to go to them.
该脚本也非常符合我的特定需求，但是概念本身是通用的。我每月向 [CentOS SIG][11]（特殊兴趣小组）发送邮件，这些邮件计划在给定的月份报告。该脚本只是告诉我本月有哪些 SIG，并记录需要发送给他们的电子邮件。

It does not actually send that email, however, for a couple of reasons. One, I may wish to edit those messages before they go out. Two, while scripts sending email worked great in the old days, these days, they're likely to result in getting spam-filtered.
但是，因以下两个原因，实际上并未发送该电子邮件。第一，我希望在消息发送之前对其进行编辑。第二，虽然发送电子邮件的脚本在过去很有效，但如今，很可能被当做垃圾邮件而被过滤。
### In conclusion
综上所述（总结）

There are some other scripts in that repo that are more or less specific to my particular needs, but I hope at least one of them is useful to you, and that the variety of what's there inspires you to automate something of your own. I'd love to see your handy automation script repos, too; link to them in the comments!
该存储库中还有一些其他脚本或多或少是针对我的特定需求的，但是我希望其中至少有一个脚本对你有用，并且激发你使自己的某些需要自动化。我也希望看到你方便的自动化脚本存储库；在评论中链接他们！
--------------------------------------------------------------------------------

via: https://opensource.com/article/20/3/automating-community-management-python

作者：[Rich Bowen][a]
选题：[lujun9972][b]
译者：[stevenzdg988](https://github.com/stevenzdg988)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/rbowen
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/Open%20Pharma.png?itok=GP7zqNZE (shapes of people symbols)
[2]: http://drbacchus.com/what-does-a-community-manager-do/
[3]: https://6dollarshirts.com/rocket-surgery
[4]: https://github.com/rbowen/centos-community-tools/tree/master/scripts
[5]: https://github.com/rbowen/centos-community-tools/blob/master/scripts/tshirts.py
[6]: https://github.com/rbowen/centos-community-tools/blob/master/scripts/followers.py
[7]: https://github.com/rbowen/centos-community-tools/blob/master/scripts/get_meetups
[8]: http://meetup.com
[9]: https://github.com/rbowen/centos-community-tools/blob/master/scripts/centos-announcements.pl
[10]: https://github.com/rbowen/centos-community-tools/blob/master/scripts/sig_reporting/reporting.pl
[11]: https://wiki.centos.org/SpecialInterestGroup
