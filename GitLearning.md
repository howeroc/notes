## Git学习笔记

### 常见问题

- windows下push时提示

```bash
$ git push --set-upstream origin master

fatal: I don't handle protocol 'https'
```
- 可用以下命令解决：
```bash
$ git remote set-url origin https://github.com/USERNAME/YOURREPOSITORY.git
```

**名词介绍**
> - 本文以wd代替Working Directory（工作目录）
> - 以repo代替Repository（仓库，即.git文件夹）

- 查看本地链接远程仓库的记录

```bash
git remote -v
```

- 将本地仓库与Github仓库链接

```bash
$ git remode add origin https://github.com/howeroc/notes.git
```

- 跳过stage直接commit修改(不推荐)

```bash
$ git commit -am 'your comment' # 带注释
$ git commit -a # 不带comment
``` 

- 修改最后一次提交的comment

```bash
$ git commit --amend
```

- 撤销修改内容

```bash
$ git checkout -- README.md # 当stage为空时将工作区恢复到Repo的状态，否则恢复到stage的状态
$ git reset --hard HEAD # 功能同上
```
**注意：**
> 以上checkout后的`--`很重要，如果不加`--`就变成了切换分支

- 回退到之前的版本可以用以下命令

```bash
$ git reset --hard HEAD^ # 其中一个`^`代表回退一个版本,两个则代表回退两个版本
$ git reset --hard HEAD~100 # 回退多个版本可以这样写
$ git reset --hard 3224423 # 后边的数字是HEAD的id
```

- 撤销提交

```bash
$ git revert HEAD # 这样就撤销了上次commit的新的commit
$ git revert HEAD^ # 这样就撤销了上上次commit恢复到上上次提交前的版本，如果最近修改和要撤销的修改有重叠则需像merge时一样手动修改冲突
```

**注意：**

> git revert 其实不会直接创建一个提交(commit), 把撤消后的文件内容放到索引(index)里,你需要再执行git commit命令，它们才会成为真正的提交(commit).

- 回退之后要找到之前已经提交的历史可以用以下命令查看:

```bash
$ git reflog
```

- 版本对比

```bash
$ git diff HEAD -- README.md # 用以查看当前版本和工作区最新版本的区别
```

- 删除文件

如果工作目录中删除了一个文件，则也需要提交，用到以下命令：

```bash
$ git rm file.md #这样我们就将删除操作提交到了工作区
$ git checkout -- file.md #如果删错了可以用版本库中的文件进行恢复
```
