## 通过备份个人博客的内容来练习Git的版本控制

### 步骤

1.新建一个文件夹`copies_of_posts_of_my_personal_blog`，该目录下有`_posts`和`PaperWeekly`两个子文件夹

2.打开git bash，进入`copies_of_posts_of_my_personal_blog`目录

3.运行以下命令

```
git init  #初始化，会在文件夹中产生一个.git文件夹
# 通过 git add 命令来实现对指定文件的跟踪
git add PaperWeekly
git add _posts
git 'My Project' > README #在文件夹下新建一个README文件，第一行内容为'My Project'
git status -s #状态简览
#新添加的未跟踪文件前面有 ?? 标记，新添加到暂存区中的文件前面有 A 标记，修改过的文件前面有 M 标记。
#这里由于都是新添加的，所以文件前面都是A，要注意。每次修改文件，都要git add一下，目的是把最新版本重新暂存
```

4.忽略一些中间文件，比如日志文件或者编译过程中的临时文件（本例没有）

```
cat .gitignore  #所有空行或者以 ＃ 开头的行都会被 Git 忽略
*.[oa]   #Git 忽略所有以 .o 或 .a 结尾的文件，一般在编译过程中出现
*~ #忽略所有以~结尾的文件（副本）
# GitHub 有一个十分详细的针对数十种项目及语言的 .gitignore 文件列表，你可以在
# https://github.com/github/gitignore 找到它
```

5.可运行`git diff `查看已更改但未add的文件内容

6.删除README，添加README.md

```
git rm README 
# 删除文件，并且下一次提交时，该文件就不再纳入版本管理了
# 如果不加git，就是简单的手工删除，运行 git status 时就会在 
# “Changes not staged for commit” 部分（也就是 未暂存清单）看到
# 如果删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项 -f

git 'my project' > README.md
git add README.md
```

7.在github上新建同名仓库，并添加SSH key与本地建立连接，参考该[博客](<https://www.jianshu.com/p/c70ca3a02087>)

8.添加`commit`

```
git commit -m "my test1"
#或者你可以利用编辑器编辑
git commit
```

9.添加刚刚创建的仓库的https地址，以进行关联

```
git remote add origin https://github.com/你的用户名/仓库名字.git
```

10.上传本地文件

```
git push -u origin master
```



### Some Tips

1.每次修改完文件都得使用`git add`命令，显得有点麻烦，之后可以在提交时输入`git commit -a -m "your message"`，Git 就会自动把所有已经跟踪过的文件暂存起来一并提交。

