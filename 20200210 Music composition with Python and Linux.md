[#]: collector: (lujun9972)
[#]: translator: (stevenzdg988)
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Music composition with Python and Linux)
[#]: via: (https://opensource.com/article/20/2/linux-open-source-music)
[#]: author: (Alan Formy-Duval https://opensource.com/users/alanfdoss)

Music composition with Python and Linux
用 Python 和 Linux 进行音乐创作
======
A chat with Mr. MAGFest—Brendan Becker.
![Wires plugged into a network switch][1]
与 MAGFest 先生的聊天——Brendan Becker。
![接入网络交换机的网络线缆][1]

I met Brendan Becker working in a computer store in 1999. We both enjoyed building custom computers and installing Linux on them. Brendan was always involved in several technology projects at once, ranging from game coding to music composition. Fast-forwarding a few years from the days of computer stores, he went on to write [pyDance][2], an open source implementation of multiple dancing games, and then became the CEO of music and gaming event [MAGFest][3]. Sometimes referred to as "Mr. MAGFest" because he was at the helm of the event, Brendan now uses the music pseudonym "[Inverse Phase][4]" as a composer of chiptunes—music predominantly made on 8-bit computers and game consoles.
1999 年，我遇到了在一家计算机商店工作的 Brendan Becker。我们都喜欢构建定制计算机并在其上安装 Linux。 Brendan 总是同时参与多个技术项目，从游戏编程到音乐创作。从电脑商店的日子快进几年，他继续编写[pyDance][2]，一个多跳舞游戏的开源实现，然后成为音乐和游戏项目[MAGFest][3]的 CEO。有时被称为 “Mr. MAGFest”，因为他是项目的负责人，Brendan 现在使用音乐笔名 “[Inverse Phase][4]” 作为 `chiptunes`(电子和音)的作曲家——主要在8位计算机和游戏控制台上制作音乐。

I thought it would be interesting to interview him and ask some specifics about how he has benefited from Linux and open source software throughout his career.
我认为采访他并询问他在整个职业生涯中如何从 Linux 和开源软件中受益的一些细节会很有趣。

![Inverse Phase performance photo][5]
![Inverse Phase 表演照片][5]

版权所有 Nickeledge, CC BY-SA 2.0.

### Alan Formy-Duval: 您是如何开始使用计算机和软件的？

Brendan Becker: There's been a computer in my household almost as far back as I can remember. My dad has fervently followed technology; he brought home a Compaq Portable when they first hit the market, and when he wasn't doing work on it, I would have access to it. Since I began reading at age two, using a computer became second nature to me—just read what it said on the disk, follow the instructions, and I could play games! Some of the time I would be playing with learning and education software, and we had a few disks full of games that I could play other times. I remember a single disk with a handful of free clones of popular titles. Eventually, my dad showed me that we could call other computers (BBS'ing at age 5!), and I saw where some of the games came from. One of the games I liked to play was written in BASIC, and all bets were off when I realized that I could simply modify the game by just reading a few things and re-typing them to make my game easier.
Brendan Becker：从我记事起，我家就有一台电脑。我父亲热衷于技术；当 Compaq Portable 第一次大量上市时，他带了一台回家，当他不用它工作时，我可以使用它。自从我两岁开始阅读来，使用电脑就成了我的第二天性——只要阅读磁盘上的内容，按照说明进行操作，我就可以玩游戏了！有时我会玩学习和教育软件，我们有几张装满游戏的磁盘，我可以在其他时间玩。我记得有一个磁盘，里面有一些流行主题的免费克隆。最终，我父亲向我展示了我们可以调用其他计算机（5 岁时在 BBS 上！），我看到了一些游戏的来源。我喜欢玩的一款游戏是用 BASIC 编写的，当我意识到我可以简单地修改游戏时，只需阅读一些内容并重新输入它们以使我的游戏更容易，所有的赌注都被取消了。

### Formy-Duval: 这是 80 年代？

Becker: The Compaq Portable dropped in 1983 to give you a frame of reference. My dad had one of the first of that model.
Becker： Compaq Portable 康柏便携式电脑于 1983 年推出，为您提供了一个参考框架。我爸爸有第一个那个模型。

### Formy-Duval: 您是如何进入 Linux 和开源软件的？

Becker: I was heavy into MODs and demoscene stuff in the early 90s, and I noticed that Walnut Creek ([cdrom.com][6]; now defunct) ran shop on FreeBSD. I was super curious about Unix and other operating systems in general, but didn't have much firsthand exposure, and thought it might be time to finally try something. DOOM had just released, and someone told me I might even be able to get it to run. Between that and being able to run cool internet servers, I started going down the rabbit hole. Someone saw me reading about FreeBSD and suggested I check out Linux, this new OS that was written from the ground up for x86, unlike BSD, which (they said) had some issues with compatibility. So, I joined #linuxhelp on undernet IRC and asked how to get started with Linux, pointing out that I had done a modicum of research (asking "what's the difference between Red Hat and Slackware?") and probing mainly about what would be easiest to use. The only person talking in the channel said that he was 13 years old and he could figure out Slackware, so I should not have an issue. A math teacher in my school gave me a hard disk, I downloaded the "A" disk sets and a boot disk, wrote it out, installed it, and didn't spend much time looking back.
Becker：在 90 年代初我酷爱 MOD 和演示场景的东西，我注意到 Walnut Creek（[cdrom.com][6]；现已解散）在 FreeBSD 上运行商店。总的来说，我对 Unix 和其他操作系统非常好奇，但没有太多的第一手资料，认为是时候尝试一些东西了。DOOM 刚刚发布，有人告诉我甚至可以让它运行。在这与能够运行很酷的互联网服务器之间，我开始陷入困境。有人看到我在阅读有关 FreeBSD 的文章，并建议我检查 Linux，这是一个重新为 x86 编写的新操作系统，与 BSD 不同，后者（他们说）存在一些兼容性问题。因此，我加入了在线交谈网络 IRC 上的 `#linuxhelp` 并询问如何开始使用 Linux，指出我已经做了一些研究（询问 “Red Hat 和 Slackware 之间有什么区别？”）并主要探讨什么是最简单的使用。频道里唯一说话的人说他已经 13 岁了，他可以弄清楚 Slackware，所以我应该没有问题。学校的一个数学老师给了我一个硬盘，我下载了 “A” 盘组和一个启动盘，写了出来，安装了它，回头看并没有花太多时间。

### Formy-Duval: 你是如何被称为 MAGFest 先生的？

Becker: Well, this one is pretty easy. I became the acting head of MAGFest almost immediately after the first event. The former chairpeople were all going their separate ways, and I demanded the event not be canceled to the guy in charge. The solution was to run it myself, and that nickname became mine as I slowly molded the event into my own.
Becker：嗯，这个很简单。在第一个项目后，我几乎立即成为了 MAGFest 的代理负责人。前任主席都各奔东西，我向负责人要求不要取消项目。解决方案是自己运行它，当我慢慢地将项目塑造成我自己的时，这个昵称就成了我的。

### Formy-Duval: I remember attending in those early days. How large did MAGFest eventually become?我记得在那些早期参加过。 MAGFest 最终有多大？

Becker: The first MAGFest was 265 people. It is now a scary huge 20,000+ unique attendees.
Becker：第一届 MAGFest 是 265 人。现在是一个可怕的庞大的罕见的 20,000+ 出席者。

### Formy-Duval: That is huge! Can you briefly describe the MAGFest convention?太棒了！您能简要描述一下 MAGFest 大会吗？

Becker: One of my buddies, Hex, described it really well. He said, "It's like this video-game themed birthday party with all of your friends, but there happen to be a few thousand people there, and all of them can be your friends if you want, and then there are rock concerts." This was quickly adopted and shortened to "It's a four-day video game party with multiple video game rock concerts." Often the phrase "music and gaming festival" is all people need to get the idea.
Becker：我的一个朋友 Hex 描述得非常好。他说：“就像是和你所有的朋友一起举办这个以电子游戏为主题的生日派对，但那里恰好有几千人，如果你愿意，他们都可以成为你的朋友，然后还有摇滚音乐会。” 这很快被采用并缩短为 “这是一个为期四天的视频游戏派对，有多个视频游戏摇滚音乐会”。通常 “音乐和游戏节” 这个措词是人们所需要的。

### Formy-Duval: How did you make use of open source software in running MAGFest?您是如何利用开源软件来运行 MAGFest 的？

Becker: At the time I became the head of MAGFest, I had already written a game in Python, so I felt most comfortable also writing our registration system in Python. It was a pretty easy decision since there were no costs involved, and I already had the experience. Later on, our online registration system and rideshare interfaces were written in PHP/MySQL, and we used Kboard for our forums. Eventually, this evolved to us rolling our own registration system from scratch in Python, which we also use at the event, and running Drupal on the main website. At one point, I also wrote a system to manage the video room and challenge stations in Python. Oh, and we had a few game music listening stations that you could flip through tracks and liner notes of iconic game OSTs (Original Sound Tracks) and bands who played MAGFest.

Becker：当我成为 MAGFest 的负责人时，我已经用 Python 编写了一个游戏，所以我觉得用 Python 编写我们的注册系统最舒服。这是一个非常容易的决定，因为不涉及任何成本，而且我已经有了经验。后来，我们的在线注册系统和拼车界面都是用 PHP/MySQL 编写的，我们的论坛使用了 Kboard。最终，从无到有逐渐形成在 Python 中滚动我们自己的注册系统，我们也在项目中使用它，并在主网站上运行 Drupal。有一次，我还用 Python 编写了一个系统来管理视频室和邀请比赛站。哦，我们有一些游戏音乐收听站，你可以翻阅曲目，标志性游戏的班轮笔记 OST（原始音轨）和演奏 MAGFest 的乐队。

### Formy-Duval: I understand that a few years ago you reduced your responsibilities at MAGFest to pursue new projects. What was your next endeavor?我知道几年前你减少了你在 MAGFest 的职责，去追求新的项目。你接下来的努力是什么？

Becker: I was always rather heavily into the game music scene and tried to bring as much of it to MAGFest as possible. As I became a part of those communities more and more, I wanted to participate. I wrote some medleys, covers, and arrangements of video game tunes using free, open source versions of the DOS and Windows demoscene tools that I had used before, which were also free but not necessarily open source. I released a few tracks in the first few years of running MAGFest, and then after some tough love and counseling from Jake Kaufman (also known as virt; Shovel Knight and Shantae are on his resume, among others), I switched gears to something I was much better at—chiptunes. Even though I had written PC speaker beeps and boops as a kid with my Compaq Portable and MOD files in the demoscene throughout the 90s, I released the first NES-spec track that I was truly proud to call my own in 2006. Several pop tributes and albums followed.
Becker：我一直非常投入游戏音乐领域，并试图将尽可能多的音乐带到 MAGFest 中。随着我越来越多地成为这些社区的一部分，我想参与其中。我使用我以前使用过的免费开源版本的 DOS 和 Windows 演示场景工具编写了一些视频游戏曲调的混合曲、封面和编曲，这些工具也是免费的，但不一定是开源的。我在运行 MAGFest 的最初几年发布了一些曲目，然后在 Jake Kaufman（也被称为 `virt`；其中包括 Shovel Knight 和 Shantae 等人在他的简历上）的一些严厉的爱和建议之后，我改变主题到我更擅长的—— `chiptunes`(电子和音)。尽管我在 90 年代的演示场景中用我的 Compaq Portable 和 MOD 文件编写了 PC 扬声器的哔哔声和嘘声，但我还是在 2006 年发布了第一首 NES-spec 曲目，我真的很自豪地称之为我自己的曲目。专辑紧随其后。

In 2010, I was approached by multiple individuals for game soundtrack work. Even though the soundtrack work didn't affect it much, I began to scale back some of my responsibilities with MAGFest more seriously, and in 2011, I decided to take a much larger step into the background. I would stay on the board as a consultant and help people learn what they needed to run their departments, but I was no longer at the helm. At the same time, my part-time job, which was paying the bills, laid off all of their workers, and I suddenly found myself with a lot of spare time. I began writing Pretty Eight Machine, a Nine Inch Nails tribute, which I spent over a year on, and between that and the game soundtrack work, I proved to myself that I could put food on the table (if only barely) with music, and this is what I wanted to do next.
2010 年，有很多人找我做游戏配乐工作。尽管配乐工作对它没有太大影响，但我开始更认真地缩减我在 MAGFest 的一些职责，并且在 2011 年，我决定在后台采取更大的步骤。我会留在董事会担任顾问，帮助人们了解他们需要什么来管理他们的部门，但我不再掌舵了。与此同时，我的兼职工作，即支付账单，解雇了他们所有的工人，我突然发现自己有很多空闲时间。我开始写 Pretty Eight Machine， Nine Inch Nails 致敬，我花了一年多，在那和游戏配乐工作之间，我向自己证明了我可以用音乐把食物放在桌子上（如果只是勉强），这就是我接下来想做的。

###

![Inverse Phase CTM 跟踪器][7]

Copyright Inverse Phase, Used with permission.
版权所有 Inverse Phase,经许可使用。

### Formy-Duval: What is your workspace like in terms of hardware and software?就硬件和软件而言，您的工作空间是什么样的？

Becker: In my DOS/Windows days, I used mostly FastTracker 2. In Linux, I replaced that with SoundTracker (not Karsten Obarski's original, but a GTK rewrite; see [soundtracker.org][8]). These days, SoundTracker is in a state of flux—although I still need to try the new GTK3 version—but [MilkyTracker][9] is a good replacement when I can't use SoundTracker. Good old FastTracker 2 also runs in DOSBox, if I really need the original. This was when I started using Linux, however, so this is stuff I figured out 20-25 years ago.
Becker：在我的 DOS/Windows 时代，我主要使用 FastTracker 2。在 Linux 中，我将其替换为 SoundTracker（不是 Karsten Obarski 的原始版本，而是 GTK 重写；参见 [soundtracker.org][8]）。这些天，SoundTracker 处于不断变化的状态——虽然我仍然需要尝试新的 GTK3 版本——但是当我无法使用 SoundTracker 时，[MilkyTracker][9] 是一个很好的替代品。如果我真的需要原版，那么好老的 FastTracker 2 也可以在 DOSBox 中运行。然而，那是我开始使用 Linux 的时候，所以这是我在 20-25 年前发现的东西。

Within the last ten years, I've gravitated away from sample-based music and towards chiptunes—music synthesized by old sound chips from 8- and 16-bit game systems and computers. There is a very good cross-platform tool called [Deflemask][10] to write music for a lot of these systems. A few of the systems I want to write music for aren't supported, though, and Deflemask is closed source, so I've begun building my own music composition environment from scratch with Python and [Pygame][11]. I maintain my code tree using Git and will control hardware synthesizer boards using open source [KiCad][12].
在过去的十年里，我已经从基于样本的音乐转向了`chiptunes`(电子和音)——由来自 8 位和 16 位游戏系统和计算机的旧声音芯片合成的音乐。有一个非常好的跨平台工具 [Deflemask][10] 可以为许多这些系统编写音乐。不过，我想为其创作音乐的一些系统不受支持，而且 Deflemask 是闭源的，因此我已经开始使用 Python 和 [Pygame][11] 从头开始构建自己的音乐创作环境。我使用 Git 维护我的代码树，并将使用开源 [KiCad][12] 控制硬件合成器板。

### Formy-Duval: What projects are you currently focused on?您目前专注于哪些项目？

Becker: I work on game soundtracks and music commissions off and on. While that's going on, I've also been working on starting an electronic entertainment museum called [Bloop][13]. We're doing a lot of cool things with archival and inventory, but perhaps the most exciting thing is that we've been building exhibits with Raspberry Pis. They're so versatile, and it's weird to think that, if I had tried to do this even ten years ago, I wouldn't have had small single-board computers to drive my exhibits; I probably would have bolted a laptop to the back of a flat-panel!
Becker：我断断续续地制作游戏配乐和音乐委员会。在此期间，我还一直致力于创办一个名为 [Bloop][13] 的电子娱乐博物馆。我们在档案和详细目录方面做了很多很酷的事情，但也许最令人兴奋的是我们一直在用 Raspberry Pi 构建展览。它们是如此多才多艺，而且很奇怪，如果我在十年前尝试这样做，我就不会拥有小型单板计算机来驱动我的展品；我可能会用螺栓将笔记本电脑固定在平板的背面！

### Formy-Duval: There are a lot more game platforms coming to Linux now, such as Steam, Lutris, and Play-on-Linux. Do you think this trend will continue, and these are here to stay?现在有更多游戏平台进入 Linux，例如 Steam、Lutris 和 Play-on-Linux。您认为这种趋势会持续下去吗？这些会一直存在吗？

Becker: As someone who's been gaming on Linux for 25 years—in fact, I was brought to Linux _because_ of games—I think I find this question harder than most people would. I've been running Linux-native games for decades, and I've even had to eat my "either a Linux solution exists or can be written" words back in the day, but eventually, I did, and wrote a Linux game.
Becker：作为一个在 Linux 上玩了 25 年游戏的人——事实上，我被带到 Linux _是因为_ 游戏——我想我认为这个问题比大多数人更难。几十年来，我一直在运行 Linux 原生游戏，我甚至不得不对“存在 Linux 解决方案或可以编写”的话表示食言，但最终，我做到了，编写了一个 Linux 游戏。

Real talk: Android's been out since 2008. If you've played a game on Android, you've played a game on Linux. Steam's been available for Linux for eight years. The Steambox/SteamOS was announced only a year after Steam. I don't hear a whole lot about Lutris or Play-on-Linux, but I know they exist and hope they succeed. I do see a pretty big following for GOG, and I think that's pretty neat. I see a lot of quality game ports coming out of people like Ryan Gordon (icculus) and Ethan Lee (flibitijibibo), and some companies even port in-house. Game engines like Unity and Unreal already support Linux. Valve has incorporated Proton into the Linux version of Steam for something like two years now, so now Linux users don't even have to search for Linux-native versions of their games.
真心话：Android 于 2008 年问世。如果您在 Android 上玩过游戏，那么您就在 Linux 上玩过游戏。Steam 已可用于 Linux 八年。Steambox/SteamOS 仅在 Steam 发布一年后发布。我没有听到很多关于 Lutris 或 Play-on-Linux 的消息，但我知道它们存在并希望它们成功。我确实看到 GOG 的追随者非常多，我认为这非常好。我看到很多高质量的游戏端口来自 Ryan Gordon (icculus) 和 Ethan Lee (flibitijibibo) 等人，甚至有些公司在内部移植。Unity 和 Unreal 等游戏引擎已经支持 Linux。Valve 已经将 Proton 纳入 Linux 版本的 Steam 已有两年左右的时间了，所以现在 Linux 用户甚至不必搜索他们游戏的 Linux 原生版本。

I can say that I think most gamers expect and will continue to expect the level of support they're already receiving from the retail game market. Personally, I hope that level goes up and not down!
我可以说，我认为大多数游戏玩家期待并将继续期待他们已经从零售游戏市场获得的支持水平。就我个人而言，我希望这个水平增长而不是下降！

_Learn more about Brendan's work as [Inverse Phase][14]._
_详细了解 Brendan 担任 [Inverse Phase][14] 的工作。_

--------------------------------------------------------------------------------

via: https://opensource.com/article/20/2/linux-open-source-music

作者：[Alan Formy-Duval][a]
选题：[lujun9972][b]
译者：[stevenzdg988](https://github.com/stevenzdg988)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/alanfdoss
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/rh_003499_01_other21x_cc.png?itok=JJJ5z6aB (Wires plugged into a network switch)
[2]: http://icculus.org/pyddr/
[3]: http://magfest.org/
[4]: http://www.inversephase.com/
[5]: https://opensource.com/sites/default/files/uploads/inverse_phase_performance_bw.png (Inverse Phase performance photo)
[6]: https://en.wikipedia.org/wiki/Walnut_Creek_CDROM
[7]: https://opensource.com/sites/default/files/uploads/inversephase_ctm_tracker_screenshot.png (Inverse Phase CTM Tracker)
[8]: http://soundtracker.org
[9]: http://www.milkytracker.org
[10]: http://www.deflemask.com
[11]: http://www.pygame.org
[12]: http://www.kicad-pcb.org
[13]: http://bloopmuseum.com
[14]: https://www.inversephase.com
