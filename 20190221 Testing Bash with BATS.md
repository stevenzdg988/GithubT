[#]: collector: (lujun9972)
[#]: translator: (stevenzdg988)
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Testing Bash with BATS)
[#]: via: (https://opensource.com/article/19/2/testing-bash-bats)
[#]: author: (Darin London https://opensource.com/users/dmlond)

Testing Bash with BATS
用 BATS 测试 Bash
======
The Bash Automated Testing System puts Bash code through the same types of testing processes used by Java, Ruby, and Python developers.
Bash 自动测试系统通过 Java，Ruby 和 Python 开发人员所使用的相同类型的测试进程来提交 Bash 代码。

![](https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/todo_checklist_team_metrics_report.png?itok=oB5uQbzf)

Software developers writing applications in languages such as Java, Ruby, and Python have sophisticated libraries to help them maintain their software's integrity over time. They create tests that run applications through a series of executions in structured environments to ensure all of their software's aspects work as expected.
用Java，Ruby和Python等语言编写应用程序的软件开发人员拥有完善的库，可以帮助他们随着时间的推移保持软件的完整性。他们创建测试，以在结构化环境中通过一系列执行来运行应用程序，以确保其所有软件方面均按预期工作。

These tests are even more powerful when they're automated in a continuous integration (CI) system, where every push to the source repository causes the tests to run, and developers are immediately notified when tests fail. This fast feedback increases developers' confidence in the functional integrity of their applications.
当这些测试在持续集成（CI）系统中自动化时甚至会更加健壮，在这种情况下，每次推送到源知识库都会使测试运行，并且在测试失败时会立即通知开发人员。这种快速反馈提高了开发人员对其应用程序功能完整性的信心。

The Bash Automated Testing System ([BATS][1]) enables developers writing Bash scripts and libraries to apply the same practices used by Java, Ruby, Python, and other developers to their Bash code.
Bash 自动测试系统（[BATS][1]）使开发人员能够编写 Bash 脚本和库，以将Java，Ruby，Python 和其他开发人员所使用的相同惯例应用于其 Bash 代码。

### Installing BATS

The BATS GitHub page includes installation instructions. There are two BATS helper libraries that provide more powerful assertions or allow overrides to the Test Anything Protocol ([TAP][2]) output format used by BATS. These can be installed in a standard location and sourced by all scripts. It may be more convenient to include a complete version of BATS and its helper libraries in the Git repository for each set of scripts or libraries being tested. This can be accomplished using the **[git submodule][3]** system.
“BATS GitHub” 页面包含安装指令。有两个 BATS 帮助程序函数库，它们提供更强大的断言或允许使用 BATS 重写 Test Anything Protocol(测试协议)([TAP][2])输出格式。可以将它们安装在标准位置，并由所有脚本提供。在 Git 知识库中包含完整版本的 BATS 及其帮助函数库对于要测试的每组脚本或函数库可能会更实用。这可以使用 **[git submodule][3]** (git 子模块)系统来完成。

The following commands will install BATS and its helper libraries into the **test** directory in a Git repository.
以下命令会将 BATS 及其帮助函数库安装到 Git 知识库中的 **test** 目录中。

```
git submodule init
git submodule add https://github.com/sstephenson/bats test/libs/bats
git submodule add https://github.com/ztombol/bats-assert test/libs/bats-assert
git submodule add https://github.com/ztombol/bats-support test/libs/bats-support
git add .
git commit -m 'installed bats'
```

To clone a Git repository and install its submodules at the same time, use the
**\--recurse-submodules** flag to **git clone**.
要克隆 Git 知识库并同时安装其子模块，请使用
**\-recurse-submodules** 为 **git clone** 标记。

Each BATS test script must be executed by the **bats** executable. If you installed BATS into your source code repo's **test/libs** directory, you can invoke the test with:
每个 BATS 测试脚本必须由 **bats** 可执行文件执行。如果您将 BATS 安装到源代码知识库的 **test/libs** 目录中，则可以使用以下命令调用测试：

```
./test/libs/bats/bin/bats <path to test script>
```

Alternatively, add the following to the beginning of each of your BATS test scripts:
或者，将以下内容添加到每个 BATS 测试脚本的开头：

```
#!/usr/bin/env ./test/libs/bats/bin/bats
load 'libs/bats-support/load'
load 'libs/bats-assert/load'
```

and **chmod +x <path to test script>**. This will a) make them executable with the BATS installed in **./test/libs/bats** and b) include these helper libraries. BATS test scripts are typically stored in the **test** directory and named for the script being tested, but with the **.bats** extension. For example, a BATS script that tests **bin/build** should be called **test/build.bats**.
并且执行命令 **chmod +x <测试脚本的路径>**。 这将 a) 使它们与安装在 **./test/libs/bats** 中的 BATS 可执行，并且 b) 包括这些帮助函数库。BATS 测试脚本通常存储在 **test** 目录中，并为要测试的脚本命名，扩展名为 **.bats**。例如，测试 **bin/build** 的 BATS 脚本应称为 **test/build.bats**。

