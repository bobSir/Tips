# Tips

## 生成sshkey 
- 在终端中敲下面的命令，第一步会生成一堆私钥和公钥，分别存在~/.ssh/id_rsa和~/.ssh/id_rsa.pub中。第二部查看公钥字符串，
- ssh-keygen -t rsa -C "$your_email"  
- cat ~/.ssh/id_rsa.pub

## 上传已有工程到Git
- 进入工程目录 cd $project_name
- 初始化git仓库 git init
- 添加文件到仓库 git add .
- 提交代码到仓库 git commit -m "init commit"
- 链接到远程仓库 git remote add origin (远程仓库地址)
- push代码到服务器 git push -u origin master
- 添加远程仓库 git remote add upstream (远程地址)
- 克隆工程到本地 git clone (地址)
- git remote -v 查看远程仓库状态
- git fetch upstream 拉取远程仓库
- git merge upstream/master 合并代码
- git stash 将冲突暂存
- git stash pop 解决冲突
- git pull    拉取远程仓库
- git log 查看提交信息
- git checkout [$]切换分支
- git cherry-pick [$] 提交修改到另一个分支
- git push orgin 提交到orgin分支
- [Git命令表_链接](http://blog.csdn.net/ithomer/article/details/7529841)

## gradlew 命令
- ./gradlew -v 
- ./gradlew -clean  清除build文件
- ./gradlew -build 
- ./gradlew -assembleDebug 只打Debug包
- ./gradlew -installRelease
- ./gradlew -installDebug
- ./gradlew clean build --refresh-dependencies

- mac文件生效 source 	~/.bashrc

- 连接远程服务器 sudo su -  ssh -p 22 root@207.148.125.203
## 不透明表
透明度      | 值
---        | ---
100%       | 00
95%        | 0D
90%        | 1A
85%        | 26
80%        | 33
75%        | 40
70%        | 4D
65%        | 59
60%        | 66
55%        | 73
50%        | 80
45%        | 8C
40%        | 99
35%        | A6
30%        | B3
25%        | BF
20%        | CC
15%        | D9
10%        | E6
5%         | F2
0%         | FF
