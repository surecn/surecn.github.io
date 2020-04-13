---
layout: post
title:  "Android CmakeLists.txt"
date:   2020-04-11 10:59:21 +0700
categories: android,音视频
---
1. 指定 cmake 的最小版本 
cmake_minimum_required(VERSION 3.4.1)

2. 设置编译类型
add_executable(demo demo.cpp) # 生成可执行文件
add_library(common STATIC util.cpp) # 生成静态库
add_library(common SHARED util.cpp) # 生成动态库或共享库

3. 查找库
find_library(VAR name path)查找到指定的预编译库，并将它的路径存储在变量中。

4. 设置 target 需要链接的库
target_link_libraries( # 目标库
                       demo
 
                       # 目标库需要链接的库
                       # log-lib 是上面 find_library 指定的变量名
                       ${log-lib} )

