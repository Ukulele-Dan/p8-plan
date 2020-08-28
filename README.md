# p8 plan

#### 介绍

This repo can be regarded as a collection of coding, wiki, and some other stuff in the process of learning advanced technologies required by a senior developer.

#### 软件架构

软件架构说明

#### 安装教程

#### 使用说明

1. docker相关命令行

```bash
# 构建基础镜像
$ ./build.sh image base
# 构建app镜像（wbh/p8:v1）并创建容器
$ ./build.sh app && ./build.sh container

# 解决jinfo, jmap等命令遇到的Operation not permitted问题（以extended权限登陆容器）
$ docker exec --privileged -it p8_server bash
```

2.常用命令行

```bash
# 运行某个Java类（https://docs.spring.io/spring-boot/docs/current/reference/html/appendix-executable-jar-format.html）
$ java -cp app.jar -D"loader.main=com.hucat.jvm.gc.Demo" org.springframework.boot.loader.PropertiesLauncher
# 测试GC回收样例程序
$ java -Xms20M -Xmx20M -XX:+PrintGC -cp app.jar -D"loader.main=com.hucat.jvm.gc.T15FullGCProblem01" org.springframework.boot.loader.PropertiesLauncher
# 查看java进程的内存设置情况
$ jps -v
# 查看jvm的map信息
$ jmap $(jps |grep app.jar |awk '{print $1}')
$ jmap -heap $(jps |grep app.jar |awk '{print $1}')
# 查看jvm的基本信息
$ jinfo $(jps |grep app.jar |awk '{print $1}')
# jvm统计工具
$ jstat -options
$ jstat -gc $(jps |grep app.jar |awk '{print $1}') 1000
$ jstat -gcutil $(jps |grep app.jar |awk '{print $1}') 1000
$ jstat -compiler/class/printcompilation $(jps |grep app.jar |awk '{print $1}')
```

3.Useful command line

```bash
# Delete all configure files generated by vscode extention -- Java Extention Pack
$ find . -type d -regex '.*/.settings' -exec rm -r {} +
$ find . -type d -not -regex '\./\.git.*' -and -regex '.*/logs' -exec rm -r {} +
$ find . -type d -name bin -exec rm -r {} +
$ find . -type f -name .project -exec rm -r {} +
$ find . -type f -name .classpath -exec rm -r {} +
# Single command integrating all commands above
$ find . -type d -regex '.*/.settings' -exec rm -r {} + && find . -type d -not -regex '\./\.git.*' -and -regex '.*/logs' -exec rm -r {} + && find . -type d -name bin -exec rm -r {} + && find . -type f -name .project -exec rm -r {} + && find . -type f -name .classpath -exec rm -r {} +
# Regenerate configure files of Java Extention Pack after cleaning them.
cmd + shift + p --> clean the java language server workspace
```

#### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request


#### 码云特技

1.  使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2.  码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3.  你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4.  [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5.  码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6.  码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)
