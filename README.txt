[github技术]git/github 使用
浏览：1265 |更新：2013-04-18 18:49
1. git 版本控制系统

相比CVS\SVN优势：

－ 支持离线开发，离线Repository

－ 强大的分支功能，适合多个独立开发者协作

－ 速度块

ps:关于git的更详细的介绍于优点在此就不介绍了，教大家怎么用是关键。:）

==============运行环境========

系统：windows

git : Git-1.7.3.1-preview20101002.rar  下载地址：http://d.download.csdn.net/down/3169511/z_y_liu89

===========================

2. github是一个git项目托管网站

注册地址：https://github.com/signup/free

3. 安装git程序，执行下面操作

$ cd ~/.ssh    //检查计算机ssh密钥

如果没有提示:No such file or directory 说明你不是第一次使用git,执行下面的操作,清理原有ssh密钥

$ ls

config id_rsa id_rsa.pub known_hosts

$ mkdir key_backup

$ cp id_rsa* key_backup

$ rm id_rsa*

获得密钥：

ssh-keygen -t rsa -C "defnngj@gmail.com"//填写email地址，然后一直“回车”ok

打开本地..\.ssh\id_rsa.pub文件。此文件里面内容为刚才生成人密钥。

4. 登陆github系统。点击右上角的 Account Settings--->SSH Public keys ---> add another public keys

把你本地生成的密钥复制到里面（key文本框中）， 点击 add key 就ok了

5. 接着打开git ，测试连接是否成功

$ ssh -T git@github.com

如果提示：Hi defnngj You've successfully authenticated, but GitHub does not provide shell access. 说明你连接成功了

6. 设置用户信息：

6.1

$ git config --global user.name "defnngj"//给自己起个用户名

$ git config --global user.email  "defnngj@gmail.com"//填写自己的邮箱

6.2

在github中找到 Account Settings--->Account Admin ,找到一下信息：

Your API token is e97279836f0d415a3954c1193dba522f ---keep it secret! Changing your password will

generate a new token

$ git config --global github.user defnngj      //github 上的用户名

$ git config --global github.token e97279836f0d415a3954c1193dba522f

====================创建一个项目========================

1. 回到github首页，点击页面右下角“New Repository”

填写项目信息：

project name: hello world

description : my first project

点击“Create Repository” ； 现在完成了一个项目在github上的创建。

2. 我们需要使用git在本地创建一个相同的项目。

$ makdir ~/hello-world    //创建一个项目hello-world

$ cd ~/hello-world    //打开这个项目

$ git init    //初始化

$ touch README

$ git add README   //更新README文件

$ git commit -m 'first commit'//提交更新，并注释信息“first commit”

$ git remote add origin git@github.com:defnngj/hello-world.git   //连接远程github项目  

$ git push -u origin master   //将本地项目更新到github项目上去

现在查看github上面的hello world 项目，是不是发现已经将本地中的README文件更新上来了。 :) 恭喜！

------------------------------------关于可能出现的错误----------------------------------

1.在执行

$ git remote addorigin git@github.com:defnngj/hello-world.git

错误提示：fatal: remote origin already exists.

解决办法：

$ git remote rm origin

然后在执行：$ git remote add origin git@github.com:defnngj/hello-world.git 就不会报错误了

2. 在执行

$ git push origin master

错误提示：error:failed to push som refs to.......

解决办法：

$ git pull origin master //先把远程服务器github上面的文件拉先来，再push 上去。

---------------------------后记-----------------------------------------------------------------------

本文是参考官方帮助进行的：http://help.github.com/win-set-up-git/ 基本与官方步骤相同，我在此属于翻译了一下！

关于更过的学习：请登陆: http://progit.org/book/zh/进行学习。

本来关于此类知识应该属于开发的，本人从事测试工作，因为老大现在在推行git的使用，所以，就花了时间，初步的学习了一下，为了更好的测试嘛。呵呵。

第二个原因，看到有个乐师用版本管理系统（SVN）来更新和管理自己的乐谱，这个很有意思。版本管理系统并不局限于代码的管理。而且版本管理系统的思想也很有意思。