##git 信息设置
修改开发者信息：
```
git config --global user.name "Your_Name"
git config --global user.email "you@example.com"
```
修改默认编辑器为vim：
```
git config --global core.editor vim
```
##git 合并多个commit
git rebase -i HEAD^n

git commit -a --amend -m "my message here"如果之前有一个提交，并且信息为:
git commit -a -m "my last commit message"

则这个commit message将不存在。但该commit的信息已经合并到"my message here"中了。

第二个是，如果你提交了最后的修改，这时可用：
$ git reset --soft HEAD^ #或HEAD^意为取消最后commit
$ git commit --amend

这将会把最后一个commit合并到前一个提交中去，例如（由上往下读）：
git add b.text
git commit -a -m "my message here"
git add a.text
git commit -a -m "my last commit message"

那么最后存在的将是"my last commit message"。也可后退n个，合并到前面第n+1个commit中去：
$ git reset --soft HEAD~n #后退到第n，我也不清楚具体含义。
$ git commit --amend [-m "new message"]

我觉得最方面的是调用reflog查看操作历史，找到具体的commit id，然后直接git reset --hard [commit_id]就回到你要的版本！

这个是一个同事让我把他的repository若干个commit变成一个，我用git rebase -i合并到最后发现剩下只有两个commit的时候，git rebase -i不再起作用，于是我求助了git maillist,果然很快有人给出了答案:
```
$ git reset --soft HEAD^1
$ git commit --amend
```