You can also run an entire set of BATS test files by passing a regular expression to BATS, e.g., **./test/lib/bats/bin/bats test/*.bats**.
您还可以通过正则表达式传递给 BATS 来运行整套 BATS 测试文件，例如 **./test/lib/bats/bin/bats test/*.bats**。

### Organizing libraries and scripts for BATS coverage
为 BATS 组织函数库和脚本的重写范围

Bash scripts and libraries must be organized in a way that efficiently exposes their inner workings to BATS. In general, library functions and shell scripts that run many commands when they are called or executed are not amenable to efficient BATS testing.
Bash 脚本和库必须以一种有效地将其内部工作暴露给 BATS 的方式进行组织。通常，在调用或执行时库函数和运行诸多命令的 Shell 脚本不适合进行有效的 BATS 测试。

For example, [build.sh][4] is a typical script that many people write. It is essentially a big pile of code. Some might even put this pile of code in a function in a library. But it's impossible to run a big pile of code in a BATS test and cover all possible types of failures it can encounter in separate test cases. The only way to test this pile of code with sufficient coverage is to break it into many small, reusable, and, most importantly, independently testable functions.
例如，[build.sh][4] 是许多人编写的典型脚本。本质上是一大堆代码。有些人甚至可能将这堆代码放入库中的函数中。但是，不可能在 BATS 测试中运行大量代码并涵盖在单独的测试用例中可能遇到的所有类型的故障。测试具有足够重写范围的这堆代码的唯一方法是将其分解为许多小的，可重用的，最重要的是可独立测试的功能。

It's straightforward to add more functions to a library. An added benefit is that some of these functions can become surprisingly useful in their own right. Once you have broken your library function into lots of smaller functions, you can **source** the library in your BATS test and run the functions as you would any other command to test them.
向库添加更多功能(函数)很简单。额外的好处是其中一些功能本身可以变得出奇的有用。将库函数分解为许多较小的函数后，您可以在 BATS 测试中 **source** 库，并像测试任何其他命令一样运行这些函数。

Bash scripts must also be broken down into multiple functions, which the main part of the script should call when the script is executed. In addition, there is a very useful trick to make it much easier to test Bash scripts with BATS: Take all the code that is executed in the main part of the script and move it into a function, called something like **run_main**. Then, add the following to the end of the script:
Bash 脚本还必须分解为多个函数，执行脚本时，脚本的主要部分应调用这些函数。此外，还有一个非常有用的技巧，可以使使用 BATS 测试 Bash 脚本变得更加容易：将脚本主要部分中执行的所有代码都移到一个函数中，称为 **run_main**。然后，将以下内容添加到脚本的末尾：

```
if [[ "${BASH_SOURCE[0]}" == "${0}" ]]
then
  run_main
fi
```

This bit of extra code does something special. It makes the script behave differently when it is executed as a script than when it is brought into the environment with **source**. This trick enables the script to be tested the same way a library is tested, by sourcing it and testing the individual functions. For example, here is [build.sh refactored for better BATS testability][5].
这段额外的代码做了一些特殊的事情。它使脚本当作为脚本执行时与使用 **source** 进入环境时的行为有所不同。此技巧使通过与测试库相同的方式测试脚本和测试各个函数功能成为可能。例如，利用脚本 [build.sh 重构以获得更好的 BATS 可测试性][5]。

### Writing and running tests
编写和运行测试

As mentioned above, BATS is a TAP-compliant testing framework with a syntax and output that will be familiar to those who have used other TAP-compliant testing suites, such as JUnit, RSpec, or Jest. Its tests are organized into individual test scripts. Test scripts are organized into one or more descriptive **@test** blocks that describe the unit of the application being tested. Each **@test** block will run a series of commands that prepares the test environment, runs the command to be tested, and makes assertions about the exit and output of the tested command. Many assertion functions are imported with the **bats** , **bats-assert** , and **bats-support** libraries, which are loaded into the environment at the beginning of the BATS test script. Here is a typical BATS test block:
如上所述，BATS 是一个 TAP 兼容测试框架，其语法和输出对于使用过其他 TAP 兼容测试套件（例如 JUnit，RSpec 或 Jest）的用户来说将是熟悉的。它的测试被组织进各个测试脚本。测试脚本被组织进一个或多个描述性 **@test** 块中，它们描述了被测试应用程序的单元。每个 **@test** 块都将运行一系列准备测试环境命令，运行要测试的命令，并对退出和被测试命令的输出进行断言。许多断言函数是通过 **bats** , **bats-assert** , 和 **bats-support** 库导入的，这些库在 BATS 测试脚本的开头加载到环境中。下面是一个典型的 BATS 测试块：

```
@test "requires CI_COMMIT_REF_SLUG environment variable" {
  unset CI_COMMIT_REF_SLUG
  assert_empty "${CI_COMMIT_REF_SLUG}"
  run some_command
  assert_failure
  assert_output --partial "CI_COMMIT_REF_SLUG"
}
```

If a BATS script includes **setup** and/or **teardown** functions, they are automatically executed by BATS before and after each test block runs. This makes it possible to create environment variables, test files, and do other things needed by one or all tests, then tear them down after each test runs. [**Build.bats**][6] is a full BATS test of our newly formatted **build.sh** script. (The **mock_docker** command in this test will be explained below, in the section on mocking/stubbing.)
如果 BATS 脚本包含 **setup(安装)** 和/或 **teardown(拆卸)** 功能，则 BATS 将在每个测试块运行之前和之后自动执行它们。这样就可以创建环境变量，测试文件以及执行一个或所有测试所需的其他操作，然后在每次测试运行后将其拆卸。[**Build.bats**][6] 是对我们新格式化的 **build.sh** 脚本的完整 BATS 测试。（此测试中的 **mock_docker** 命令将在以下关于模拟/桩的部分中进行说明。）

When the test script runs, BATS uses **exec** to run each **@test** block as a separate subprocess. This makes it possible to export environment variables and even functions in one **@test** without affecting other **@test** s or polluting your current shell session. The output of a test run is a standard format that can be understood by humans and parsed or manipulated programmatically by TAP consumers. Here is an example of the output for the **CI_COMMIT_REF_SLUG** test block when it fails:
当测试脚本运行时，BATS 使用 **exec** 来将每个 **@test** 块作为单独的子进程运行。这样就可以在一个 **@test** 中导出环境变量甚至函数，而不会影响其他 **@test** 或污染您当前的 Shell 会话。测试运行的输出是一种标准格式，可以被人理解，并且可以由 TAP 用户以编程方式进行解析或操作。下面是 **CI_COMMIT_REF_SLUG** 测试块失败时的输出示例：

```
 ✗ requires CI_COMMIT_REF_SLUG environment variable
   (from function `assert_output' in file test/libs/bats-assert/src/assert.bash, line 231,
    in test file test/ci_deploy.bats, line 26)
     `assert_output --partial "CI_COMMIT_REF_SLUG"' failed

   -- output does not contain substring --
   substring (1 lines):
     CI_COMMIT_REF_SLUG
   output (3 lines):
     ./bin/deploy.sh: join_string_by: command not found
     oc error
     Could not login
   --

   ** Did not delete , as test failed **

1 test, 1 failure
```

Here is the output of a successful test:
下面是成功测试的输出：

```
✓ requires CI_COMMIT_REF_SLUG environment variable
```

### Helpers

Like any shell script or library, BATS test scripts can include helper libraries to share common code across tests or enhance their capabilities. These helper libraries, such as **bats-assert** and **bats-support** , can even be tested with BATS.
像任何 Shell 脚本或库一样，BATS 测试脚本可以包括帮助程序库，以在测试之间共享通用代码或增强其性能。这些帮助程序库，例如 **bats-assert** 和 **bats-support** 甚至可以使用 BATS 进行测试。

Libraries can be placed in the same test directory as the BATS scripts or in the **test/libs** directory if the number of files in the test directory gets unwieldy. BATS provides the **load** function that takes a path to a Bash file relative to the script being tested (e.g., **test** , in our case) and sources that file. Files must end with the prefix **.bash** , but the path to the file passed to the **load** function can't include the prefix. **build.bats** loads the **bats-assert** and **bats-support** libraries, a small **[helpers.bash][7]** library, and a **docker_mock.bash** library (described below) with the following code placed at the beginning of the test script below the interpreter magic line:
如果测试目录中的文件数量庞大，则可以将库放置在同一测试目录中作为 BATS 脚本，也可以将它们放置在 **test/libs** 目录中。BATS 提供了 **load** 函数，该函数采用相对于要测试的脚本的 Bash 文件的路径（例如，在我们的示例中的 **test**），并声明该文件。文件必须以前缀 **.bash** 结尾，但是传递给 **load** 函数的文件路径不能包含前缀。**build.bats** 加载 **bats-assert** 和 **bats-support** 库，一个小型 **[helpers.bash][7]** 库以及 **docker_mock.bash** 库（如下所述），以下代码位于解释器调谐线下方的测试脚本的开头：

```
load 'libs/bats-support/load'
load 'libs/bats-assert/load'
load 'helpers'
load 'docker_mock'
```

### Stubbing test input and mocking external calls
测试输入桩和模拟外部调用

The majority of Bash scripts and libraries execute functions and/or executables when they run. Often they are programmed to behave in specific ways based on the exit status or output ( **stdout** , **stderr** ) of these functions or executables. To properly test these scripts, it is often necessary to make fake versions of these commands that are designed to behave in a specific way during a specific test, a process called "stubbing." It may also be necessary to spy on the program being tested to ensure it calls a specific command, or it calls a specific command with specific arguments, a process called "mocking." For more on this, check out this great [discussion of mocking and stubbing][8] in Ruby RSpec, which applies to any testing system.
大多数 Bash 脚本和库运行时执行函数和(或)可执行文件。通常，它们被程序化为基于特定方式运行退出状态或这些函数或可执行文件的输出（**stdout**，**stderr**）。为了正确地测试这些脚本，通常需要制作这些命令的伪版本，这些被设计用来在特定测试过程中以特定方式运行，称为“桩(桩？)”。可能还需要监视正在测试的程序，以确保其调用了特定命令，或者使用特定参数调用了特定命令，此过程称为“模拟”。有关更多信息，请查看在 Ruby RSpec 中适用于任何测试系统的伟大的 [有关模拟和桩的讨论][8]。

The Bash shell provides tricks that can be used in your BATS test scripts to do mocking and stubbing. All require the use of the Bash **export** command with the **-f** flag to export a function that overrides the original function or executable. This must be done before the tested program is executed. Here is a simple example that overrides the **cat** executable:
Bash shell 提供了的技巧，可以在您的 BATS 测试脚本中使用进行模拟和桩。所有这些都需要使用带有 **-f** 标志的 Bash **export** 命令来导出重写原始函数或可执行文件的函数。必须在测试程序执行之前完成此操作。下面是重写可执行命令 **cat** 的简单示例：

```
function cat() { echo "THIS WOULD CAT ${*}" }
export -f cat
```

This method overrides a function in the same manner. If a test needs to override a function within the script or library being tested, it is important to source the tested script or library before the function is stubbed or mocked. Otherwise, the stub/mock will be replaced with the actual function when the script is sourced. Also, make sure to stub/mock before you run the command you're testing. Here is an example from **build.bats** that mocks the **raise** function described in **build.sh** to ensure a specific error message is raised by the login function:
此方法以相同的方式重写函数。如果测试需要重写要测试的脚本或库中的函数，则在对函数进行桩或模拟之前，必须先声明已测试脚本或库，这一点很重要。否则，在声明脚本时，桩/模拟将被原函数替代。另外，在运行即将进行的测试命令之前确认桩/模拟。下面是**build.bats**的示例，该示例模拟**build.sh**中描述的**raise**函数，以确保利用登录函数引发特定的错误消息：

```
@test ".login raises on oc error" {
  source ${profile_script}
  function raise() { echo "${1} raised"; }
  export -f raise
  run login
  assert_failure
  assert_output -p "Could not login raised"
}
```

Normally, it is not necessary to unset a stub/mock function after the test, since **export** only affects the current subprocess during the **exec** of the current **@test** block. However, it is possible to mock/stub commands (e.g. **cat** , **sed** , etc.) that the BATS **assert** functions use internally. These mock/stub functions must be **unset** before these assert commands are run, or they will not work properly. Here is an example from **build.bats** that mocks **sed** , runs the **build_deployable** function, and unsets **sed** before running any assertions:
通常，没有必要在测试后复原桩/模拟功能，因为 **export**（输出）仅在当前 **@test** 块的 **exec**（执行）期间影响当前子进程。但是，可以模拟/桩 BATS **assert** 函数在内部使用的命令（例如**cat**，**sed**等）是可能的。在运行这些断言命令之前，必须对这些模拟/桩函数进行 **unset**（复原） ，否则它们将无法正常工作。下面是 **build.bats** 中的一个示例，该示例模拟 **sed**，运行 **build_deployable** 函数并在运行任何断言之前复原 **sed**：

```
@test ".build_deployable prints information, runs docker build on a modified Dockerfile.production and publish_image when its not a dry_run" {
  local expected_dockerfile='Dockerfile.production'
  local application='application'
  local environment='environment'
  local expected_original_base_image="${application}"
  local expected_candidate_image="${application}-candidate:${environment}"
  local expected_deployable_image="${application}:${environment}"
  source ${profile_script}
  mock_docker build --build-arg OAUTH_CLIENT_ID --build-arg OAUTH_REDIRECT --build-arg DDS_API_BASE_URL -t "${expected_deployable_image}" -
  function publish_image() { echo "publish_image ${*}"; }
  export -f publish_image
  function sed() {
    echo "sed ${*}" >&2;
    echo "FROM application-candidate:environment";
  }
  export -f sed
  run build_deployable "${application}" "${environment}"
  assert_success
  unset sed
  assert_output --regexp "sed.*${expected_dockerfile}"
  assert_output -p "Building ${expected_original_base_image} deployable ${expected_deployable_image} FROM ${expected_candidate_image}"
  assert_output -p "FROM ${expected_candidate_image} piped"
  assert_output -p "build --build-arg OAUTH_CLIENT_ID --build-arg OAUTH_REDIRECT --build-arg DDS_API_BASE_URL -t ${expected_deployable_image} -"
  assert_output -p "publish_image ${expected_deployable_image}"
}
```

Sometimes the same command, e.g. foo, will be invoked multiple times, with different arguments, in the same function being tested. These situations require the creation of a set of functions:
有的时候相同的命令，例如 `foo`，将在被测试的同一函数中使用不同的参数多次调用。 这些情况需要创建一组函数：

  * mock_foo: takes expected arguments as input, and persists these to a TMP file
  * foo: the mocked version of the command, which processes each call with the persisted list of expected arguments. This must be exported with export -f.
  * cleanup_foo: removes the TMP file, for use in teardown functions. This can test to ensure that a @test block was successful before removing.

  * mock_foo：将期望的参数作为输入，并将其持久化到 TMP 文件中
  * foo：命令的模拟版本，该命令使用持久化的预期参数列表处理每个调用。必须使用 `export -f` 将其导出。
  * cleanup_foo：删除 TMP 文件，用于拆卸函数。这可以进行测试以确保在删除之前成功完成 `@test` 块。

Since this functionality is often reused in different tests, it makes sense to create a helper library that can be loaded like other libraries.
由于此功能通常在不同的测试中重复使用，因此创建可以像其他库一样加载的帮助程序库会变得有意义。

A good example is **[docker_mock.bash][9]**. It is loaded into **build.bats** and used in any test block that tests a function that calls the Docker executable. A typical test block using **docker_mock** looks like:
**[docker_mock.bash][9]**是一个很棒的例子。它被加载到 **build.bats** 中，并在任何测试调用 Docker 可执行文件的函数的测试块中使用。使用 **docker_mock** 典型的测试块如下所示：

```
@test ".publish_image fails if docker push fails" {
  setup_publish
  local expected_image="image"
  local expected_publishable_image="${CI_REGISTRY_IMAGE}/${expected_image}"
  source ${profile_script}
  mock_docker tag "${expected_image}" "${expected_publishable_image}"
  mock_docker push "${expected_publishable_image}" and_fail
  run publish_image "${expected_image}"
  assert_failure
  assert_output -p "tagging ${expected_image} as ${expected_publishable_image}"
  assert_output -p "tag ${expected_image} ${expected_publishable_image}"
  assert_output -p "pushing image to gitlab registry"
  assert_output -p "push ${expected_publishable_image}"
}
```

This test sets up an expectation that Docker will be called twice with different arguments. With the second call to Docker failing, it runs the tested command, then tests the exit status and expected calls to Docker.
该测试建立了一个使用不同的参数两次调用 Docker 的预期。在对Docker 的第二次调用失败时，将运行测试命令，然后测试退出状态和对 Docker 调用的预期。

One aspect of BATS introduced by **mock_docker.bash** is the **${BATS_TMPDIR}** environment variable, which BATS sets at the beginning to allow tests and helpers to create and destroy TMP files in a standard location. The **mock_docker.bash** library will not delete its persisted mocks file if a test fails, but it will print where it is located so it can be viewed and deleted. You may need to periodically clean old mock files out of this directory.
一个方面 BATS 利用 **mock_docker.bash** 引入 **${BATS_TMPDIR}** 环境变量，BATS 在测试开始的位置对其进行了设置，以允许测试和助手程序在标准位置创建和销毁 TMP 文件。如果测试失败，**mock_docker.bash** 库将不会删除其持久化的模拟文件，但会在其所在位置进行打印，以便可以查看和删除它。您可能需要定期从该目录中清除旧的模拟文件。

One note of caution regarding mocking/stubbing: The **build.bats** test consciously violates a dictum of testing that states: [Don't mock what you don't own!][10] This dictum demands that calls to commands that the test's developer didn't write, like **docker** , **cat** , **sed** , etc., should be wrapped in their own libraries, which should be mocked in tests of scripts that use them. The wrapper libraries should then be tested without mocking the external commands.
请注意关于模拟/桩的警告：**build.bats** 测试有意识地违反了关于测试声明的规定：[不要模拟没有拥有的！][10]该规定要求调用开发人员没有编写代码的测试命令，例如 **docker**，**cat**，**sed**等，应封装在自己的库中，应在使用它们脚本的测试中对其进行模拟。然后应该在不模拟外部命令的情况下测试封装库。

This is good advice and ignoring it comes with a cost. If the Docker CLI API changes, the test scripts will not detect this change, resulting in a false positive that won't manifest until the tested **build.sh** script runs in a production setting with the new version of Docker. Test developers must decide how stringently they want to adhere to this standard, but they should understand the tradeoffs involved with their decision.
这是一个很好的建议，而忽略它是有代价的。如果 Docker CLI API 发生变化，则测试脚本将不会检测到此变化，从而导致一个错误内容直到经过测试的 **build.sh** 脚本在使用新版本 Docker 的生产环境中运行后才显示出来。测试开发人员必须确定要严格遵守此标准的程度，但是他们应该了解其所涉及的权衡。

### Conclusion
总结

Introducing a testing regime to any software development project creates a tradeoff between a) the increase in time and organization required to develop and maintain code and tests and b) the increased confidence developers have in the integrity of the application over its lifetime. Testing regimes may not be appropriate for all scripts and libraries.
在任何软件开发项目中引入测试方案都会在 a）增加开发和维护代码及测试所需的时间和组织与 b）增加开发人员在对应用程序整个生命周期中完整性的信心之间进行权衡。测试方案可能不适用于所有脚本和库。

In general, scripts and libraries that meet one or more of the following should be tested with BATS:
通常，满足以下一个或多个条件的脚本和库才可以使用 BATS 测试：

  * They are worthy of being stored in source control
  * They are used in critical processes and relied upon to run consistently for a long period of time
  * They need to be modified periodically to add/remove/modify their function
  * They are used by others
  * 值得存储在源代码管理中
  * 用于关键进程中，并可以长期稳定运行
  * 需要定期对其进行修改以添加/删除/修改其函数
  * 可以被其他人使用

Once the decision is made to apply a testing discipline to one or more Bash scripts or libraries, BATS provides the comprehensive testing features that are available in other software development environments.
一旦决定将测试规则应用于一个或多个 Bash 脚本或库，BATS 将提供其他软件开发环境中可用的全面测试功能。

Acknowledgment: I am indebted to [Darrin Mann][11] for introducing me to BATS testing.
致谢：感激[Darrin Mann][11]向我引荐了 BATS 测试。

--------------------------------------------------------------------------------

via: https://opensource.com/article/19/2/testing-bash-bats

作者：[Darin London][a]
选题：[lujun9972][b]
译者：[stevenzdg988](https://github.com/stevenzdg988)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://opensource.com/users/dmlond
[b]: https://github.com/lujun9972
[1]: https://github.com/sstephenson/bats
[2]: http://testanything.org/
[3]: https://git-scm.com/book/en/v2/Git-Tools-Submodules
[4]: https://github.com/dmlond/how_to_bats/blob/preBats/build.sh
[5]: https://github.com/dmlond/how_to_bats/blob/master/bin/build.sh
[6]: https://github.com/dmlond/how_to_bats/blob/master/test/build.bats
[7]: https://github.com/dmlond/how_to_bats/blob/master/test/helpers.bash
[8]: https://www.codewithjason.com/rspec-mocks-stubs-plain-english/
[9]: https://github.com/dmlond/how_to_bats/blob/master/test/docker_mock.bash
[10]: https://github.com/testdouble/contributing-tests/wiki/Don't-mock-what-you-don't-own
[11]: https://github.com/dmann
