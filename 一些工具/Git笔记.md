- 课程出处：[尚硅谷Git入门到精通全套教程（涵盖GitHub\Gitee码云\GitLab）](https://www.bilibili.com/video/BV1vy4y1s7k6?p=2)
- 截图演示的远程库和代码操作在笔记记录完成后将被删除，只是起方便参考的作用
- [跳至文档最后](#EOF)

# 一、课程介绍

## 1. Git

- Git介绍：分布式版本控制工具（与集中式版本控制工具相对）
- Git安装
- Git命令
- **Git分支**：分支特性、分支创建、分支转换、分支合并（包括代码合并冲突的解决）
- IDEA集成Git

## 2. GitHub

  - （Git官方的代码托管中心，用来在服务器上存储代码）

  - 创建远程库
  - 代码推送：Push
  - 代码拉起：Pull
  - 代码克隆：Clone
  - SSH免密登录
  - IDEA集成GitHub

## 3. 码云Gitee：

  - 国内的类似GitHub的网站

  - 码云创建远程库
  - IDEA集成Gitee
  - 码云连接GitHub，进行代码的复制和迁移

## 4.GitLab：

- 基于局域网的代码托管中心，用于公司内部的代码管理

- GitLab服务器的搭建和部署
- IDEA集成GitLab



- Git与Maven同为项目管理工具



# 二、Git 概述

## 1.Git概述

- Git是一个免费开源的分布式版本控制系统，可以快速高效地处理从小型到大型额各种项目
- Git具有廉价的本地库（位于本地磁盘上）、方便的暂存区域和多个工作流分支等特性，其性能优于Subversion等版本控制工具

## 2.何为版本控制

- 版本控制时一种记录文件内容变化，以便将来查阅特定版本修订情况的系统
- 版本控制最重要的是可以记录文件修改历史记录，从而让用户能够查看历史版本，方便版本切换



## 3.为什么需要版本控制

- 个人开发过渡到团队协作



## 4.集中式版本控制工具

- CVS、SVN、VSS
- 集中化版本控制系统有一个单一的集中管理的服务器，保存所有文件的修订版本。所有人通过连接到该服务器，取出或提交文件
- 好处：每个人可在一定程度上看到项目中其他人的代码。管理员可以给每个开发者不同的权限，且只管理一个系统较方便
- 坏处：中央服务器的单点故障时，任何人在故障期间都无法提交更新，故无法协同工作



## 5.分布式版本控制工具

- Git、Mercurial、Bazzar、Darcs
- 分布式版本控制工具中，客户端提取的不是最新版本的文件快照，而是把代码仓库（包括历史记录）完整地镜像到本地库。这样，一个人的文件发生故障，可以用其他客户端的本地仓库进行恢复。
- 故分布式解决了集中式的缺陷：
	- 服务器（外部库）断网时也可以开发——版本控制是在本地进行的
	- 每个客户端都保存完整的项目，更加安全



## 6.Git工作机制

- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203081838373.png" alt="屏幕截图(11)" style="zoom:33%;" />
- 下面三个都是存放在本地磁盘上的不同目录中，而远程库位于互联网上



## 7.和代码托管中心

- 代码托管中心是基于网络服务器的远程代码仓库，一般称为远程库
- 局域网：GitLab
- 互联网：GitHub、Gitee码云



# 三、Git常用命令

## 1.设置（修改）用户签名

- `git config --global user.name 用户名`：设置用户签名
- `git config --global user.email 邮箱`：设置用户邮箱
- 签名的作用是区分不同操作者身份。用户的签名信息在每一个版本的提交信息中能看到，以此确认本次提交是谁做的。Git首次安装必须设置。
- 这个签名和用来登录GitHub等网站的账号没有任何关系
- 查看用户签名两种方式：
	- git中输入`cat ~/.gitconfig`
	- C盘当前用户文件夹打开`.gitconfig`文件



## 2.初始化本地库

- 作用是使git获取该目录的管理权
- 在相应目录（某目录右键`git bash here`）输入`git init`
- 之后会生成文件夹`.git`



## 3.查看本地库状态

- 代码：`git status`
- 初始化本地库后，查看状态，没有文件
- 在库中新建文件后，查看状态，显示：`untracked files`，文件被标红



## 4.添加暂存区

- 目的：使git追踪（track)某文件

- 代码：`git add 文件名`
- 添加后，查看状态，文件被标绿
- 也可以使用代码`git rm --cached 文件名`取消添加



## 5.提交本地库

- 目的：形成文件历史版本
- 代码：`git commit -m "版本信息" 文件名`
- 使用代码后，会提供7位版本号
- 使用`git reflog`查看简要版本信息
- 使用`git log`查看完整版本信息（可以看到完整的版本号和用户签名)



