[#]: collector: (lujun9972)
[#]: translator: (stevenzdg988)
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (9 favorite open source tools for Node.js developers)
[#]: via: (https://opensource.com/article/20/1/open-source-tools-nodejs)
[#]: author: (Hiren Dhadhuk https://opensource.com/users/hirendhadhuk)

9 favorite open source tools for Node.js developers
9 个 Node.js 开发人员最喜欢的开源工具
======
Of the wide range of tools available to simplify Node.js development,
here are the 10 best.
![Tools illustration][1]
在可用于简化 Node.js 开发的各种工具中，
以下 10 种是最佳选择。
![工具说明][1]

I recently read a survey on [StackOverflow][2] that said more than 49% of developers use Node.js for their projects. This came as no surprise to me.
我最近在 [StackOverflow][2] 上阅读了一项调查，该调查称超过 49％ 的开发人员在其项目中使用 Node.js。这对我来说不足为奇。

As an avid user of technology, I think it's safe to say that the introduction of Node.js led to a new era of software development. It is now one of the most preferred technologies for software development, right next to JavaScript.
作为热衷于技术的用户，我可以肯定地说 Node.js 的采用引领了软件开发的新时代。现在，它仅次于 JavaScript 成为最受欢迎的软件开发技术之一。

### What is Node.js, and why is it so popular?
Node.js 是什么，为什么它如此受欢迎？

Node.js is a cross-platform, open source runtime environment for executing JavaScript code outside of the browser. It is also a preferred runtime environment built on Chrome's JavaScript runtime and is mainly used for building fast, scalable, and efficient network applications.
Node.js 是一个跨平台的开源运行环境，用于在浏览器外部执行 JavaScript 代码。它也是基于 Chrome 的 JavaScript 运行时创建的首选运行环境，主要用于快速创建，可扩展和高效的网络应用程序。

I remember when we used to sit for hours and hours coordinating between front-end and back-end developers who were writing different scripts for each side. All of this changed as soon as Node.js came into the picture. I believe that the one thing that drives developers towards this technology is its two-way efficiency.
记得当时我们花费几个小时来协调为各自编写不同脚本的前端和后端开发人员。当 Node.js 出现后，所有这些都改变了。我相信，促使开发人员采用这项技术是因为它的双向效率。

With Node.js, you can run your code simultaneously on both the client and the server side, speeding up the whole process of development. Node.js bridges the gap between front-end and back-end development and makes the development process much more efficient.
使用 Node.js，您可以同时在客户端和服务器端运行代码，从而加快了整个开发过程。Node.js 弥合了前端和后端开发之间的差距，并使开发过程更加高效。

### A wave of Node.js tools
一波 Node.js 工具

For 49% of all developers (including me), Node.js is at the top of the pyramid when it comes to front-end and back-end development. There are tons of [Node.js use cases][3] that have helped me and my team deliver complex projects within our deadlines. Fortunately, Node.js' rising popularity has also produced a wave of open source projects and tools to help developers working with the environment.
对于 49％ 的开发人员（包括我），Node.js 在前端和后端开发方面处于金字塔顶端。有大量的 [Node.js 用例][3] 帮助我和我的团队在截止日期之内交付复杂的项目。幸运的是，Node.js 的日益普及也产生了一系列开源项目和工具，以帮助开发人员使用该环境。

Recently, there has been a sudden increase in demand for projects built with Node.js. Sometimes, I find it quite challenging to manage these projects and keep up the pace while delivering high-quality results. So I decided to automate certain aspects of development using some of the most efficient of the many open source tools available for Node.js developers.
最近，对使用 Node.js 构建的项目的需求突然增加。有时，我发现管理这些项目并同时保持交付高质量项目的步伐非常具有挑战性。因此，我决定使用一些为 Node.js 开发人员提供的许多可用的开源工具中最高效的工具，使某些方面的开发自动化。

In my extensive experience with Node.js, I've worked with a wide range of tools that have helped me with the overall development process—from streamlining the coding process to monitoring to content management.
根据我在 Node.js 方面的丰富经验，我使用了许多的工具，这些工具对整个开发过程都非常有帮助-从简化编码过程到监测再到内容管理。

To help my fellow Node.js developers, I compiled this list of 9 of my favorite open source tools for simplifying Node.js development.
为了帮助我的 Node.js 开发同道，我整理了最喜欢的 9 种开源工具清单，以简化 Node.js 开发。

### Webpack

[Webpack][4] is a handy JavaScript module bundler used to simplify front-end development. It detects modules with dependencies and transforms them into static assets that represent the modules.
[Webpack][4] 是一个容易使用的 JavaScript 模块捆绑程序，用于简化前端开发。它检测具有依赖的模块，并将其转换为静态的描述模块。

You can install the tool through either the npm or Yarn package manager.
可以通过软件包管理器 npm 或 Yarn 安装该工具。

With npm:
利用 npm 命令安装如下：

```
`npm install --save-dev webpack`
```

With Yarn:
利用 Yarn 命令安装如下：

```
`yarn add webpack --dev`
```

Webpack creates single bundles or multiple chains of assets that can be loaded asynchronously at runtime. Each asset does not have to be loaded individually. Bundling and serving assets becomes quick and efficient with the Webpack tool, making the overall user experience better and reducing the developer's hassle in managing load time.
Webpack 创建可以在运行时异步加载的单个包或多重约束。不必单独加载。使用 Webpack 工具可以快速高效地打包和提供服务，从而改善用户整体体验，并减少开发人员在管理加载时间方面的困难。

### Strapi

[Strapi][5] is an open source headless content management system (CMS). A headless CMS is basically software that lets you manage your content devoid of a prebuilt frontend. It is a backend-only system that functions using RESTful APIs.
[Strapi][5] 是一个开放源代码的无头内容管理系统（CMS）。无头 CMS 是一种基础软件，可以管理内容而无需预先构建前端。是一个只使用 RESTful API 功能的后端系统。

You can install Strapi through Yarn or npx packages.
可以通过软件包管理器 Yarn 或 npx 安装 Strapi。

With Yarn:
利用 Yarn 命令安装如下：

```
`yarn create strapi-app my-project --quickstart`
```

With npx:
利用 npx 命令安装如下：

```
`npx create-strapi-app my-project --quickstart`
```

Strapi's goal is to fetch and deliver your content in a structured manner across any device. The CMS makes it easy to manage your applications' content and make sure they are dynamic and accessible across any device.
Strapi 的目标是在任何设备上以结构化的方式获取和交付内容。CMS 使您可以轻松管理应用程序的内容，并确保它们是动态的并且可以访问任何设备。

It provides a lot of features, including file upload, a built-in email system, JSON Web Token (JWT) authentication, and auto-generated documentation. I find it very convenient, as it simplifies the overall CMS and gives me full autonomy in editing, creating, or deleting all types of contents.
它提供了许多功能，包括文件上传，内置的电子邮件系统，JSON Web Token （JWT）验证和自动生成文档。我发现它非常方便，因为它简化了整个 CMS，并为我提供了编辑，创建或删除所有类型内容的完全自主权。

In addition, the content structure built through Strapi is extremely flexible because you can create and reuse groups of content and customizable APIs.
另外，通过 Strapi 构建的内容结构非常灵活，因为您可以创建和重用内容组和可定制的 API。

### Broccoli

[Broccoli][6] is a powerful build tool that runs on an [ES6][7] module. Build tools are software that let you assemble all the different assets within your application or website, e.g., images, CSS, JavaScript, etc., into one distributable format. Broccoli brands itself as the "asset pipeline for ambitious applications."
[Broccoli][6] 是一个功能强大的构建工具，可在 [ES6][7] 模块上运行。生成工具是一种软件，可让您将应用程序或网站中的所有不同的有用内容（例如图像，CSS，JavaScript 等）组合成一种可分配的格式。Broccoli 将自己称为 “雄心勃勃的应用程序的有用管道”。

You need a project directory to work with Broccoli. Once you have the project directory in place, you can install Broccoli with npm using:
您需要一个项目目录才能使用 Broccoli。放置好项目目录后，可以使用以下命令通过 npm 安装 Broccoli：

```
npm install --save-dev broccoli
npm install --global broccoli-cli
```

You can also use Yarn for installation. 
您也可以使用 Yarn 进行安装。

The current version of Node.js would be the best version for the tool as it provides long-time support. This helps you avoid the hassle of updating and reinstalling as you go. Once the installation process is completed, you can include the build specification in your Brocfile.js.
当前版本的 Node.js 是该工具的最佳版本，因为对它提供了长期的支持。可以帮助您避免进行更新和重新安装过程中的麻烦。安装过程完成后，可以在 Brocfile.js 文件中包含创建规范。

In Broccoli, the unit of abstraction is a tree, which stores files and subdirectories within specific subdirectories. Therefore, before you build, you must have a specific idea of what you want your build to look like.
在 Broccoli 中，抽象单位是树，该树将文件和子目录存储在特定子目录中。因此，在创建之前，您必须对要构建的外观有一个特定的了解。必须有一个明确的想法，你想让创建的看起来与其一样。

The best part about Broccoli is that it comes with a built-in server for development that lets you host your assets on a local HTTP server. Broccoli is great for streamlined rebuilds, as its concise architecture and flexible ecosystem boost rebuild and compilation speeds. Broccoli lets you get organized to save time and maximize productivity during development.
Broccoli最好的部分是，它带有用于开发的内置服务器，可让您将有用的内容托管在本地 HTTP 服务器上。Broccoli 非常适合合理化重建，因为其简洁的架构和灵活的生态系统可提高重建和编译速度。Broccoli 可让您井井有条，以节省时间并在开发过程中最大限度地提高生产力。

### Danger

[Danger][8] is a very handy open source tool for streamlining your pull request (PR) checks. As Danger's library description says, the tool helps you "formalize" your code review system by managing PR checks. Danger integrates with your CI and helps you speed up the review process.
[Danger][8] 是一个非常方便的开源工具，用于简化您的拉取请求（PR）检查。正如 Danger 库描述所说，该工具可通过管理 PR 检查来帮助 “形式化” 您的代码检查系统。Danger 与您的 CI 集成在一起，可帮助您加快审核过程。

Integrating Danger with your project is an easy step-by-step process—you just need to include the Danger module and create a Danger file for each project. However, it's more convenient to create a Danger account (easy to do through GitHub or Bitbucket), then set up access tokens for your open source software projects.
将 Danger 与您的项目集成是一个简单的分步过程-您只需要包括 Danger 模块并为每个项目创建一个 Danger 文件。然而，创建一个Danger 帐户（通过 GitHub 或 Bitbucket 轻松完成），并且为开源软件项目设置访问令牌更加方便。

Danger can be installed via NPM or Yarn. To use Yarn, add danger -D to add it to your package.JSON.
可以通过 NPM 或 Yarn 安装 Danger。要使用 Yarn，请添加 Danger -D 将其添加到 package.JSON 中。

After you add Danger to your CI, you can:
将 Danger 添加到 CI 后，您可以：

  * Highlight build artifacts of importance
  * Manage sprints by enforcing links to tools like Trello and Jira
  * Enforce changelogs
  * Utilize descriptive labels
  * And much more
  * 高亮显示创建建重要的工件
  * 通过强制链接到 Trello 和 Jira 之类的工具来管理 sprint
  * 强制更新日志
  * 使用描述性标签
  * 以及更多

For example, you can design a system that defines the team culture and sets out specific rules for code review and PR checks. Common issues can be solved based on the metadata Danger provides along with its extensive plugin ecosystem.
例如，您可以设计一个定义团队文化并为代码审查和 PR 检查设定特定规则的系统。常见议题可以根据 Danger 提供的元数据及其广泛的插件生态系统来解决。

### Snyk

Cybersecurity is a major concern for developers. [Snyk][9] is one of the most well-known tools to fix vulnerabilities in open source components. It started as a project to fix vulnerabilities in Node.js projects and has evolved to detect and fix vulnerabilities in Ruby, Java, Python, and Scala apps as well. Snyk mainly runs in four stages:
网络安全是开发人员的主要关注点。[Snyk][9] 是修复开源组件中漏洞的最著名工具之一。它最初是一个用于修复 Node.js 项目漏洞的项目，并且已经演变为可以检测并修复 Ruby，Java，Python 和 Scala 应用程序中的漏洞。Snyk 主要运行四个阶段：

  * Finding vulnerability dependencies
  * Fixing specific vulnerabilities
  * Preventing security risks by PR checks
  * Monitoring apps continuously
  * 查找漏洞依赖性
  * 修复特定漏洞
  * 通过 PR 检查预防安全风险
  * 持续监控应用程序

Snyk can be integrated with your project at any stage, including coding, CI/CD, and reporting. I find it extremely helpful for testing Node.js projects to test out npm packages for security risks or at build-time. You can also run PR checks for your applications in GitHub to make your projects more secure. Synx also provides a range of integrations that you can use to monitor dependencies and fix specific problems.
Snyk 可以在任何阶段与项目集成，包括编码，CI/CD 和报告。我发现这对于测试 Node.js 项目以测试 npm 软件包是否存在安全风险或在构建时非常有帮助。您还可以在 GitHub 中为您的应用程序运行 PR 检查，以使您的项目更安全。Synx 还提供了一系列集成，可用于监视依赖关系并解决特定问题。

To run Snyk on your machine locally, you can install it through NPM:
要在本地计算机上运行 Snyk，可以通过 NPM 安装它：

```
`npm install -g snyk`
```

### Migrat

[Migrat][10] is an extremely easy to use data-migration tool that uses plain text. It works across a diverse range of stacks and processes that make it even more convenient. You can install Migrat with a simple line of code:
[Migrat][10] 是一种非常易于使用的使用纯文本的数据迁移工具。 它可在各种堆栈和进程中工作，从而使其更加实用。您可以使用简单的代码行安装 Migrat：

```
`$ npm install -g migrat`
```

Migrat is not specific to a particular database engine. It supports multi-node environments, as migrations can run on one node globally or once per server. What makes Migrat convenient is the facilitation of passing context to each migration.
Migrat 不是特定于特别的数据库引擎。它支持多节点环境，因为迁移可以在一个全局节点上运行，也可以在每个服务器上运行一次。使 Migrat 方便的原因是便于将上下文传递给每个迁移。

You can define what each migration is for (e.g.,. database sets, connections, logging interfaces, etc.). Moreover, to avoid haphazard migrations, where multiple servers are running migrations globally, Migrat facilitates global lockdown while the process is running so that it can run only once globally. It also comes with a range of plug-ins for SQL databases, Slack, HipChat, and the Datadog dashboard. You can send live migrations to any of these platforms.
您可以定义每种迁移的用途（例如，数据库集，连接，日志记录接口等）。此外，为了避免随意迁移，即多个服务器正在全局范围内进行迁移，Migrat 有助于在进程运行时进行全局锁定，从而使其只能在全局范围内运行一次。它还附带了一系列用于 SQL 数据库，Slack，HipChat 和 Datadog 仪表盘的插件。您可以将实时迁移状况发送到任意一个平台。

### Clinic.js

[Clinic.js][11] is an open source monitoring tool for Node.js projects. It combines three different tools—Doctor, Bubbleprof, and Flame—that help you monitor, detect, and solve performance issues with Node.js.
[Clinic.js][11] 是一个用于 Node.js 项目的开源监视工具。它结合了三种不同的工具 Doctor，Bubbleprof 和 Flame，可利用 Node.js 帮助您监视，检测和解决性能问题。

You can install Clinic.js from npm by running this command:
您可以通过运行以下命令从 npm 安装 Clinic.js：

```
`$ npm install clinic`
```

You can choose which of the three tools that comprise Clinic.js you want to use based on which aspect of your project you want to monitor and the report you want to generate:
您可以根据要监视项目的某个方面以及要生成的报告，选择要使用的包含 Clinic.js 的三个工具中的一个：

  * Doctor provides detailed metrics by injecting probes and provides recommendations on the overall health of your project.
  * Bubbleprof is great for profiling and generates metrics using async_hooks.
  * Flame is great for uncovering hot paths and bottlenecks in your code.
  * Doctor 通过注入探针来提供详细的指标，并就项目的总体运行状况提供建议。
  * Bubbleprof 非常适合分析，并使用 `async_hooks` 生成标准。
  * Flame 非常适合发现代码中的热路径和瓶颈。

### PM2

Monitoring is one of the most important aspects of any backend development process. [PM2][12] is a process management tool for Node.js that helps developers monitor multiple aspects of their projects such as logs, delays, and speed. The tool is compatible with Linux, MacOS, and Windows and supports all Node.js versions starting from Node.js 8.X.
监视是任何后端开发过程中最重要的一方面。[PM2][12] 是 Node.js 的进程管理工具，可帮助开发人员监视项目的多个方面，例如日志，延迟和速度。该工具与 Linux，MacOS 和 Windows 兼容，并支持从 Node.js 8.X 开始的所有 Node.js 版本。

You can install PM2 with npm using:
您可以使用以下命令通过 npm 安装 PM2：

```
`$ npm install pm2 --g`
```

If you do not already have Node.js installed, you can use:
如果尚未安装 Node.js，则可以使用以下命令安装：

```
`wget -qO- https://getpm2.com/install.sh | bash`
```

Once it's installed, start the application with:
安装完成后，使用以下命令启动应用程序：

```
`$ pm2 start app.js`
```

The best part about PM2 is that it lets you run your apps in cluster mode. You can spawn a process for multiple CPU cores at a time. This makes it easy to enhance application performance and maximize reliability. PM2 is also great for updates, as you can update your apps and reload them with zero downtime using the "hot reload" option. Overall, it's a great tool to simplify process management for Node.js applications.
关于 PM2 的最好之处在于，可以在集群模式下运行应用程序。可以同时为多个 CPU 内核生成一个进程。这样可以轻松增强应用程序性能并最大程度地提高可靠性。PM2也非常适合更新，因为您可以使用 “热重载” 选项更新应用程序并以零停机时间重新加载应用程序。总体而言，它是为 Node.js 应用程序简化进程管理的好工具。

### Electrode

[Electrode][13] is an open source application platform from Walmart Labs. The platform helps you build large-scale, universal React/Node.js applications in a structured manner.
[Electrode][13] 是 Walmart Labs 的开源应用程序平台。该平台可帮助您以结构化方式构建大规模通用的 React/Node.js 应用程序。

The Electrode app generator lets you build a flexible core focused on the code, provides some great modules to add complex features to the app, and comes with a wide range of tools to optimize your app's Node.js bundle.
Electrode 应用程序生成器使您可以构建专注于代码的灵活内核，提供一些出色的模块以向应用程序添加复杂功能，并提供了广泛的工具来优化应用程序的 Node.js 包。

Electrode can be installed using npm. Once the installation is finished, you can start the app using Ignite and dive right in with the Electrode app generator.
可以使用 npm 安装 Electrode。安装完成后，您可以使用 Ignite 启动应用程序，并直接使用 Electrode 应用程序生成器进行深入研究。

You can install Electrode using NPM:
您可以使用 NPM 安装 Electrode：

```
`npm install -g electrode-ignite xclap-cli`
```

### Which are your favorite?
你最喜欢哪一个？

These are just a few of the always-growing list of open source tools that can come in handy at different stages when working with Node.js. Which are your go-to open source Node.js tools? Please share your recommendations in the comments.
这些只是不断增长的开源工具列表中的一小部分，在使用 Node.js 时，这些工具可以在不同阶段派上用场。您最喜欢使用哪些开源 Node.js 工具？请在评论中分享您的建议。
--------------------------------------------------------------------------------

via: https://opensource.com/article/20/1/open-source-tools-nodejs

作者：[Hiren Dhadhuk][a]
选题：[lujun9972][b]
译者：[stevenzdg988](https://github.com/stevenzdg988)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/hirendhadhuk
[b]: https://github.com/lujun9972
[1]: https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/tools_hardware_purple.png?itok=3NdVoYhl (Tools illustration)
[2]: https://insights.stackoverflow.com/survey/2019#technology-_-other-frameworks-libraries-and-tools
[3]: https://www.simform.com/nodejs-use-case/
[4]: https://webpack.js.org/
[5]: https://strapi.io/
[6]: https://broccoli.build/
[7]: https://en.wikipedia.org/wiki/ECMAScript#6th_Edition_-_ECMAScript_2015
[8]: https://danger.systems/
[9]: https://snyk.io/
[10]: https://github.com/naturalatlas/migrat
[11]: https://clinicjs.org/
[12]: https://pm2.keymetrics.io/
[13]: https://www.electrode.io/
