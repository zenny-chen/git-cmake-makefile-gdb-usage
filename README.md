# Git, CMake, Makefile and GDB/LLDB Usage
Git、CMake、Makefile、GDB（LLDB）使用技巧

<br />

## Git命令一般使用

- [程序员学习道路第一条，学会Git,一学就会](https://www.toutiao.com/a6694015880218542606)
- [一篇文章，教你学会Git](https://www.toutiao.com/a6774284445873603083/)
- [Git超实用总结，再也不怕记忆力不好了](https://www.cnblogs.com/qcloud1001/p/9796750.html)
- [.gitignore 常用语法](https://blog.csdn.net/mengxin00100/article/details/122353917)
- [记一次git revert误操作找回](https://zhuanlan.zhihu.com/p/94922874)
- [git checkout切换到指定commit](https://blog.csdn.net/gtLBTNq9mr3/article/details/110729551)
- [怎么退出git bash编辑界面，怎么退出git log](https://blog.csdn.net/weixin_43290229/article/details/86094690)
- [Git取消跟踪文件和目录](https://blog.csdn.net/qq_38301914/article/details/70198006)
- [How To Rename a Local and Remote Git Branch](https://linuxize.com/post/how-to-rename-local-and-remote-git-branch/)
- git clone 一个项目并切换到指定分支：`git clone -b branch_name https://your_git_project.git`
- git递归拉取子项目：`git pull --recurse-submodules`
- 丢弃当前修改的本地文件：`git checkout -- filepathname`
- 丢弃上一次的提交：`git reset --hard origin/master`
- `git status`：先检查一下情况
- `git commit -a -m "xxx"`：-a表示所有修改过的文件都commit
- `git commit -m "xxx" 1.cpp 2.cpp`：指定commit哪几个文件
- git用指定的账号提交：`git commit "comment"  --author="John Doe <john@doe.org>"`
- 列出指定目录指定日期区间的所有提交，并以日期从老到新的次序排列，最后输出到指定文件：`git log  --reverse  --oneline  --since  ==2020-01-20  --until  ==2021-02-05  project/src/  >  /tmp/commit-log.txt`
- Linux中配置git的编辑器为系统自带的GEdit编辑器：`git config --global core.editor "gedit -s"`
- 追加或修改上一次提交的更多提交信息：`git commit --amend`，然后再执行push。
- Ubuntu 22.04 开始默认禁用了 **RSA** 加密算法。解决方法有2个：
1. 在客户端得ssh得config文件里加PubkeyAcceptedKeyTypes +ssh-rsa。如果要全局处理，就修改 **`/etc/ssh/ssh_config`** 文件，加上述内容。
1. 可以生成 key 的时候不用 rsa 算法，用 **`ed25519`** 或者别的支持的。比如：**`ssh-keygen -t ed25519 -P ""`**

- [Perforce使用教程](https://zhuanlan.zhihu.com/p/45167236)

<br/>

## VS Code 自带 Git 的使用步骤

1. Fetch From All Remotes
1. 如果有新的改动提交，则先 Merge 此提交，然后 Push 到自己分支。
1. 对于需要修改的文件，先添加 Stage Changes
1. Commit Staged
1. Push
1. 如果 Push 失败，Git 提示需要先 Pull，则先 Pull 一下。

<br/>

## GDB/LLDB的使用技巧

- [linux下生成core dump方法与gdb解析core dump文件](https://blog.csdn.net/weixin_39249306/article/details/94554782)
- [GDB调试教程：1小时玩转Linux gdb命令](http://c.biancheng.net/gdb/)
- GDB查看寄存器
```bash
info registers
info all-registers
info registers reggroup
info registers regname
```
- Linux下在GDB调试模式下忽略 **`SIGSEGV`** 信号，而直接让程序继续执行：
```bash
handle SIGSEGV nostop noprint
```
如果用的是LLDB，则用以下命令：
```bash
break set -n main -C "process handle --pass true --stop false SIGSEGV"
```
- [GDB and LLDB Command Examples](https://developer.apple.com/library/archive/documentation/IDEs/Conceptual/gdb_to_lldb_transition_guide/document/lldb-command-examples.html)
- [gdb到底是怎样实现的？](https://www.toutiao.com/a6699652803918299655)
- [调试程序时，设置断点的原理是什么？](https://www.toutiao.com/a6651660887507599886/)
- [gdb（debugger）加入软件断点的本质原理分析](https://www.toutiao.com/a6828945264800170504/)
- [调试引入的不确定性：必现的BUG神秘消失，断点改变代码执行逻辑](https://www.toutiao.com/article/6830405796770087431/)
- [Linux内核KGDB进阶：源码级调试实战演练](https://mp.weixin.qq.com/s?__biz=Mzg4NDQ0OTI4Ng==&mid=2247493582&idx=1&sn=f9a0110082b0c1547958ed9d2fe8d4b0)

<br/>

## CMake的常用用法集合

- [cmake 简介](https://www.cnblogs.com/lidabo/p/7359422.html)
- [CMAKE最全实战(1)](https://www.toutiao.com/i6858063275733713416/)
- [CMAKE最全实战(2)](https://www.toutiao.com/a6859561394904236547/)
- [Android NDK 开发之 CMake 必知必会](https://blog.csdn.net/zhying719/article/details/82657519)
- [【CMake 语法】(4) CMake 命令、命令参数、转义序列](https://blog.csdn.net/m0_57845572/article/details/118520228)
- Linux系统下安装CMake：
```shell
sudo sh cmake-<version>-linux-x86_64.sh  --prefix=/usr/local/  --exclude-subdir
```
- CMake命令行概述：[cmake(1)](https://cmake.org/cmake/help/latest/manual/cmake.1.html)  比如：
```cmake
# 这里所使用的 -j4 是指：
# 在cmake完成代码构建的生成之后， 在使用 make 命令时所指定的多线程个数
# --install-prefix 对应于 CMAKE_INSTALL_PREFIX
cmake -S src_dir -B build_dir --install-prefix install_dir -j4
```
- CMake指定安装目录：[CMAKE_INSTALL_PREFIX](https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html)（这里要注意的是，**`CMAKE_INSTALL_PREFIX`** 与 **`--install-prefix`** 必须指定为 **绝对路径**。）
- 判定CMake中某个符号是否没有被定义使用：`if(NOT DEFINED CMAKE_BUILD_TYPE)`。可参考：[Why if\(DEFINED <variable>\) doesn't work in cmake? \[duplicate\]](https://stackoverflow.com/questions/51621228/why-ifdefined-variable-doesnt-work-in-cmake)
- [If value not equal in cmake 2.8](https://stackoverflow.com/questions/11741325/if-value-not-equal-in-cmake-2-8)（使用`if(NOT <expression>)`时，里面的 **`NOT`** 必须是全大写）
- [if](https://cmake.org/cmake/help/latest/command/if.html)
- [string](https://cmake.org/cmake/help/latest/command/string.html)
- CMake **`string(TOUPPER <string1> <output variable>)`** 的使用：[CMake Regex to convert lower case to upper case](https://stackoverflow.com/questions/4905340/cmake-regex-to-convert-lower-case-to-upper-case)
- [\[CMake\] Return value of cmake string find](https://cmake.org/pipermail/cmake/2014-June/057778.html)
- [Back To Basics: CMake Functions and Macros](https://medium.com/@back_to_basics/cmake-functions-and-macros-22293041519f)
- CMake用于输出消息，即打印字符串：[message](https://cmake.org/cmake/help/latest/command/message.html)（其中，常用的模式有：**`STATUS`**、**`WARNING`** 和 **`FATAL_ERROR`**）
- CMake 使用系统环境变量：**`$ENV{SYSTEM_VAR_NAME}`**。比如：**`$ENV{CUDA_PATH}`**。
- [cmake构建时指定编译器架构(x86 or x64)](https://www.cnblogs.com/lidabo/p/12017014.html)
- [cmake命令行生成32位和64位项目](https://www.cnblogs.com/pandamohist/p/13644953.html)
- [Visual Studio 16 2019](https://cmake.org/cmake/help/latest/generator/Visual%20Studio%2016%202019.html)
- 用CMake生成 **Eclipse** C/C++项目工程：**`cmake -G "Eclipse CDT4 - Unix Makefiles" -DCMAKE_BUILD_TYPE=Debug ...`**。

关于上述命令中 **`Eclipse CDT4`** 的进一步描述：
```
When I worked in the CDT generator I wasn't (and still am not) familiar with the release cycle or the design constraints of the CDT, 
        hence the name includes CDT4 thinking it might not be compatible with the future versions. 

However, as another user points out people have successfully used it with CDT 5/6.

So, as long as the CDT doesn't break the xml format for external makefiles you should be able to use it.
```

- [CMAKE_ECLIPSE_VERSION](https://cmake.org/cmake/help/latest/variable/CMAKE_ECLIPSE_VERSION.html)
- [CMake error no CMAKE_C_COMPILER could be found using Xcode and GLFW](https://stackoverflow.com/questions/41380900/cmake-error-no-cmake-c-compiler-could-be-found-using-xcode-and-glfw)
- [CMake平台判断](https://blog.csdn.net/bianchengjingling22/article/details/88810593)
- [cmake_host_system_information](https://cmake.org/cmake/help/latest/command/cmake_host_system_information.html)（可用于判断当前系统名，比如 **Ubuntu**、**CentOS** 等）
- CMake判定当前是否使用的是MSVC编译器，使用 [MSVC](https://cmake.org/cmake/help/latest/variable/MSVC.html) 这一变量。比如：**`if(MSVC)`**。这里还包含了对 [MSVC_VERSION](https://cmake.org/cmake/help/latest/variable/MSVC_VERSION.html) 变量的介绍。
- [In CMake, how can I test if the compiler is Clang?](https://stackoverflow.com/questions/10046114/in-cmake-how-can-i-test-if-the-compiler-is-clang)
- [switching between gcc and clang-llvm using cmake](https://stackoverflow.com/questions/7031126/switching-between-gcc-and-clang-llvm-using-cmake)
- [如何使用CMake为单个目标编译具有不同选项的不同源文件？](https://www.javaroad.cn/questions/90941)
- CMake对当前使用哪种编译器的通用判定方法：[CMAKE_\<LANG\>_COMPILER_ID](https://cmake.org/cmake/help/latest/variable/CMAKE_LANG_COMPILER_ID.html)（这里的 **`<LANG>`** 可以是：[CMAKE_\<LANG\>_CLANG_TIDY](https://cmake.org/cmake/help/latest/variable/CMAKE_LANG_CLANG_TIDY.html)）。Google整理出来的当前CMake支持的 **`<LANG>`** 的列表：
> Supported languages include C , CXX (i.e. C++), CUDA , OBJC (i.e. Objective-C), OBJCXX , Fortran , HIP , ISPC , and ASM . By default C and CXX are enabled if no language options are given.
- [CMake ISPC](https://cmake.org/cmake/help/latest/envvar/ISPC.html)
- [CMAKE添加编译选项](https://blog.csdn.net/qinglongzhan/article/details/80743731)（汇编语言的编译选项的环境变量：`CMAKE_ASM_FLAGS`）
- [CMAKE_BUILD_TYPE](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html#variable:CMAKE_BUILD_TYPE)（Debug, Release, RelWithDebInfo and MinSizeRel）
- 使用 [CMAKE_CONFIGURATION_TYPES](https://cmake.org/cmake/help/latest/variable/CMAKE_CONFIGURATION_TYPES.html) 来配置 CMake 所生成的项目工程所包含的构建类型。比如：`-DCMAKE_CONFIGURATION_TYPES="Debug;Release;MinSizeRel;RelWithDebInfo"`。
- 编译选项针对不同构建类型的配置：`CMAKE_C_FLAGS_DEBUG`、`CMAKE_C_FLAGS_RELEASE`、`CMAKE_C_FLAGS_RELWITHDEBINFO`。
- [Using NASM with CMake and Clang](https://metricpanda.com/using-nasm-with-cmake-and-clang/)
- CMake允许使用指定的编程语言：**[enable_language](https://cmake.org/cmake/help/latest/command/enable_language.html)**
- CMake中开启汇编文件的编译：类Unix下使用GAS为 `enable_language(ASM)`；Visual Studio下使用MASM为 `enable_language(ASM_MASM)`；在Android Studio中使用为x86架构NASM，为：`enable_language(ASM_NASM)`。
- CMake在一个项目工程中同时指定当前项目支持C、C++和CUDA编译器（对于汇编语言的支持使用 **`enable_language()`**，而不在这里显式指定），可使用 **[project](https://cmake.org/cmake/help/latest/command/project.html)** 进行指定：
```cmake
project(project_name C CXX CUDA)
```
- 通过CMake环境变量设置C语言标准：[CMAKE_C_STANDARD](https://cmake.org/cmake/help/latest/variable/CMAKE_C_STANDARD.html)
- 通过CMake环境变量设置C++语言标准：[CMAKE_CXX_STANDARD](https://cmake.org/cmake/help/latest/variable/CMAKE_CXX_STANDARD.html)
比如：
```cmake
# 如果基于GCC等带有自身语法扩展的编译器，则默认会启用 -std=gnu11、-std=gnu++20 等
set(CMAKE_C_STANDARD  11)
set(CMAKE_CXX_STANDARD  20)
```
- **CMakeLists.txt** 文件中，[cmake_minimum_required](https://cmake.org/cmake/help/latest/command/cmake_minimum_required.html) 需要放在文件最开始，即倘若当前 **CMakeLists.txt** 文件包含了 **`project`** 语句，则需要放在该语句的上面；否则可能会引发CMake过程中的warning。
- 添加子目录的 cmake 项目：[**add_subdirectory**](https://cmake.org/cmake/help/latest/command/add_subdirectory.html)
- CMake添加带有字符串的宏定义： 
```cmake
ADD_COMPILE_DEFINITIONS(SOME_DIR="${CMAKE_INSTALL_PREFIX}")
```
或是
```cmake
ADD_COMPILE_DEFINITIONS(SOME_DIR=\"${CMAKE_INSTALL_PREFIX}\")
```
- CMake对外部提供可选项：[option](https://cmake.org/cmake/help/latest/command/option.html)
- CMake修改 **`CMAKE_CXX_FLAGS`** 等编译选项中的默认优化选项：[Optimize in CMake by default](https://9to5answer.com/optimize-in-cmake-by-default)（见 **Solution 3**）
- CMake通过设置CMake环境变量来为所有编译目标间接设置 **位置独立的代码**（**`-fPIC`** 的效果）[CMAKE_POSITION_INDEPENDENT_CODE](https://cmake.org/cmake/help/latest/variable/CMAKE_POSITION_INDEPENDENT_CODE.html)
- CMake 设置多处理器进行编译：[CMAKE_BUILD_PARALLEL_LEVEL](https://cmake.org/cmake/help/latest/envvar/CMAKE_BUILD_PARALLEL_LEVEL.html)
- [CMake target_compile_options](https://cmake.org/cmake/help/latest/command/target_compile_options.html)
- CMake设置GCC中的 **`-fvisibility=`**：[CMAKE_\<LANG\>_VISIBILITY_PRESET](https://cmake.org/cmake/help/latest/variable/CMAKE_LANG_VISIBILITY_PRESET.html)。比如：
```cmake
set(CMAKE_CXX_VISIBILITY_PRESET hidden)
set(CMAKE_C_VISIBILITY_PRESET default)
```
- 如果指向对某些指定的目标库做相关的可见性设置，可使用以下方式：
```cmake
set_target_properties(foo_library
                      PROPERTIES
                      C_VISIBILITY_PRESET    default
                      CXX_VISIBILITY_PRESET  hidden
                      CUDA_VISIBILITY_PRESET  hidden
                     )
```
- 基于CMake添加 **`-ldl`** （包含 **`dlopen`** 以及 **`dlclose`** 等动态加载符号的库）的变量： [CMAKE_DL_LIBS](https://cmake.org/cmake/help/latest/variable/CMAKE_DL_LIBS.html)（对该变量的具体使用可参考：[CMAKE_DL_LIBS](https://discourse.cmake.org/t/cmake-dl-libs/1159)）
- [include_directories](https://cmake.org/cmake/help/latest/command/include_directories.html)（该选项相当于编译选项：**`-I`**）
- [link_directories](https://cmake.org/cmake/help/latest/command/link_directories.html)（该选项相当于编译选项：**`-L`**）
- [link_libraries](https://cmake.org/cmake/help/latest/command/link_libraries.html)（为后续所有目标添加链接库，并可用于指定Debug或Release模式）
- [cmake:设置编译选项的讲究(add_compile_options和CMAKE_CXX_FLAGS的区别)](https://blog.csdn.net/10km/article/details/51731959)
- [cmake中链接系统标准库](https://blog.csdn.net/ly890700/article/details/72806033)
- [cmake引入第三方库](https://blog.csdn.net/yuegooxi/article/details/123706146)
- 引用并链接CMake自带的系统库模块（比如：[FindZLIB](https://cmake.org/cmake/help/latest/module/FindZLIB.html)）：
```cmake
find_package(ZLIB REQUIRED)
target_link_libraries(my_module_name  ZLIB::ZLIB)
```
- 要搜索 **`find_package`** 的路径变量需要使用：[CMAKE_MODULE_PATH](https://cmake.org/cmake/help/latest/variable/CMAKE_MODULE_PATH.html)
- [FindBoost](https://cmake.org/cmake/help/latest/module/FindBoost.html)（指定定制的boost库include路径使用 **`Boost_INCLUDE_DIR`**；指定定制的boost库的lib路径使用：**`Boost_LIBRARY_DIR_RELEASE`** 和 **`Boost_LIBRARY_DIR_DEBUG`**）
- [Boost library](https://cliutils.gitlab.io/modern-cmake/chapters/packages/Boost.html)（不使用CMake默认内置的FindBoost模块，而自己手动指定，可使用此CMake命令选项：**`-DBoost_NO_BOOST_CMAKE=ON`**）
- CMake中要包含其他用于CMake的文件或CMake模块：[include](https://cmake.org/cmake/help/latest/command/include.html)（比如：**`include(additional_config.cmake)`**）
- [How to statically link external library by target_link_libraries()?](https://discourse.cmake.org/t/how-to-statically-link-external-library-by-target-link-libraries/1718)
- 显式指定连接器使用哪种工具：[LINKER_LANGUAGE](https://cmake.org/cmake/help/latest/prop_tgt/LINKER_LANGUAGE.html)。比如在某些Linux系统中，C语言项目要连接含有C++标准库的一些动态链接库，可能需要使用 **`g++`** 或 **`clang++`** 工具链，而不是 **`gcc`** 或 **`clang`**。此时我们可以设置 **`LINKER_LANGUAGE`** 并最好再加上 **`libstdc++`** 的连接。比如：
```cmake
set(LINKER_LANGUAGE  CXX)
target_link_libraries(project_name  your_cpp_lib  stdc++)
```
- CMake中指定连接器选项可使用 [LINK_FLAGS](https://cmake.org/cmake/help/latest/prop_tgt/LINK_FLAGS.html) 这一 **`PROPERTY`**。比如：
```cmake
set_target_properties(target  PROPERTIES LINK_FLAGS  "-s")    # Linux GCC
set_target_properties(target  PROPERTIES LINK_FLAGS  "/OPT:ref  /OPT:ICF")    # Windows MSVC
```
- CMake对可执行文件目标设置连接器选项：[CMAKE_EXE_LINKER_FLAGS_\<CONFIG\>](https://cmake.org/cmake/help/latest/variable/CMAKE_EXE_LINKER_FLAGS_CONFIG.html)
```cmake
# Add '/DEBUG' option to all the build targets
set(CMAKE_EXE_LINKER_FLAGS  "${CMAKE_EXE_LINKER_FLAGS} /DEBUG")

# Add '-g' option only to DEBUG build target
set(CMAKE_EXE_LINKER_FLAGS_DEBUG  "${CMAKE_EXE_LINKER_FLAGS_DEBUG} -g")
```
- CMake对动态连接库目标设置连接器选项：[CMAKE_SHARED_LINKER_FLAGS_\<CONFIG\>](https://cmake.org/cmake/help/latest/variable/CMAKE_SHARED_LINKER_FLAGS_CONFIG.html)
```cmake
# Add '/DEBUG' option to all the build targets
set(CMAKE_SHARED_LINKER_FLAGS  "${CMAKE_SHARED_LINKER_FLAGS} /DEBUG")

# Add '-g' option only to DEBUG build target
set(CMAKE_SHARED_LINKER_FLAGS_DEBUG  "${CMAKE_SHARED_LINKER_FLAGS_DEBUG} -g")
```
- [Selecting Static or Shared Libraries](https://cmake.org/cmake/help/latest/guide/tutorial/Selecting%20Static%20or%20Shared%20Libraries.html)
- MSVC中设置运行时库类型（[/MD, /MT, /LD \(Use Run-Time Library\)](https://learn.microsoft.com/en-us/cpp/build/reference/md-mt-ld-use-run-time-library)）：[CMAKE_MSVC_RUNTIME_LIBRARY](https://cmake.org/cmake/help/latest/variable/CMAKE_MSVC_RUNTIME_LIBRARY.html)
- [cmake 中使用环境变量](https://www.cnblogs.com/stdpain/p/13467203.html)
- CMake给Visual Studio设置环境变量，使用`VS_DEBUGGER_ENVIRONMENT`。具体可参考：[Correct use of VS_DEBUGGER_WORKING_DIRECTORY etc.](http://cmake.3232098.n2.nabble.com/Correct-use-of-VS-DEBUGGER-WORKING-DIRECTORY-etc-td7599386.html)（其中，正确地设置`VS_DEBUGGER_ENVIRONMENT`变量的方式如下所示）
```cmake
set_target_properties(appName PROPERTIES VS_DEBUGGER_WORKING_DIRECTORY "PATH=${CMAKE_INSTALL_PREFIX}/bin;%PATH% \$(LocalDebuggerEnvironment)"
```
- [CMake INSTALL](https://cmake.org/cmake/help/latest/command/install.html)
- CMake为MSVC安装pdb调试文件到目标 **bin** 目录：
```cmake
install(FILES $<TARGET_PDB_FILE:project_name> DESTINATION bin)
```
- 在项目安装时，将指定文件重命名然后复制到指定目标路径：
```cmake
install(FILES ${MY_SRC_LIB}/file.txt  RENAME file.log  DESTINATION dst_dir)
```
- 用CMake来拷贝文件（[file\(COPY\)](https://cmake.org/cmake/help/latest/command/file.html#copy)）：
```cmake
file(COPY "${CMAKE_SOURCE_DIR}/some_dir/header.h" "${CMAKE_SOURCE_DIR}/another_dir/resource.res" DESTINATION "${CMAKE_BINARY_DIR}/dir")
```
- [file\(DOWNLOAD\)](https://cmake.org/cmake/help/latest/command/file.html#download)
- CMake修改项目最终生成文件名的前缀和后缀：`set_target_properties(project_name PROPERTIES PREFIX "prefix")`；`set_target_properties(project_name  PROPERTIES SUFFIX "suffix")`。比如，要把输出文件扩展名改为 **.suf**：`set_target_properties(project_name PROPERTIES SUFFIX ".suf")`。如果当前CMake项目是一个Linux上的动态链接库，并且我们想让生成 .so 文件不带有“lib”前缀，则可以：`set_target_properties(MySharedLib PROPERTIES PREFIX "")`，那么最后将会生成“MySharedLib.so”文件。
- [CMake execute_process](https://cmake.org/cmake/help/latest/command/execute_process.html)（比如：
```cmake
execute_process(COMMAND python "${PROJECT_SOURCE_DIR}/script.py" OUTPUT_VARIABLE output)
message(STATUS ${output})
）
```

- CMake将 **`.h.in`** 文件配置为正式的 **`.h`** 文件：[configure_file](https://cmake.org/cmake/help/latest/command/configure_file.html)

例如：有以下 **.h.in** 文件：
```c
#define MATERIALX_MAJOR_VERSION @MATERIALX_MAJOR_VERSION@
#define MATERIALX_MINOR_VERSION @MATERIALX_MINOR_VERSION@
#define MATERIALX_BUILD_VERSION @MATERIALX_BUILD_VERSION@
```
经过此 **CMakeLists.txt** 文件处理之后：
```cmake
set(MATERIALX_MAJOR_VERSION 1)
set(MATERIALX_MINOR_VERSION 38)
set(MATERIALX_BUILD_VERSION 7)

configure_file(${CMAKE_CURRENT_SOURCE_DIR}/Generated.h.in ${CMAKE_CURRENT_BINARY_DIR}/Generated.h)
```
最后生成以下 **.h** 文件：
```c
#define MATERIALX_MAJOR_VERSION 1
#define MATERIALX_MINOR_VERSION 38
#define MATERIALX_BUILD_VERSION 7
```

- [FindCUDAToolkit](https://cmake.org/cmake/help/latest/module/FindCUDAToolkit.html)（具体可以用：[**find_package**](https://cmake.org/cmake/help/latest/command/find_package.html#basic-signature)(**`CUDAToolKit`**)）
- [CMAKE_CUDA_RUNTIME_LIBRARY](https://cmake.org/cmake/help/latest/variable/CMAKE_CUDA_RUNTIME_LIBRARY.html)
- Link CUDA Driver API library: **`target_link_libraries(project_name `** [**CUDA::cuda_driver**](https://cmake.org/cmake/help/latest/module/FindCUDAToolkit.html#cuda-driver-library) **`)`**
- CMake中设置CUDA额外编译选项：`TARGET_COMPILE_OPTIONS(project_name PRIVATE $<$<COMPILE_LANGUAGE:CUDA>: --use_fast_math --gpu-architecture=sm35>)`
- CMake中启用CUDA单独编译（即relocatable device code，-rdc=true）：
```cmake
SET_TARGET_PROPERTIES(project_name PROPERTIES INTERFACE_LINK_LIBRARIES "" CUDA_SEPARABLE_COMPILATION ON)
```
- 为当前项目的CUDA设定所支持的架构：[CMAKE_CUDA_ARCHITECTURES](https://cmake.org/cmake/help/latest/variable/CMAKE_CUDA_ARCHITECTURES.html)。在设定 **`CMAKE_CUDA_ARCHITECTURES`** 时，必须将该命令放在当前项目根目录下的 **CMakeLists.txt** 文件中设置；或是通过CMake的环境变量传入；而不能放在子项目目录中 **CMakeLists.txt** 文件里设置。如果我们就设置一个架构，比如虚拟架构与实机架构都是75，那么我们可以直接使用：`set(CMAKE_CUDA_ARCHITECTURES  75)`。如果我们要设置多个架构可以这么写：`set(CMAKE_CUDA_ARCHITECTURES  "60;70;75")`。
- [CMAKE_CUDA_RUNTIME_LIBRARY](https://cmake.org/cmake/help/latest/variable/CMAKE_CUDA_RUNTIME_LIBRARY.html)
- CMake中调用其他进程获取相应字符串值：
```cmake
# This module determines which compute capability / SM version
# we should be compiling our CUDA code for, and adds the appropriate
# switch to the NVCC compiler flags - so that you don't have to worry
# about it.
#
# TODO: Be willing to take CUDA_CC, CUDA_TARGET_COMPUTE_CAPABILITY, 
# CUDA_TARGET_COMPUTE or CUDA_TARGET_COMPUTE_CAP and maybe even 
# those without the CUDA_ prefix

if (NOT CUDA_TARGET_COMPUTE_CAPABILITY)
        if("$ENV{CUDA_SM}" STREQUAL "")
                set(ENV{CUDA_INCLUDE_DIRS} "${CUDA_INCLUDE_DIRS}")
                set(ENV{CUDA_CUDART_LIBRARY} "${CUDA_CUDART_LIBRARY}")
                set(ENV{CMAKE_CXX_COMPILER} "${CMAKE_CXX_COMPILER}")
                execute_process(COMMAND bash -c "${CMAKE_CURRENT_SOURCE_DIR}/scripts/get_cuda_sm.sh"  OUTPUT_VARIABLE CUDA_TARGET_COMPUTE_CAPABILITY_) 
        else()
                set(CUDA_TARGET_COMPUTE_CAPABILITY_ $ENV{CUDA_SM})
        endif()

        set(CUDA_TARGET_COMPUTE_CAPABILITY "${CUDA_TARGET_COMPUTE_CAPABILITY_}" CACHE STRING "CUDA compute capability of the (first) CUDA device on the system, in XY format (like the X.Y format but no dot); see table of features and capabilities by capability X.Y value at https://en.wikipedia.org/wiki/CUDA#Version_features_and_specifications")

        execute_process(COMMAND bash -c "echo -n $(echo ${CUDA_TARGET_COMPUTE_CAPABILITY})" OUTPUT_VARIABLE CUDA_TARGET_COMPUTE_CAPABILITY) 
        execute_process(COMMAND bash -c "echo ${CUDA_TARGET_COMPUTE_CAPABILITY} | sed 's/^\\([0-9]\\)\\([0-9]\\)/\\1.\\2/;' | xargs echo -n" OUTPUT_VARIABLE FORMATTED_COMPUTE_CAPABILITY) 

        message(STATUS "CUDA device-side code will assume compute capability ${FORMATTED_COMPUTE_CAPABILITY}")
endif()

set(CUDA_GENCODE "arch=compute_${CUDA_TARGET_COMPUTE_CAPABILITY},code=\"sm_${CUDA_TARGET_COMPUTE_CAPABILITY},compute_${CUDA_TARGET_COMPUTE_CAPABILITY}\"")
```
- CMake 对项目文件进行分组：[source_group](https://cmake.org/cmake/help/latest/command/source_group.html)。比如：

```cmake
file(GLOB  kernel_header  "${CMAKE_SOURCE_DIR}/path/to/cuh_folder/*.cuh")
source_group("KERNEL"  FILES ${kernel_header})
add_library(lib_target  SHARED  ${kernel_header})
```

- CMake 中把某种文件类型指定为特定文件类型（比如把 **`.cuh`** 文件类型指定为标准 C++ 头文件类型）：需要通过 [set_source_files_properties](https://cmake.org/cmake/help/latest/command/set_source_files_properties.html) 对文件对象设置 [LANGUAGE](https://cmake.org/cmake/help/latest/prop_sf/LANGUAGE.html) 属性。比如：

```cmake
file(GLOB  kernel_header  "${CMAKE_SOURCE_DIR}/path/to/cuh_folder/*.cuh")
set_source_files_properties(${kernel_header}  PROPERTIES LANGUAGE CXX  HEADER_FILE_ONLY ON)
```

- [牛X！推荐一个腾讯开源的Markdown编辑器](https://www.toutiao.com/article/7387946688373096994/)

<br/>

### cmake 使用的一个例子

本例子基于：[oneTBB Installation from Sources](https://github.com/oneapi-src/oneTBB/blob/master/INSTALL.md)

```cmake
# Do our experiments in /tmp
cd /tmp
# Clone oneTBB repository
git clone https://github.com/oneapi-src/oneTBB.git
cd oneTBB
# Create binary directory for out-of-source build
mkdir build && cd build
# Configure: customize CMAKE_INSTALL_PREFIX and disable TBB_TEST to avoid tests build
cmake -DCMAKE_INSTALL_PREFIX=/tmp/my_installed_onetbb -DTBB_TEST=OFF ..
# Build
cmake --build .
# Install
cmake --install .
# Well done! Your installed oneTBB is in /tmp/my_installed_onetbb
```

<br/>

## cmake 创建一个 CUDA 项目

```cmake
cmake_minimum_required(VERSION  3.24.0)

set(CMAKE_MODULE_PATH  "${CMAKE_SOURCE_DIR}/cmake"  "${CMAKE_MODULE_PATH}")

find_package(CUDAToolKit  12.2  REQUIRED)

if(MSVC)
    if(NOT DEFINED OPENCL_INCLUDE_DIR)
        set(OPENCL_INCLUDE_DIR  "$ENV{CUDA_PATH}/include/")
    endif()

    if(NOT DEFINED OPENCL_LIBRARY)
        set(OPENCL_LIBRARY  "$ENV{CUDA_PATH}/lib/x64/OpenCL.lib")
    endif()

    add_definitions(-D_CRT_SECURE_NO_DEPRECATE)
    add_definitions(-D_CRT_SECURE_NO_WARNINGS)
else()
    add_compile_definitions(_GLIBCXX_USE_CXX11_ABI=0)
endif()

set(CMAKE_C_STANDARD  17)
set(CMAKE_CXX_STANDARD  20)

if(NOT DEFINED CMAKE_CUDA_ARCHITECTURES)
    set(CMAKE_CUDA_ARCHITECTURES  75)
endif()

include_directories(${OPENCL_INCLUDE_DIR})

if(CUDA_FOUND)
    link_libraries(${CUDA_LIBRARIES})
    include_directories(PRIVATE  ${CUDA_INCLUDE_DIRS})
else()
    message(FATAL_ERROR  "CUDA Tool Kit Not Found!")

file(GLOB  h_src    ${PROJ_DIR}/*.h*)
file(GLOB  c_src    ${PROJ_DIR}/*.c)
file(GLOB  cpp_src  ${PROJ_DIR}/*.cpp)
file(GLOB  cuda_h   ${PROJ_DIR}/*.cuh)
file(GLOB  cuda_src ${PROJ_DIR}/*.cu)

# Make .cuh headers as C++ headers
set_source_files_properties(${cuda_h}  PROPERTIES  LANGUAGE  CXX  HEADER_FILE_ONLY  ON)

source_group("header"  FILES  ${h_src})
source_group("cuda_header"  FILES  ${cuda_h})
source_group("src"  FILES  ${c_src}  ${cpp_src})
source_group("cuda_src"  FILES  ${cuda_src})

add_library(proj_name  SHARED  ${h_src} {c_src} {cpp_src} {cuda_h} {cuda_src})
set_target_properties(proj_name  PROPERTIES INTERFACE_LINK_LIBRARIES  ""  CUDA_SEPARABLE_COMPILATION  ON)

set(CUDA_COMPILE_OPTIONS  ${CUDA_COMPILE_OPTIONS}  -G  -g  --use_fast_math  --threads 0)

if(MSVC)
    set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS}  /Zi")
    set(CMAKE_SHARED_LINKER_FLAGS  "${CMAKE_SHARED_LINKER_FLAGS}  /DEBUG")
    set_target_properties(proj_name  PROPERTIES  LINK_FLAGS  "/OPT:ref  /OPT:ICF   /NODEFAULTLIB:LIBCMT")
else()
    set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS}  -g")

    # Modify the default `-O3` option to `-O2`
    string(REGEX  REPLACE  "([\\/\\-]O)3"  "\\12"  CMAKE_CXX_FLAGS_RELEASE  "${CMAKE_CXX_FLAGS_RELEASE}")

    set_target_properties(proj_name  PROPERTIES  LINK_FLAGS  "-s  -Wl,--exclude-libs,ALL")
endif()

if(CUDA_VERSION_MAJOR  GREATER_EQUAL  11)
    set(CUDA_COMPILE_OPTIONS  ${CUDA_COMPILE_OPTIONS}  --extended-lambda)
else()
    set(CUDA_COMPILE_OPTIONS  ${CUDA_COMPILE_OPTIONS}  --expt-extended-lambda)
endif()

target_compile_options(proj_name  PRIVATE  $<$<COMPILE_LANGUAGE:CUDA>: ${CUDA_COMPILE_OPTIONS}>)

target_link_libraries(proj_name  PRIVATE  CUDA::cudart  CUDA::cuda_driver)
```

<br/>

## makefile的常用用法集合

- [GNU Make in Detail for Beginners](https://opensourceforu.com/2012/06/gnu-make-in-detail-for-beginners/)
- [linux下的C语言开发（makefile编写详解）](https://www.toutiao.com/i6763898618379239950/)
- [全网最牛Linux内核Makefile文件详解](https://www.toutiao.com/i7034387758751678988/)
- [Makefile编译选项](http://blog.chinaunix.net/uid-24612247-id-176517.html)
- [Makefile编译时怎么打印出变量值](https://blog.csdn.net/zygblock/article/details/53330643)

