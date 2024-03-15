# LearnGit
## 在本地主机或服务器端设置git用户名以及邮箱
* 设置用户名```git config --global user.name "luo0207"```
* 设置用户邮箱 ```git config --global user.email "1272773750@qq.com"```
* 设置输出的彩色格式使得输出更可读 ```git config --global color.ui auto```
* 查看git设置后的config的信息```git config --list```

![image](https://github.com/luo0207/LearnGit/assets/104191820/8c2bf26c-4667-457e-b278-ee0de3e6c643)


## 将本地主机或者远程服务器与github进行ssh连接
[参考github官方教程](https://docs.github.com/zh/authentication/connecting-to-github-with-ssh/about-ssh)

**1、 在本地主机/ 远程服务器生成密钥对：id_rsa, id_rsa.pub**
*  在本地主机cmd命令提示符/远程服务器进行密钥生成：```ssh-keygen -t rsa -b 4096 -C "邮箱地址"```
*  在生成密钥时候可以不修改密钥存放位置直接进行第二步骤，如若修改了存放的位置，进行下一步
*  将新生成的密钥加入密钥管理, 即为将 SSH 密钥添加到 ssh-agent，首先启动ssh后台代理```eval "$(ssh-agent -s)"```。注意, 根据您的环境，您可能需要使用不同的命令。 例如，在启动 ssh-agent 之前，你可能需要通过运行 ```sudo -s -H ```根访问，或者可能需要使用 ```exec ssh-agent bash``` 或``` exec ssh-agent zsh ```运行 ```ssh-agent```。
  运行成功后如下图：

 ![image](https://github.com/luo0207/LearnGit/assets/104191820/cfb04ad4-311b-4cf8-9611-fffc6f41c901)
*  将新生成的密钥加入管理：```ssh-add /home/luoyawen/.ssh/git/id_rsa```

**2、将本地生成的ssh密钥添加至github的ssh处**
* 查看公钥内容: ```cat /home/luoyawen/.ssh/git/id_rsa.pub```并将其添加至github账号中的ssh连接处中去
* 检查本地/服务器是否可以连接至github账号中去：```ssh -T git@github.com``` 如果成功连接，则显示如下图：
  
 ![image](https://github.com/luo0207/LearnGit/assets/104191820/e446a940-e3dd-473f-b71e-63a4717431f8)


## 常用命令及操作
* ```git clone + https/ssh``` 可将github上的代码拷贝到本地
* ```git status``` 查询仓库状态
  一般的状态有： Changes not staged for commit  没有保存的变化
                Untracked files  新添加的没有被git管理的文件
* ```git add``` 将文件添加至暂存区
* ```git commit -m + "修改说明"``` 提交新添加的文件，将暂存区的文件实际保存在仓库的历史记录中。该操作可记录当前工作树中所有文件的当前状态。
**如果想注释写的更详细一些 可以直接写入git commit**  会弹出记事本来记录注释
笔记本记录的格式为： 第一行为提交的更改内容， 第二行是空行， 第三行是原因
写好后```ctrl + x```退出, 文件已经被commit。
**在写记事本的时候想中止提交，只需删除记事本所有内容再```ctrl x```退出， 选择不保存no**

* ```git push``` 服务器上的文件会更新
* ```git log``` 显示文件提交的记录， 如果只需要显示简洁版本 加入```--pretty=short```的参数即可。 **按下q即可退出其实简洁模式只是少了日期** 
* ```git log + 文件名``` 只显示对应文件的改变
* ```git diff``` 可以用于查看工作树、暂存区、最新提交之间的差别
* ```git diff```一般用于观察工作树和暂存区之间的区别
* ```git diff HEAD``` 用于观察工作树和最新提交之间的差别
```
diff --git a/README.md b/README.md  # 变动前的a和变动后的b的差别
index cc44f64..1ff06b0 100644  # 俩个文件的哈希值
--- a/README.md  # -号代表变动前的文件
+++ b/README.md  # +号代表变动后的文件
@@ -37,4 +37,9 @@  # - 变动前的文件，从第37行开始，连续变4行  + 变动后的文件37行开始连续9行， 下面是变动的具体内容
 **如果想注释写的更详细一些 可以直接写入git commit**  会弹出记事本来记录注释   
 笔记本记录的格式为： 第一行为提交的更改内容， 第二行是空行， 第三行是原因
 写好后```ctrl + x```退出, 文件已经被commit。
-* ```git push``` 服务器上的文件会更新
\ No newline at end of file
+**在写记事本的时候想中止提交，只需删除记事本所有内容再```ctrl x```退出， 选择不保存no**
+
+* ```git push``` 服务器上的文件会更新
+* ```git log``` 显示文件提交的记录， 如果只需要显示简洁版本 加入```--pretty=short```的参数即可。 **按下q即可退出其实简洁模式只是少了日期**
+* ```git log + 文件名``` 只显示对应文件的改变
+* ```git diff``` 可以用于查看工作树、暂存区、最新提交之间的差别  
\ No newline at end of file
```

## 分支操作
* ```git branch```  可以确定目前所在的分支以及目前的分支名列表
* ```git checkout -b + 分支名称```   等价于先创建分支```git branch + 分支名称```  再切换到对应分支 ```git checkout + 分支名称```  **在切换分支之前要确保这条分支的内容已经add并且commit了 不然会丢失修改的内容, 本地的文件会被切换的分支的内容覆盖**

> 在开发中创建分支的优点在于子分支的更改不会影响到其余分支，这样可以进行多个子功能的并行开发并且不会影响到其余分支

> 基于特定功能的开发在特性分支中进行，主题完成后在和主分支合并，遵循该开发流程，就可以保证主分支可以随时供人查看。
* ```git merge``` 合并分支，首先切换到要合并到的分支, 比如 ```git checkout ```
* ```git merge --no-ff + 合并的分支名称```
* ```git log --graph``` 可以以图表的形式输出提交日志

## 回溯操作
* ```git reset```可以对当前的状态进行回溯，回到之前的状态，只需要哈希值
* ```git log```往往只可以得到截至当前的记录，如果想看到之前的记录，则需要进行```git reflog```
* ```git commit -am + 文件名```添加并commit当前文件
* ```git commit -amend```可以修改上次提交的文件名称
* ```git rebase -i HEAD~2``` 