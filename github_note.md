# github

## git概述

* git是一个免费，开源的分布式版本控制系统

* 核心意义：团队中不同人对同一个决策发生冲突时，即使提醒共同商讨

### 版本控制工具

* 集中式
  
  * CVS、SVN、VSS

* 分布式
  
  * git、mercurial、bazaar、darcs。。。
  
  * 核心点：除了中央仓库保存变化，每一个开发者自己也保存一份
  
  * 优点：
    
    * 服务器断网也可开发
    
    * 每个客户端保存整个完整项目，包含历史记录，更安全

### 历史

* 1991 Linux本人合并代码

* 2002 收费的bitkeeper代管linux

* 2005 开发samba的Andrew试图破解bitkeeper，Linux用c语言两周写出git的主体程序，一个月后linux由git管理

* 2008年github上线

## git常用命令

* [git 常用命令大全（附命令注释）_git命令大全-CSDN博客](https://blog.csdn.net/2401_84164527/article/details/137486475)

### 设置用户签名

* git config --global user.name admin

* git config --global user.email admin@123.com

* git config --list # 查看全局配置

### 初始化

* git init

### 查看本地库

* git status  # 查看git状态

* git add 文件名 # 添加文件到git工作区

* git commit -m "日志信息" 文件名 # 提交文件，不加文件名，提交全部文件

* git reflog -n 数量 # 查看版本信息

* git log  # 查看版本详细信息

* git reset --hard 版本号 # 版本穿梭 ，多用于查看历史代码，尽量保持线性开发

### 底层逻辑

* 工作区(写代码) -- git add -->  暂存区（临时存储） -- git commit --> 本地库（历史版本）

## git gui

* 下载地址： [Git - GUI Clients](https://git-scm.com/download/gui/windows)



## git与idea

* java忽略模板 
  
  ```
  # Compiled class file
  *.class
  
  # Log file
  *.log
  
  # BlueJ files
  *.ctxt
  
  # Mobile Tools for Java (J2ME)
  .mtj.tmp/
  
  # Package Files #
  *.jar
  *.war
  *.nar
  *.ear
  *.zip
  *.tar.gz
  *.rar
  
  # virtual machine crash logs, see http://www.java.com/en/download/help/error_hotspot.xml
  hs_err_pid*
  replay_pid*
  ```

* 其他模板地址：[GitHub - github/gitignore: A collection of useful .gitignore templates](https://github.com/github/gitignore)

* 单分支冲突
  
  * 单个分支开发，往往会造成合并时出现冲突，需要多个版本和分支同时使用
