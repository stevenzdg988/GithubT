[#]: subject: "10 Git tutorials to level up your open source skills in 2022"
[#]: via: "https://opensource.com/article/22/1/git-tutorials"
[#]: author: "Manaswini Das https://opensource.com/users/manaswinidas"
[#]: collector: "lujun9972"
[#]: translator: "stevenzdg988"
[#]: reviewer: " "
[#]: publisher: " "
[#]: url: " "

10 Git tutorials to level up your open source skills in 2022
2022 年提升开源技能的 10 个 Git 学习指南
======
These articles contain hacks, lesser-known facts, and tips and tricks
that can come in handy while working with Git.
这些文章包含黑客，鲜为人知的事实，以及在使用 Git 时可以派上用场提示和技巧。

![Business woman on laptop sitting in front of window][1]
![坐在窗前笔记本电脑前的女商人][1]

Git is an indispensable part of the code-sharing development workflow. Be you a beginner or an expert, this powerful version control system is the first thing you are expected to learn when working with open source code. You don't need to know everything under the sun when it comes to Git, but knowing specific hacks makes sharing your code a lot easier on platforms like GitLab, so you can collaborate with developers far and near. If there's something you're not sure about, `git --help` can come to your rescue.

Git 是代码共享开发工作流程中不可或缺的一部分。无论您是初学者还是专家，第一件事就是在使用开源代码时需要学习这个功能强大的版本控制系统。在谈到 Git 时，不需要知道所有事情，但是了解一些特性可以让您在 GitLab 等平台上更轻松地共享代码，因此您可以与不同地方的开发人员协作。如果有什么没把握的地方，`git --help` 可以帮助你。

I'm amazed every day by the amount of control that knowing Git provides. There is not a single instance when you can't revert to an earlier version, however impossible or sticky the situation you may be in.
我每天都对 Git 提供的已知控制数量感到惊讶。没有一个无法恢复到早期版本的实例，无论您所处的情况是多么不可能或棘手。

Opensource.com had a great set of articles regarding Git in 2021; I'm summarizing just the top 10. All the articles contain hacks, lesser-known facts, and tips and tricks that can come in handy while working with Git.
在 2021 年 Opensource.com 有大量关于 Git 的文章；我只汇总了前 10 名。所有文章都包含包含黑客，鲜为人知的事实，以及在使用 Git 时可以派上用场提示和技巧。
### A practical guide to using the git stash command 使用 git stash 命令的实用指南

[Ramakrishna Pattnaik][2] explains the functions of the [git stash command][3]. This article highlights how `git stash` can help you list, check, save, and retrieve changes to ensure a hassle-free experience when switching branches. It can also help you track changes locally without committing and while maintaining a clean working directory.
[Ramakrishna Pattnaik][2] 解释了 [git stash 命令][3] 的功能。这篇文章重点介绍 `git stash` 如何帮助您列出、检查、保存和恢复更改，以确保切换分支时的无忧体验。它还可以帮助您跟踪在本地无需提交的更改而，同时保持干净的工作目录。

### 5 commands to level up your Git game 5 个 Git 命令快速升级你的游戏

[Seth Kenlon][4] details [five lesser-known Git commands][5] that can make your life easier. Developers can save time with commands like `git whatchanged, git stash, git worktree,` and `git cherry-pick`.
[Seth Kenlon][4] 详细介绍了 [五个鲜为人知的 Git 命令][5]，它们可以让您的生活更轻松。开发人员可以使用 `git whatchanged`、`git stash`、`git worktree` 和 `git cherry-pick` 等命令来节省时间。

### What is Git cherry-picking? 什么是 

This tutorial by [Rajeev Bera][6] walks you through the what, why, and how of the [git cherry-pick command][7] and lists all possible use cases when `git cherry-pick` will help you escape a sticky situation.
[Rajeev Bera][6] 教程将引导您了解 [git cherry-pick 命令][7] 的内容、原因和方式，并列出所有可能的用例，`git cherry-pick` 可以帮助您避免棘手的情况。

### 3 reasons I use the git cherry-pick command 使用 git cherry-pick 命令的 3 个原因

I share how [leveraging git cherry-pick][8] can help you avoid redundancy, handle multiple commits in one go, and restore lost changes.
我分享了 [利用 git cherry-pick][8] 如何帮助您避免冗余、一次性处理多个提交并恢复丢失的更改。

### Experiment on your code freely with git worktree 使用 git worktree 自由地尝试你的代码

The `git stash` command takes care of saving changes to a working directory. Seth Kenlon introduces us to `git worktree` and the several [git worktree use cases][9] that can help you get a repository back to a known state.
`git stash` 命令负责将更改保存到工作目录。Seth Kenlon 向我们介绍了 `git worktree` 和几个 [git worktree 用例][9]，它们可以帮助您将存储库恢复到已知状态。

### 4 tips for context switching in Git  4 个 Git 上下文切换的技巧

This article by [Olaf Alders][10] discusses the pros and cons of [four different ways of switching branches][11] while working with Git. These options will help you simplify your workflow and maintain a clean working directory without losing your changes.
[Olaf Alders][10] 的这篇文章讨论了使用 Git 时[四种不同的切换分支方式][11] 的优缺点。这些选项将帮助您简化工作流程并保持干净的工作目录，而不会丢失您的更改。

### Find what changed in a Git commit 查找 Git 提交中的更改

Seth Kenlon explains how to leverage simple commands like [git log and git whatchanged][12] to extract specific information regarding what changed in a Git commit. It's a helpful shortcut, and the name makes it easy to remember.
Seth Kenlon 解释了如何利用如 [git log 和 git whatchanged][12] 等简单命令来提取有关 Git 提交内容中更改的特定信息。这是一个有用的快捷方式，而且名字很容易记住。

### 7 Git tips for managing your home directory 7 个管理主目录的 Git 技巧

Seth Kenlon shares the dos and don'ts of [managing and organizing $HOME with Git][13] and explains how it made his life more convenient across devices. Even better, it's freed him to experiment with new ideas, knowing he can roll them back easily.
Seth Kenlon 分享了磁盘操作系统和 [使用 Git 管理和组织 $HOME 变量][13] 的注意事项，并解释了它如何让他的跨设备生活更实用。更好的是，这让他可以自由地尝试新想法，因为他知道他可以轻松地将它们回滚。

### GitOps vs. DevOps: What's the difference? GitOps 与 DevOps：有什么区别？

[Bryant Son][14] introduces you to [GitOps,][15] which he describes as an evolved version of DevOps that uses Git as the single source of truth. The article also lists helpful resources available on Opensource.com for learning DevOps and landing a job in open source.
[Bryant Son][14] 向您介绍了 [GitOps,][15]，他将其描述为 DevOps 的进化版本，它使用 Git 作为单一事实来源。 这篇文章还列出了 Opensource.com 上可用于学习 DevOps 和在开源领域找到工作的有用资源。

### Get started with Argo CD 开始使用 Argo CD

[Ayush Sharma][16] details the advantages of [Argo CD,][17] a pull-based GitOps development tool. Argo CD gives you the best of both worlds by managing Kubernetes manifests in Git and syncing them in a cluster.
[Ayush Sharma][16] 详细介绍了 [Argo CD,][17] 一种基于拉取式的 GitOps 开发工具的优势。Argo CD 通过在 Git 中管理 Kubernetes 清单并将它们同步到集群中，为您提供两全其美的体验。

Can you think of other Git hacks that make your life easier? Please let us know in the comments or [send us an article idea][18].
你能想到其他让你的生活更轻松的 Git 技巧吗？请在评论中告诉我们或[向我们发送文章创意][18]。

--------------------------------------------------------------------------------

via: https://opensource.com/article/22/1/git-tutorials

作者：[Manaswini Das][a]
选题：[lujun9972][b]
译者：[stevenzdg988](https://github.com/stevenzdg988)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/manaswinidas
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/lenovo-thinkpad-laptop-concentration-focus-windows-office.png?itok=-8E2ihcF (Woman using laptop concentrating)
[2]: https://opensource.com/users/rkpattnaik780
[3]: https://opensource.com/article/21/4/git-stash
[4]: https://opensource.com/users/seth
[5]: https://opensource.com/article/21/4/git-commands
[6]: https://opensource.com/users/acompiler
[7]: https://opensource.com/article/21/4/cherry-picking-git
[8]: https://opensource.com/article/21/3/git-cherry-pick
[9]: https://opensource.com/article/21/4/git-worktree
[10]: https://opensource.com/users/oalders
[11]: https://opensource.com/article/21/4/context-switching-git
[12]: https://opensource.com/article/21/4/git-whatchanged
[13]: https://opensource.com/article/21/4/git-home
[14]: https://opensource.com/users/brson
[15]: https://opensource.com/article/21/3/gitops
[16]: https://opensource.com/users/ayushsharma
[17]: https://opensource.com/article/21/8/argo-cd
[18]: https://opensource.com/how-submit-article