## 6.修改文件

- 修改文件后，查看状态，显示文件被修改，且被标红
- 对该文件进行添加和提交，查看版本信息：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203090830691.png" alt="image-20220309083056610" style="zoom:33%;" />
- `HEAD->main`指针指向最新版本



## 7.历史版本

- 基本语法：
	- `git reflog`：查看版本信息
	- `git log`：查看详细版本信息



## 8.版本穿梭

- 语法：`git reset --hard 版本号`
- 版本号可以是7位长的简化版本号
- 版本穿梭后，查看版本信息，可以看到`HEAD`指针指向过去版本<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203090841848.png" alt="image-20220309084157773" style="zoom:33%;" />
- git版本切换的原理：不是创建多个副本，而是创建多个日志信息，在切换时使`HEAD`指针指向特定的日志即可
- 另一种查看指针指向的方法：
	- 在`.git/HEAD`文件中确认当前分支，这里是`main`
	- 打开`.git/refs/heads`的`main`文件，里面即为当前指针指向的版本号



# 四、Git分支操作

## 1.分支介绍

- 在版本控制过程中，为了同时推进多个任务，可以为每个任务创建单独的分支
- 分支意味着程序员吧自己的工作从开发主线上分离开来，开发自己分支时，不会影响其他分支
- 分支底层也是指针引用 
- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203090855679.png" alt="image-20220309085517514" style="zoom:33%;" />
- `master`为程序主线分支，可以理解为用户正在使用的程序。两个`feature`是新的功能的分支，当功能开发完毕，就可以添加到主分支。同时，`hot-fix`（热修：紧急修复）也可以作为分支被创建，修复完成后，再添加到主分支



## 2.分支的好处

- 同时并行推进多个功能开发，提高开发效率
- 各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响



## 3.创建分支：

- 命令：`git branch 分支名`
- 创建分支时，该分支获得所有历史版本

## 4.查看分支

- 命令：`git branch -v`
- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203090905252.png" alt="image-20220309090538187" style="zoom:33%;" />
- `main`被标绿，表示`HEAD`指向`main`分支。同时`.git/refs/heads`中多出了`feature`文件



## 5.切换分支

- 命令：`git checkout 分支名`
- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203090908001.png" alt="image-20220309090807929" style="zoom:33%;" />
- `HEAD`指向`feature`分支（标为蓝色），同时`.git/HEAD`内容变为`feature`
- 在该分支内修改文件，不要忘了添加和提交：
- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203090914623.png" alt="image-20220309091438556" style="zoom:33%;" />
- 切换分支的本质是改变`HEAD`指针的指向。在不同分支下——例如`main`分支——切换版本，是改变`main`指针的指向



## 6.合并分支

- 命令：`git merge 分支名`：将某分支合并到当前分支
- 先切换到`main`分支，再使用该命令
- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203090918886.png" alt="image-20220309091825780" style="zoom:33%;" />



## 7.合并冲突

- 原因：两个分支对于同一个文件有两套不同的修改。Git无法替我们决定使用哪一个，必须认为决定新代码内容

- 合并后：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203090932401.png" alt="image-20220309093248329" style="zoom:33%;" />

- 不仅提示显示合并失败，标蓝的内容也多了`|merging`，表示合并没有完成

- 这时打开文件，会多出如下内容：

- ```
	内容1
	<<<<<<<<< HEAD
	内容2
	===========
	内容3
	>>>>>>>>>>> feature
	```

- 内容2为当前分支的部分文本，内容3位为`feature`分支的部分文本。应对它们进行处理，同时删除测试符号

- 修改文件后，查看状态：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203090938476.png" alt="image-20220309093826399" style="zoom:33%;" />

- 添加文件。在提交这一步，应输入`git commit -m "提交信息"`，后面不能加文件名，不然会报错<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203090946885.png" alt="image-20220309094652778" style="zoom:33%;" />





