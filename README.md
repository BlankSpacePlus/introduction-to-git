# Git和Github学习记录

Git是Linux发明者Linus开发的一款新时代的版本控制系统，应用广泛。<br/><br/>
![在这里插入图片描述](https://github.com/ChenYikunReal/git_learning/blob/master/images/Github.PNG?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80Mzg5NjMxOA==,size_16,color_FFFFFF,t_70)

## 项目目录
- books： 收集到的相关书籍资料
- exe： Git安装程序exe(Git在国内下载比较麻烦)
- images： Git学习期间的一些图片/截图

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

## 神奇的<code>git pull origin master --allow-unrelated-histories</code>命令
通常，比如我们新建一个Github的Repository(带README.md)，本地直接提交就会被<code>rejected</code>……<br/>
这种情况其实也蛮常见的，这就是我上面写到的“暴力提交三步走”的弊端——没考虑本地Git和远端Github的兼容。<br/>
此时，<code>git pull origin master --allow-unrelated-histories</code>命令就显得很香，可以解决此问题，基本屡试不爽！

## 修改Repository语言类型
我们可能会遇到一个非常恶心的问题：Repository语言不是我们期待的……<br/>
比如一个Vue/HTML项目，最后呈现出的是JavaScript；比如一个Java项目因为加了一些C工程代码而变成了CMake……<br/>
此时需要添加.gitattributes文件：<code>*.* linguist-language=java</code><br/>
上面的写法比较暴力，但确实挺实用的……
