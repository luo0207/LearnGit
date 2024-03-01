# LearnGit
## 将本地主机或者远程服务器与github进行ssh连接
[参考github官方教程](https://docs.github.com/zh/authentication/connecting-to-github-with-ssh/about-ssh)
**1、 在本地主机/ 远程服务器生成密钥对：id_rsa, id_rsa.pub**
*  在本地主机cmd命令提示符/远程服务器进行密钥生成：```ssh-keygen -t rsa -b 4096 -C "邮箱地址"```
*  在生成密钥时候可以不修改密钥存放位置直接进行第二步骤，如若修改了存放的位置，进行下一步
*  将新生成的密钥加入密钥管理