# 五、Git团队协作**机制**

## 1.团队内协作

- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091332231.png" alt="image-20220309133250082" style="zoom:33%;" />
- A（左边的人，作为远程库的创建者）先将自己的代码push到远程库
- B（右边的人）自己没有代码，他需要将远程库的代码clone（完整复制）到本地
- B对代码进行修改后，将新的代码push到远程库（两者需要在一个团队中，B才有权限push）
- 对于修改后的代码，A使用pull命令更新本地库



## 2.跨团队协作

- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091337591.png" alt="image-20220309133738418" style="zoom:33%;" />
- 目的：C（右一）帮助A和B修改代码，但两者不是一个团队
- fork的作用是复制对方的远程库，创建自己的相应的远程库
- C然后clone本地库，对代码进行修改，再push到自己的远程库
- C用自己的远程库发起pull request，由A审核。审核通过，A在远程库使用merge合并代码
- 之后，A和B这个团队使用pull将远程库新的代码更新到本地

# 六、GitHub操作

## 1.创建远程仓库

- 命名：一般，远程库和本地库的名字是一样的
- 选择`Public`，不需要初始化，点击创建



## 2.创建远程库别名

- 目的：为远程（库）地址（较长）建立较短的别名，方便以后操作
- `git remote -v`：查看当前所有远程地址别名
- `git remote add 别名 远程地址`：为该远程地址起别名。别名一般和本地库名称一致。
- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091402127.png" alt="image-20220309140249064" style="zoom:33%;" />



## 3.推送本地分支到远程库

- 语法：`git push 别名 分支`
- 最小的推送单位为分支
- 第一次推送会进行身份验证：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091410595.png" alt="image-20220309141002455" style="zoom: 25%;" />
- 然后提示推送成功：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091412562.png" alt="image-20220309141201478" style="zoom:33%;" />
- 远程库中可以看到该文件



## 4.拉取远程代码到本地库

- 目的：使本地库与远程库同步
- 命令：`git pull 别名 分支`
- 先在网页端更改`hello.text`，再使用pull
- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091434111.png" alt="image-20220309143415013" style="zoom:33%;" />



## 5.克隆远程仓库到本地

- 命令：`git clone 远程地址`
- 以下操作在虚拟机上完成
- 从GitHub上获得远程库的地址：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091444167.png" alt="image-20220309144419022" style="zoom: 25%;" />
- 输入命令后：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091448435.png" alt="image-20220309144830322" style="zoom:33%;" />
- 该命令的作用是：
	- 拉取代码
	- 初始化本地仓库
	- 创建别名（默认为`origin`）



## 6.邀请加入团队

- 虚拟机上想要push，会提示没有权限：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091512624.png" alt="image-20220309151210561" style="zoom:33%;" />
- 这时，需要主机（远程库创建者）邀请对方
- 主机在`git_test`中选择`settings - collaborators - manage access`中选择添加
- 对方需要打开邀请链接（这里是`www.github.com/el-nino2020/git_tests/invitations`，可见邀请链接具有一定格式），并同意
- 虚拟机之后就有push权限了





## 7.跨团队协作

- 虚拟机对主机的`git_test`远程库进行fork操作：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091531757.png" alt="屏幕截图(12)" style="zoom: 25%;" />
- 在自己的账号多出了一个远程库：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091533316.png" alt="屏幕截图(13)" style="zoom: 25%;" />
- 在远程库修改`hello.txt`后，发起pull request
- 主机看到有一个pull request：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091547514.png" alt="屏幕截图(14)" style="zoom: 25%;" />
- 进入该request，可以查看代码改动，也可以实时聊天：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091552711.png" alt="屏幕截图(15)" style="zoom: 25%;" />
- 之后点击`merge pull request`，再点击`confirm`即可同意该request



## 8.SSH免密登录

