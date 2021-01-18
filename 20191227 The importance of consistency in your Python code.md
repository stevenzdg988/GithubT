[#]: collector: (lujun9972)
[#]: translator: (stevenzdg988)
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (The importance of consistency in your Python code)
[#]: via: (https://opensource.com/article/19/12/zen-python-consistency)
[#]: author: (Moshe Zadka https://opensource.com/users/moshez)

The importance of consistency in your Python code
Python代码前后一致的重要性
======
This is part of a special series about the Zen of Python focusing on the
12th, 13th, and 14th principles: the roles of ambiguity and obviousness.
本部分是有关 Python 之禅的特殊系列，聚焦在第 12,13,14 规范：角色的二义和明确
![Two animated computers waving one missing an arm][1]
![两台栩栩如生的计算机挥舞着独臂][1]
The principle of least surprise is [a guideline][2] when designing user interfaces. It says that when the user performs an action, the program should do whatever would surprise the user the least. This is for the same reason kids love reading the same book over and over again: there is nothing more comforting to people than the ability to predict and have those predictions come true.
设计用户界面的规范是 [准则][2]。它说，当用户执行一个操作时，程序应该做最不会让用户感到惊讶的事情。这和孩子们喜欢一遍又一遍地读同一本书的原因是一样的:没有什么比能够预测并让预测成真更让人欣慰的了。

A critical insight in the development of the [ABC language][3], Python's inspiration, was that programming languages are user interfaces and need to be designed with the same tools that UI designers use. Thankfully, since then, more languages have adopted the concepts of affordance and ergonomics from UI design, even if they apply them less strictly.
在[ABC 语言][3] (Python 的灵感来源)的发展过程中，一个重要的见解是，编程设计是用户界面，需要 UI 设计者使用相同工具来设计。值得庆幸的是，从那以后，越来越多的语言采用了 UI 设计中的可视化和人体工程学概念，即使它们的应用并不严格。

This brings us to the next three principles in the [Zen of Python][4].
这就引出了 [Python 之禅][4] 中的三个规范。
### In the face of ambiguity, refuse the temptation to guess.当存在多种可能，不要尝试去猜测。

What should the result of **1 + "1"** be? Both **"11"** and **2** would be valid guesses. This expression is _ambiguous_: there is no single thing it can do that would not be a surprise to at least some people.
**1 + "1"**的结果应该是什么? **“11”** 和 **2** 都是猜测。这个表达是 _ambiguous_：没有任何事情可以做，这至少对某些人来说并不令人惊讶。
Some languages choose to guess. In JavaScript, the result is **"11"**. In Perl, the result is **2**. In C, naturally, the result is the empty string. In the face of ambiguity, JavaScript, Perl, and C all guess.
一些语言选择猜测。在 JavaScript 中，结果为 **“11”**。在 Perl 中，结果为 ** 2 **。在 C 语言中，结果自然是空字符串。面对歧义，JavaScript，Perl 和 C 都在猜测。

In Python, this raises a **TypeError**: an error that is not silent. It is atypical to catch **TypeError**: it will usually terminate the program or at least the current task (for example, in most web frameworks, it will terminate the handling of the current request).
在 Python 中，这会引发 **TypeError**：不是非静音的错误。捕获 **TypeError** 是非典型的：它通常将终止程序或至少终止当前任务（例如，在大多数Web框架中，它将终止对当前请求的处理）。 

Python refuses to guess what **1 + "1"** means. The programmer is forced to write code with clear intention: either **1 + int("1")**, which would be **2**; or **str(1) + "1"**, which would be **"11"**; or **"1"[1:]**, which would be an empty string. By refusing to guess, Python makes programs more predictable.
Python 拒绝猜测 ** 1 + "1" **的含义。程序员被迫以明确的意图编写代码：** 1 + int("1")**，即 ** 2 **；或者 ** str(1) + "1" **，即 **"11"**;或 ** "1"[1：] **，这将是一个空字符串。通过拒绝猜测，Python 使程序更具可预测性。

### There should be one—and preferably only one—obvious way to do it.
尽量找一种，最好是唯一一种明显的解决方案

Prediction also goes the other way. Given a task, can you predict the code that will be written to achieve it? It is impossible, of course, to predict perfectly. Programming, after all, is a creative task.

However, there is no reason to intentionally provide multiple, redundant ways to achieve the same thing. There is a sense in which some solutions are "better" or "more Pythonic."

Part of the appreciation for the Pythonic aesthetic is that it is OK to have healthy debates about which solution is better. It is even OK to disagree and keep programming. It is even OK to agree to disagree for the sake of harmony. But beneath it all, there has to be a feeling that, eventually, the right solution will come to light. There must be the hope that eventually we can live in true harmony by agreeing on the best way to achieve a goal.

### Although that way may not be obvious at first (unless you're Dutch).
虽然这并不容易，因为你不是 Python 之父

This is an important caveat: It is often _not_ obvious, at first, what is the best way to achieve a task. Ideas are evolving. _Python_ is evolving. The best way to read a file block-by-block is, probably, to wait until Python 3.8 and use the [walrus operator][5].

This common task, reading a file block-by-block, did not have a "single best way to do it" for almost _30 years_ of Python's existence.

When I started using Python in 1998 with Python 1.5.2, there was no single best way to read a file line-by-line. For many years, the best way to know if a dictionary had a key was to use **.haskey**, until the **in** operator became the best way.

It is only by appreciating that sometimes, finding the one (and only one) way of achieving a goal can take 30 years of trying out alternatives that Python can keep aiming to find those ways. This view of history, where 30 years is an acceptable time for something to take, often feels foreign to people in the United States, when the country has existed for just over 200 years.

The Dutch, whether it's Python creator [Guido van Rossum][6] or famous computer scientist [Edsger W. Dijkstra][7], have a different worldview according to this part of the Zen of Python. A certain European appreciation for time is essential to appreciate it.

--------------------------------------------------------------------------------

via: https://opensource.com/article/19/12/zen-python-consistency

作者：[Moshe Zadka][a]
选题：[lujun9972][b]
译者：[译者ID](https://github.com/译者ID)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/moshez
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/rh_003499_01_other11x_cc.png?itok=I_kCDYj0 (Two animated computers waving one missing an arm)
[2]: https://www.uxpassion.com/blog/the-principle-of-least-surprise/
[3]: https://en.wikipedia.org/wiki/ABC_(programming_language)
[4]: https://www.python.org/dev/peps/pep-0020/
[5]: https://www.python.org/dev/peps/pep-0572/#abstract
[6]: https://en.wikipedia.org/wiki/Guido_van_Rossum
[7]: http://en.wikipedia.org/wiki/Edsger_W._Dijkstra
