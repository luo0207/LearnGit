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