- 最初是没法使用这种方式的：<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091625004.png" alt="image-20220309162516934" style="zoom:25%;" />
- 在c盘当前用户文件夹打开git bash，输入`ssh-kegen -t rsa -C 描述信息`（`-t`表示加密类型），点击三次回车，创建`.ssh`文件夹，生成秘钥（每次都不一样，所以在这里展示也无所谓）
- <img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091621859.png" alt="image-20220309162149680" style="zoom: 25%;" />
- `id_rsa.pub`里即是公钥信息，在GitHub用户设置中`SSH and GPG keys`中新建SSH key，将信息复制进去
- 这时，可以用SSH克隆`git_test`库的数据了<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091631159.png" alt="image-20220309163151078" style="zoom:25%;" />
- 验证，使用SSH来pull，成功<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091634452.png" alt="image-20220309163410342" style="zoom:25%;" />
- 修改文件后，使用SSH来push，也成功<img src="https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202203091639554.png" alt="image-20220309163944466" style="zoom:25%;" />
- 免密登录对于Ubuntu使用git来说至关重要，因为每次使用push都要输入用户名和一个私有令牌



# 七、IDEA集成Git



## 1.配置Git忽略文件

- 在c盘用户目录下创建`git.ignore`文件，以对所有Git项目进行忽略
- 这个不用，还是在每一个Git目录下配置`.gitignore`比较合理





## 2. IDEA设置

- `settings` - `Versions control` - `git`中配置`git.exe`的全路径



## 3. 初始化本地库

- `VCS`——`import into version control `——`create git repository`

## 4.相关操作

- add、commit都可以右键执行

## 5. 切换版本

- 左下角点`Git`——`log`
- 在想要回退的版本上右键`checkout revision "版本号"`

## 6.创建分支

- 项目目录上右键`git`——`repository`——`branches`，或者右下角点击当前分支名字。再点击`new branch`

## 7.切换分支

- 点击分支名，点`checkout`

## 8. 合并分支（正常合并）

- 先在`hot-fix`分支中添加一条代码，提交
- 切换回`main`分支，点击`hotfix`——`merge into current`

## 9. 合并分支（合并冲突）

- 在两个分支中各写一条代码（两者会冲突），提交
- 切换回`main`分支，点击`hotfix`——`merge into current`
- 弹出提示框，显示冲突，点击`merge`
- 出现3个代码框，左边的是当前分支代码，中间的是没有冲突的代码（用作显示合并的结果），右边的是另一条分支的代码
- `×`表示不合并，`>>`表示插入这条代码



# 八、IDEA集成GitHub

## 1.设置github账号

- `settings` - `Versions control` 中应该有`github`，如果没有，在`plugins`（插件）中下载
- 点击`+`号，可以用账号登录，也可以用token（github 设置中developer settings中）

## 2. 分享项目到github

- 选择`VCS` ——`import into version control `——`share project on github`
- 这一步相当于在github上手动创建一个库，并把当前项目push上去

## 3.将代码push到远程库

- 点击`Git`——`push`
- 默认使用HTTPS的链接来push，会受制于网络情况
- 由于用token登录，也可以使用ssh链接：获取到远程库的ssh链接后，点击当前远程链接的别名，比如`main`，点击`define remote`，即可进行配置
- push是将本地库代码推送到远程库，如果两者的代码版本不一致，push的操作会被拒绝。即，如果要push成功，本地库代码版本需要比远程库的高。因此，在**改本地库的代码之前，要先检查远程库和本地库的版本的区别。**如果本地库版本落后，就先pull

## 4. pull远程库

- 点击`Git`——`pull`
- pull是拉取远程库代码到本地，如果两者代码不一致，会自动合并。合并失败，会要求手动解决冲突，比较麻烦，**应避免**

## 5. clone远程库到本地

- 打开一个新的IDEA窗口，选择`get from version control`，将远程库的clone链接放入`url`一栏



# 九、码云

## 1.介绍

- 基于Git的一个代码托管中心。**国内**公司，因此国内访问不会出现网络问题。
- 能用GitHub就不要用码云了，因为码云的界面几乎和github一样，只不过是中文的

## 2.IDEA集成码云

- 需要在`settings`——`plugins`中下载`gitee`插件，因为默认没有
- 用法和`github`插件一样

## 3. 码云复制github远程库

- 在创建远程库中，只填写导入已有仓库，使用github中某个远程库的http地址
- 这相当于复制了一份github远程库的代码
- 如果要同步，点击这个按钮即可：
- ![image-20220417102205584](https://cdn.jsdelivr.net/gh/el-nino2020/ImageBed/202204171022747.png)

# EOF

[返回顶部](#一、课程介绍)















