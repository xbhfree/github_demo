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

# gitlab

## 基础

* 官网：
  
  * https://about.gitlab.com/
  
  * https://gitlab.cn/

* 功能：
  
  * 源代码托管
    
    * 安全审计
    
    * 代码推送规则
  
  * CI/CD 部署运维
    
    * 流水线部署
    
    * 多流水线，多场景
  
  * 效能管理
  
  * 敏捷项目管理
  
  * DevSecOps 开发运维一体化
  
  * 云原生

## 安装部署

### 安装准备（以debain为例）

* 开启ssh
  
  * ```shell
    sudo systemctl status sshd
    sudo systemctl enable sshd
    sudo systemctl start sshd
    ```

* 防火墙开启http\https
  
  * ```shell
    # 开启ssh防火墙端口
    sudo ufw allow 22/tcp
    #开启http端口
    sudo ufw allow 80/tcp
    #开启https端口
    sudo ufw allow 443/tcp
    sudo ufw enable
    ```

### 安装步骤（以kali linux为示例）

* sudo apt-update
  sudo apt-upgrade
  sudo apt-get install -y curl openssh-server ca-certificates

* curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh | sudo bash
  sudo EXTERNAL_URL="http://kali.gitlab" apt-get install gitlab-ee

* 国内版本：curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash
  `sudo EXTERNAL_URL="http://debain.gitlab" apt-get install gitlab-ce`

* sudo vim /etc/gitlab/gitlab.rb

* 修改配置文件
  
  * external_url "http://虚拟机IP地址:9696"

* sudo gitlab-ctl reconfigure

* sudo gitlab-ctl restart

### gitlab使用

* 管理员账号密码
  
  * 账号：root
  
  * 密码： cat /etc/gitlab/initial_root_password  4smlozNtggohkbBGbZgANlcAiUq5jzqKo7LZr/ZVNts=
  
  * admin area -> Overview -> Users 可以修改密码

* 修改时间
  
  * 用户偏好 -> 取消使用相对时间，就可以用具体的时间

* 群组权限
  
  * owner：所有者，创建组的人员，可以开除管理员，但管理员无法操纵owner角色
  
  * maintainer：管理员，具备sudo的用户，一般给小组长或者产品经理
  
  * developer：干活的人，只能在自己组里面上传下载代码
  
  * repoter：只能看，不能改，一般给其他组的人，或者大牛
  
  * guest：匿名用户，相当于被删除了

## idea连接gitlab

### 准备工作

* 安装gitlab projects插件

* versionControl中就会有gilab选项

* 添加gitlab用户

* gitlab中需要先创建自己的令牌

* 将gitlab url、令牌输入，选择ssh的连接方式

* gitlab中配置自己的密钥

* 设置-》仓库-》初始默认分支修改为初始推送后完全保护，之后只能合并到master方式来推送代码
