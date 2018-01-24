# 日常使用手册
## 一、基本概念
### 1. 工作空间
用户操作，添加1.txt文件
### 2. 缓存区
从工作空间添加1.txt：`git add 1.txt`\
撤销修改:`git checkout 1.txt`\
本地库覆盖工作空间：`git checkout head`

### 3. 本地库
将缓存区内容添加到本地库：`git commit –m “comment”`
### 4. 远程库
* 下载远程库：`git clone https://github.com/dandanlinpu/test.git`
* 查看关联的远程库：`git remote -v`
>默认git clone后远程库名字为origin
* 提交分支：`git push 远程主机名 本地分支：远程分支`
* 获取和合并分支：`git pull 远程主机名 本地分支：远程分支`
>分支名字一样时可以只写一个,如：\
>git push origin master\
>git pull origin master
* 获取分支：`git fetch 远程主机名 远程分支`
* 在当前分支上合并获取的分支:`git merge 待合并至当前分支名`
>例:\
>git fetch origin master\
>在本地引用此fetch的分支时使用origin\\master \
>git merge origin\\master\ 或者 git merge dev

>git pull = git fetch + git merge
## 二、日常使用
### 1. 首次安装git配置
配置软件显示中文不乱码：
options->Default File Contents Encoding，change为UTF-8

配置用户名和邮箱：
`git config –global user.email 邮箱`\
`git config –global user.name 姓名`

配置连接github公钥：
本地生成公钥，在git bash中： ssh-keygen -t rsa,将生成的公钥文件id_rsa内容添置github网站对应位置
### 2. 已有远程库
先进行下载：git clone https://github.com/dandanlinpu/test.git
### 3. 已有本地库
要上传到github?
### 4. 要将本地库和远程库联系起来
git remote add 自己起的主机名 远程库地址,如git remote add test https://github.com/dandanlinpu/test.git
### 5. 状态
`git status`
### 6. 分支管理
* 查看远程分支 `git branch –r `
* 查看所有分支 `git branch –a` 
* 创建`git branch dev`
* 切换`git checkout dev`
* 等同于`git checkout –b dev `
* 分支合并 `git merge `
### 7. push失败处理
本地库master: 1->2->3\
远程master:1->2->4(不同于3的修改，比如其他人在2基础上提交的修改)\
在本地push master分支 git push origin master,会失败：：
failed to push some refs … updates were rejected because the remote contains work that you do not have locally.\
>处理方法：获取远程库到本地，在本地处理merge冲突,再push
1. 先fetch：git fetch origin master
2. 然后merge:git merge origin/master
3. 提示冲突，然后打开本地文件，本地文件已被自动修改，提示了冲突的位置和原因，一一修改。
4. 更新本地库： git add、 git commit
5. push到远程库


