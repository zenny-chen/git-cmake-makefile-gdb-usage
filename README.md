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

<br />

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

<br />

## CMake的常用用法集合

- [cmake 简介](https://www.cnblogs.com/lidabo/p/7359422.html)
- [CMAKE最全实战(1)](https://www.toutiao.com/i6858063275733713416/)
- [CMAKE最全实战(2)](https://www.toutiao.com/a6859561394904236547/)
- 判定CMake中某个符号是否没有被定义使用：`if(NOT DEFINED CMAKE_BUILD_TYPE)`。可参考：[Why if\(DEFINED <variable>\) doesn't work in cmake? \[duplicate\]](https://stackoverflow.com/questions/51621228/why-ifdefined-variable-doesnt-work-in-cmake)
- [If value not equal in cmake 2.8](https://stackoverflow.com/questions/11741325/if-value-not-equal-in-cmake-2-8)（使用`if(NOT <expression>)`时，里面的 **`NOT`** 必须是全大写）
- [cmake构建时指定编译器架构(x86 or x64)](https://www.cnblogs.com/lidabo/p/12017014.html)
- [CMake平台判断](https://blog.csdn.net/bianchengjingling22/article/details/88810593)
- [Android NDK 开发之 CMake 必知必会](https://blog.csdn.net/zhying719/article/details/82657519)
- [CMAKE添加编译选项](https://blog.csdn.net/qinglongzhan/article/details/80743731)（汇编语言的编译选项的环境变量：`CMAKE_ASM_FLAGS`）
- [CMAKE_BUILD_TYPE](https://cmake.org/cmake/help/latest/variable/CMAKE_BUILD_TYPE.html#variable:CMAKE_BUILD_TYPE)（Debug, Release, RelWithDebInfo and MinSizeRel）
- 编译选项针对不同构建类型的配置：`CMAKE_C_FLAGS_DEBUG`、`CMAKE_C_FLAGS_RELEASE`、`CMAKE_C_FLAGS_RELWITHDEBINFO`。
- [Using NASM with CMake and Clang](https://metricpanda.com/using-nasm-with-cmake-and-clang/)
- CMake中开启汇编文件的编译：类Unix下使用GAS为 `ENABLE_LANGUAGE(ASM)`；Visual Studio下使用MASM为 `ENABLE_LANGUAGE(ASM_MASM)`；在Android Studio中使用为x86架构NASM，为：`enable_language(ASM_NASM)`。
- [如何使用CMake为单个目标编译具有不同选项的不同源文件？](https://www.javaroad.cn/questions/90941)
- [cmake 中使用环境变量](https://www.cnblogs.com/stdpain/p/13467203.html)
- [MSVC_VERSION](https://cmake.org/cmake/help/latest/variable/MSVC_VERSION.html)
- CMake同时指定当前项目支持C、C++和CUDA编译器（对于汇编语言的支持使用 **`enable_language()`**，而不在这里显式指定）：
```cmake
PROJECT(project_name C CXX CUDA)
```
- CMake给Visual Studio设置环境变量，使用`VS_DEBUGGER_ENVIRONMENT`。具体可参考：[Correct use of VS_DEBUGGER_WORKING_DIRECTORY etc.](http://cmake.3232098.n2.nabble.com/Correct-use-of-VS-DEBUGGER-WORKING-DIRECTORY-etc-td7599386.html)（其中，正确地设置`VS_DEBUGGER_ENVIRONMENT`变量的方式如下所示）
```cmake
set_target_properties(appName PROPERTIES VS_DEBUGGER_WORKING_DIRECTORY "PATH=${CMAKE_INSTALL_PREFIX}/bin;%PATH% \$(LocalDebuggerEnvironment)"
```
- CMake为MSVC安装pdb调试文件：
```cmake
install(FILES $<TARGET_PDB_FILE:libname> DESTINATION bin)
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
- [CMAKE_DL_LIBS](https://cmake.org/cmake/help/latest/variable/CMAKE_DL_LIBS.html)
- [In CMake, how can I test if the compiler is Clang?](https://stackoverflow.com/questions/10046114/in-cmake-how-can-i-test-if-the-compiler-is-clang)
- [switching between gcc and clang-llvm using cmake](https://stackoverflow.com/questions/7031126/switching-between-gcc-and-clang-llvm-using-cmake)
- CMake添加带有字符串的宏定义： 
```cmake
ADD_COMPILE_DEFINITIONS(SOME_DIR="${CMAKE_INSTALL_PREFIX}")
```
或是
```cmake
ADD_COMPILE_DEFINITIONS(SOME_DIR=\"${CMAKE_INSTALL_PREFIX}\")
```
- [cmake:设置编译选项的讲究(add_compile_options和CMAKE_CXX_FLAGS的区别)](https://blog.csdn.net/10km/article/details/51731959)
- [cmake中链接系统标准库](https://blog.csdn.net/ly890700/article/details/72806033)
- [cmake引入第三方库](https://blog.csdn.net/yuegooxi/article/details/123706146)
- CMake修改项目最终生成文件名的前缀和后缀：`set_target_properties(project_name PROPERTIES PREFIX "prefix")`；`set_target_properties(project_name  PROPERTIES SUFFIX "suffix")`。比如，要把输出文件扩展名改为 **.suf**：`set_target_properties(project_name PROPERTIES SUFFIX ".suf")`。如果当前CMake项目是一个Linux上的动态链接库，并且我们想让生成 .so 文件不带有“lib”前缀，则可以：`set_target_properties(MySharedLib PROPERTIES PREFIX "")`，那么最后将会生成“MySharedLib.so”文件。
- 用CMake生成 **Eclipse** C/C++项目工程：`cmake -G"Eclipse CDT4 - Unix Makefiles" -DCMAKE_BUILD_TYPE=Debug ...`。
- [FindCUDAToolkit](https://cmake.org/cmake/help/latest/module/FindCUDAToolkit.html)
- [CMAKE_CUDA_RUNTIME_LIBRARY](https://cmake.org/cmake/help/latest/variable/CMAKE_CUDA_RUNTIME_LIBRARY.html)
- CMake中设置CUDA额外编译选项：`TARGET_COMPILE_OPTIONS(project_name PRIVATE $<$<COMPILE_LANGUAGE:CUDA>: --use_fast_math --gpu-architecture=sm35>)`
- CMake中启用CUDA单独编译（即relocatable device code，-rdc=true）：
```cmake
SET_TARGET_PROPERTIES(project_name PROPERTIES INTERFACE_LINK_LIBRARIES "" CUDA_SEPARABLE_COMPILATION ON)
```
- [CMAKE_CUDA_ARCHITECTURES](https://cmake.org/cmake/help/latest/variable/CMAKE_CUDA_ARCHITECTURES.html#variable:CMAKE_CUDA_ARCHITECTURES)
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

<br />

## makefile的常用用法集合

- [GNU Make in Detail for Beginners](https://opensourceforu.com/2012/06/gnu-make-in-detail-for-beginners/)
- [linux下的C语言开发（makefile编写详解）](https://www.toutiao.com/i6763898618379239950/)
- [全网最牛Linux内核Makefile文件详解](https://www.toutiao.com/i7034387758751678988/)
- [Makefile编译选项](http://blog.chinaunix.net/uid-24612247-id-176517.html)
- [Makefile编译时怎么打印出变量值](https://blog.csdn.net/zygblock/article/details/53330643)

