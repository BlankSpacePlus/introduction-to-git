# Git和Github学习记录

Git是Linux发明者Linus开发的一款新时代的版本控制系统，应用广泛。<br/><br/>
![在这里插入图片描述](https://github.com/ChenYikunReal/git_learning/blob/master/images/Github.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzg5NjMxOA==,size_16,color_FFFFFF,t_70)
<br/>
这里会试着分享一些自己学习和使用Git/Github/Gitee的一些经验！

## 项目目录
- books： 收集到的相关书籍资料
- exe： Git安装程序exe(Git在国内下载比较麻烦)
- images： Git学习期间的一些图片/截图

## Git与Github相连的基本配置
[真小白入门之Github](https://blog.csdn.net/nmjuzi/article/details/82184818)

## 提交到Github上的通常流程(个人简易版)
### 命令行提交
1. <code>git add .</code>
2. <code>git commit -m "注释"</code>
3. <code>git push -u origin master</code>
### IDEA(PyCharm、CLion、WebStorm等类似)提交
1. VCS → Import into Version Control → Create Git Repository...
2. 选定项目目录点右键 → Git
    1. Repository → Remotes... → + → 添加URL → ...
    2. Add
    2. Commit → Commit Message内容 → Commit按钮
    3. Repository → Push... → Push按钮

## Windows本地看不到.git
<code>.git</code>文件夹是隐藏文件夹，必须设置一下查看隐含文件夹才能看得到！

## DownloadZip和clone到的项目有何不同
据我所知，区别主要就是zip不含.git；而clone到的有.git。

## 解决本地历史和远端仓库历史不一致的方案
通常，比如我们新建一个Github的Repository(带README.md)，本地直接提交就会被<code>rejected</code>……<br/>
这种情况其实也蛮常见的，这就是我上面写到的“暴力提交三步走”的弊端——没考虑本地Git和远端Github的兼容。<br/>
此时，<code>git pull origin master --allow-unrelated-histories</code>命令就显得很香，可以解决此问题，基本屡试不爽！

## 修改Repository语言类型
我们可能会遇到一个非常恶心的问题：Repository语言不是我们期待的……<br/>
比如一个Vue/HTML项目，最后呈现出的是JavaScript；比如一个Java项目因为加了一些C工程代码而变成了CMake……<br/>
此时需要添加.gitattributes文件：<code>\*.\* linguist-language=java</code><br/>
上面的写法比较暴力，但确实挺实用的……

## 查看提交日志
<code>git log</code>这个命令我还是试过的，它能打印出你在这个Git目录下的commit记录。<br/>
如果是Git目录，则可以查看Log：<br/>
![在这里插入图片描述](https://github.com/ChenYikunReal/git_learning/blob/master/images/IncorrectLog.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzg5NjMxOA==,size_16,color_FFFFFF,t_70)
<br/>
如果不是Git目录，则不可以查看Log：<br/>
![在这里插入图片描述](https://github.com/ChenYikunReal/git_learning/blob/master/images/CorrectLog.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzg5NjMxOA==,size_16,color_FFFFFF,t_70)
<br/>
可以查看本地Git的记录

## 查看状态
查看当前仓库的状态可以用<code>git status</code>这个命令，有时候不知道进行到哪一步的话这个命令挺有用的。<br/>
大家可以在提交的每一步进行后使用这个命令看一看仓库状态。

## 分支与合并
说实话，直到写这部分，我还没怎么用过分支与合并，所有的项目基本都是自己来处理，那顺便学一下吧！<br/>
本地做个测试即可，首先需要创建一个本地仓库，我新建一个<code>git_test</code>文件夹，在此目录下使用<code>git init</code>命令可使git_test文件夹含.git文件夹。<br/>
注意此时新建项目的不能直接新建分支，否则会报错：<code>fatal: Not a valid object name: 'master'.</code>，也就是说必须先commit至少一次才行。<br/>
先随便放一个文件进去，再依次输入<code>git add .</code>、<code>git commit -m "测试"</code>，完成初次提交。<br/>
接下来新建分支<code>a_test<code>，命令为<code>git branch a_test</code>。<br/>
使用命令<code>git branch</code>可查看分支情况：
```text
  a_test
* master
```
<code>master</code>表示主干，<code>a_test</code>则是新建的分支，<code>\*</code>表示当前分支<br/>
使用命令<code>git checkout a_test<code>即可切换到a_test分支目录下。<br/>
回到主分支，使用命令<code>git checkout -b b_test</code>可以新建b_test分支并切换过去：
```text
  a_test
* b_test
  master
```
接下来我们该测试合并分支了，切回master，使用命令<code>git merge a_test</code>，如果无冲突则直接合并成功：<br/>
```text
Already up to date.
```
