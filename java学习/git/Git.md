# 安装

- 从官网下载，默认

- 启动git bash

- 设置

  - ```shell
    $ git config --global user.name "Your Name"
    $ git config --global user.email "email@example.com"
    ```

# 使用

## 版本库

- 在目录下git init使当前文件变为仓库

  - ```shell
    git init
    ```

- 在当前目录下创建一个文本文件，使用git add添加到暂存区，git commit -m "备注信息"添加到本地仓库

  - ```shell
    $ git add 1.txt
    
    //将所有发生改变但不包括删除的文件添加到暂存区
    git add -A . 
    
    ShadowMoon@DESKTOP-V0B375N MINGW64 /d/learngit (master)
    $ git commit -m "wrote a file"
    
    ```

- 修改文件内存后，使用git status查询仓库中文件的状态

  - ```shell
    $ git status
    On branch master
    Changes not staged for commit:
      (use "git add <file>..." to update what will be committed)
      (use "git restore <file>..." to discard changes in working directory)
            modified:   1.txt
    
    no changes added to commit (use "git add" and/or "git commit -a")
    
    ```

- 使用git diff查看修改了什么(查看的是工作区文件和版本库中的有何不同)

  - ```shell
    $ git diff
    diff --git a/1.txt b/1.txt
    index 4219741..533805d 100644
    --- a/1.txt
    +++ b/1.txt
    @@ -1 +1 @@
    -lalal
    \ No newline at end of file
    +lala
    \ No newline at end of file
    
    ```

## 版本回退

- git log [--pretty=oneline] 查看提交日志

  - ```javascript
    $ git log --pretty=oneline
    //head表示当前版本
    //head^为上个版本，head^^为上上个...head~100为上100个
    b1250fa28dc3dcc793a13c766a1e644179f79709 (HEAD -> master) add la
    041774c914d4f3d5731d60a6b81fd875dc8634ce 减l
    f045353f7f6b2f157925bc1fcbcbdc6c7459b54c wrote a file
    
    //回到过去
    $ git reset --hard head^
    HEAD is now at 041774c 减l
    
    //回到过去后，未来被隐藏要使用版本号才能回到未来
    $ git log
    commit 041774c914d4f3d5731d60a6b81fd875dc8634ce (HEAD -> master)
    Author: AFeng <1165875749@qq.com>
    Date:   Sat Jul 10 14:27:31 2021 +0800
    
        减l
    
    commit f045353f7f6b2f157925bc1fcbcbdc6c7459b54c
    Author: AFeng <1165875749@qq.com>
    Date:   Sat Jul 10 14:17:21 2021 +0800
    
        wrote a file
     
    //版本号的前几位就好    
    $ git reset --hard b1250fa28d
    HEAD is now at b1250fa add la
    
    //重启后也可查看每一条命令并可看到版本号
    $ git reflog
    b1250fa (HEAD -> master) HEAD@{0}: reset: moving to b1250fa28d
    041774c HEAD@{1}: reset: moving to head^
    b1250fa (HEAD -> master) HEAD@{2}: commit: add la
    041774c HEAD@{3}: commit: 减l
    f045353 HEAD@{4}: commit (initial): wrote a file
    
    git 1
    
    ```
    
    

## 工作区与暂存区

- 工作区就是我们当前的目录（learngit）

- add是添加到暂存区（stage）中，commit是添加到分支中（master）

  ![工作区与暂存区](D:\Users\ShadowMoon\OneDrive\桌面\新建压缩\java笔记\java学习\git\工作区与暂存区.png)



##　删除撤销

- ```java
  //把工作区的文件撤回到暂存区或版本库中的样子
  $ git checkout -- 1.txt
  
  //从暂存区恢复到工作区（这样就可以使用checkout --将暂存区的东西删除）
  $ git restore --staged 1.txt
  
  //将本地文件删除后导致跟版本库不一致，需要把版本库的也删掉
  $ git status
  On branch master
  Changes not staged for commit:
    (use "git add/rm <file>..." to update what will be committed)
    (use "git restore <file>..." to discard changes in working directory)
          deleted:    test.txt
  
  no changes added to commit (use "git add" and/or "git commit -a")
  
      
  //删除版本库中的文件
  $ git rm test.txt
  rm 'test.txt'
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/learngit (master)
   //提交
  $ git commit -m "rm test.txt"
  [master fed690e] rm test.txt
   1 file changed, 0 insertions(+), 0 deletions(-)
   delete mode 100644 test.txt
  
  ```

## github

### ssh关联

- 查看用户目录中是否有.ssh目录并其目录下有id_rsa`和`id_rsa.pub

  - 没有，使用$ ssh-keygen -t rsa -C "youremail@example.com"来生产，无脑回车

  - ```java
    $ ssh-keygen -t rsa -C "youremail@example.com"
    ```

- 将id_ras.pub中内容复制到github设置中的ssh中去

### 使用

- fork到自己的仓库，clone下来修改，pull request请求接受修改

## 仓库

- ```java
  //进入目录后使用指令将本文件与远程仓库关联（origin是默认远程库的名字）
  $ git remote add origin git@github.com:Wednesday-ph/learngit1.git
      
  //将本地分支master推送到远程仓库。第一次可以使用-u可以分支关联简化命令。
  $  git push [-u] origin master
  The authenticity of host 'github.com (52.74.223.119)' can't be established.
  RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
  This key is not known by any other names
  Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
  Warning: Permanently added 'github.com' (RSA) to the list of known hosts.
  Enumerating objects: 22, done.
  Counting objects: 100% (22/22), done.
  Delta compression using up to 8 threads
  Compressing objects: 100% (9/9), done.
  Writing objects: 100% (22/22), 1.50 KiB | 95.00 KiB/s, done.
  Total 22 (delta 1), reused 0 (delta 0), pack-reused 0
  remote: Resolving deltas: 100% (1/1), done.
  To github.com:Wednesday-ph/learngit1.git
   * [new branch]      master -> master
  Branch 'master' set up to track remote branch 'master' from 'origin'.
  
  //查看远程库信息    
  $ git remote -v
  origin  git@github.com:Wednesday-ph/learngit1.git (fetch)
  origin  git@github.com:Wednesday-ph/learngit1.git (push)
  //根据名字删除（解除关联）
  $ git remote rm origin    
  
  //clone远程仓库    
  $ git clone git@github.com:Wednesday-ph/gitskills1.git
  Cloning into 'gitskills1'...
  remote: Enumerating objects: 3, done.
  remote: Counting objects: 100% (3/3), done.
  remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
  Receiving objects: 100% (3/3), done.
      
      
  

## 分支

- head指向master（分支），master指向提交![分支1](D:\Users\ShadowMoon\OneDrive\桌面\新建压缩\java笔记\java学习\git\分支1.png)

- ```java
  //创建分支并切换等同于git branch dev ; git checkout dev
  $ git checkout -b dev
  Switched to branch 'dev']    
  Switched to a new branch 'dev'
  
  //查看分支
  $ git branch
  * dev
    main
      
  //使用分支    
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (dev)
  $ git add README.md
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (dev)
  $ git commit -m "branch teest"
  [dev 1d526dc] branch teest
   1 file changed, 5 insertions(+), 1 deletion(-)
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (dev)
  $ git checkout master
  error: pathspec 'master' did not match any file(s) known to git
  
      
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (dev)
  $ git checkout main
  Switched to branch 'main'
  Your branch is up to date with 'origin/main'.
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (main)
  //合并分支(fast forward快进，直接将main的指针指向dev)
  $ git merge dev
  Updating 2b1b430..1d526dc
  Fast-forward
   README.md | 6 +++++-
   1 file changed, 5 insertions(+), 1 deletion(-)
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (main)
  //删除分支    
  $ git branch -d dev
  Deleted branch dev (was 1d526dc).
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (main)
  $ git branch
  * main
  
  //新命令    
  切换分支：git switch <name>
  创建+切换分支：git switch -c <name>    
      
  
  ```

- ```java
  /***					冲突				***/
  
  $ git switch -c feature1
  Switched to a new branch 'feature1'
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (feature1)
  $ git branch
  * feature1
    main
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (feature1)
  $ git add README.md
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (feature1)
  $ git commit -m "and simple"
  [feature1 fcbf89a] and simple
   1 file changed, 1 insertion(+), 1 deletion(-)
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (feature1)
  $ git switch main
  Switched to branch 'main'
  Your branch is ahead of 'origin/main' by 3 commits.
    (use "git push" to publish your local commits)
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (main)
  $ git add README.md
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (main)
  $ git commit -m "& simple"
  [main c348975] & simple
   1 file changed, 1 insertion(+), 1 deletion(-)
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (main)
  $ git mere feature1
  git: 'mere' is not a git command. See 'git --help'.
  
  The most similar command is
          merge
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (main)
  //出现冲突    
  $ git merge feature1
  Auto-merging README.md
  CONFLICT (content): Merge conflict in README.md
  Automatic merge failed; fix conflicts and then commit the result.
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (main|MERGING)
  $ git status
  On branch main
  Your branch is ahead of 'origin/main' by 4 commits.
    (use "git push" to publish your local commits)
  
  You have unmerged paths.
    (fix conflicts and run "git commit")
    (use "git merge --abort" to abort the merge)
  
  Unmerged paths:
    (use "git add <file>..." to mark resolution)
          both modified:   README.md
  
  no changes added to commit (use "git add" and/or "git commit -a")
  
  //文件中的内容（<< == >> 标记出不同分支）
  <<<<<<< HEAD
  Creating a new branch is quick & simple.
  =======
  Creating a new branch is quick AND simple.
  >>>>>>> feature1            
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (main|MERGING)
  $ git add README.md
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (main|MERGING)
  $ git commit -m "fix comflict"
  [main 1c0582b] fix comflict
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (main)
  //查看分支合并图            
  $ git log --graph --pretty=oneline --abbrev-commit
  *   1c0582b (HEAD -> main) fix comflict
  |\
  | * fcbf89a (feature1) and simple
  * | c348975 & simple
  |/
  * 4c13a82 reset
  * a0ee3d9 AND simple
  * 1d526dc branch teest
  * 2b1b430 (origin/main, origin/HEAD) Initial commit
              
  
  
  ```

- ```java
              /***					分支管理策略				***/
  //master用来发布，dev用来干活
  //--no-ff禁用fast forward，merge时会创建一个新commit
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (main)
  $ git switch -c dev
  Switched to a new branch 'dev'
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (dev)
  $ git add README.md
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (dev)
  $ git commit -m "add branch"
  [dev 5bb4ba8] add branch
   1 file changed, 1 insertion(+)
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (dev)
  $ git switch main
  Switched to branch 'main'
  Your branch is ahead of 'origin/main' by 6 commits.
    (use "git push" to publish your local commits)
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (main)
  //--no-ff禁用fast forward，merge时会创建一个新commit    
  $ git merge --no-ff -m "merge with no-ff" dev
  Merge made by the 'recursive' strategy.
   README.md | 1 +
   1 file changed, 1 insertion(+)
  
  ShadowMoon@DESKTOP-V0B375N MINGW64 /d/test/gitskills1/gitskills1 (main)
  //查看分支历史    
  $ git log --graph --pretty=oneline --abbrev-commit
  *   053514c (HEAD -> main) merge with no-ff
  |\
  | * 5bb4ba8 (dev) add branch
  |/
  *   1c0582b fix comflict
  |\
  | * fcbf89a and simple
  * | c348975 & simple
  |/
  * 4c13a82 reset
  * a0ee3d9 AND simple
  * 1d526dc branch teest
  * 2b1b430 (origin/main, origin/HEAD) Initial commit
      
              
  
  ```

- 分支策略（master用来发布，在dev上干活）![分支策略](D:\Users\ShadowMoon\OneDrive\桌面\新建压缩\java笔记\java学习\git\分支策略.png)

- ```java
     //bug修复
     
     //git stash将当前工作现场存储起来
     $ git stash
     Saved working directory and index state WIP on dev: fed690e rm test.txt
     
     //存储现场的列表    
     $ git stash list
     stash@{0}: WIP on dev: fed690e rm test.txt
     
     //恢复现场并删除
     $ git stash pop
     On branch dev
     Changes to be committed:
       (use "git restore --staged <file>..." to unstage)
             new file:   hello.py
     
     Dropped refs/stash@{0} (e63be912ae8c2563df6116f08812d8cbcf385d1a)
     
     //恢复指定现场并不删除（可以不指定）
     $ git stash apply stash@{0}
         
     //用于复制修改（master中的错误，它的分支也是有的）
     $ git cherry-pick 54b8770
     [master dac5614] del 12
      Date: Wed Jul 14 13:44:40 2021 +0800
      1 file changed, 1 insertion(+), 1 deletion(-)
       
          
          
     //新功能应该新建一个分支     
     //强制删除已提交的分支
     $ git branch -D dev1
     Deleted branch dev1 (was 1d46979).
          
     ```

## 多人协作

- ```java
  
  
  //查看远程库信息
  $ git remote
  origin
  
  //详细    
  $ git remote -v
  origin  git@github.com:Wednesday-ph/gitskills1.git (fetch)
  origin  git@github.com:Wednesday-ph/gitskills1.git (push)
      
  //推送分支（master、dev必须同步，其他视情况）
  $ git push origin main
  $ git push origin dev
      
  
      
      
      
      
  //抓取分支
  //抓取分支, .git在里面一个文件中    
  $ git clone git@github.com:Wednesday-ph/gitskills1.git
  Cloning into 'gitskills1'...
  remote: Enumerating objects: 26, done.
  remote: Counting objects: 100% (26/26), done.
  remote: Compressing objects: 100% (10/10), done.
  remote: Total 26 (delta 7), reused 23 (delta 7), pack-reused 0
  Receiving objects: 100% (26/26), 2.36 KiB | 301.00 KiB/s, done.
  Resolving deltas: 100% (7/7), done.
      
  //默认只有master主分支，创建远程库的分支
  $ git switch -c dev origin/dev
  Switched to a new branch 'dev'
  Branch 'dev' set up to track remote branch 'dev' from 'origin'.
  
  //同时push
  //有冲突，需要使用git pull拉取下来再合并再推送    
  $ git push origin dev
  To github.com:michaelliao/learngit.git
   ! [rejected]        dev -> dev (non-fast-forward)
  error: failed to push some refs to 'git@github.com:michaelliao/learngit.git'
  hint: Updates were rejected because the tip of your current branch is behind
  hint: its remote counterpart. Integrate the remote changes (e.g.
  hint: 'git pull ...') before pushing again.
  hint: See the 'Note about fast-forwards' in 'git push --help' for details.    
      
  //pull失败，需要与远程库建立连接    
  $ git pull
  There is no tracking information for the current branch.
  Please specify which branch you want to merge with.
  See git-pull(1) for details.
  
      git pull <remote> <branch>
  
  If you wish to set tracking information for this branch you can do so with:
  
      git branch --set-upstream-to=origin/<branch> dev    
  
  
  //建立连接，再pull        
  $ git branch --set-upstream-to=origin/dev dev
  Branch 'dev' set up to track remote branch 'dev' from 'origin'. 
  $ git pull
  Auto-merging env.txt
  CONFLICT (add/add): Merge conflict in env.txt
  Automatic merge failed; fix conflicts and then commit the result.     
      
  //修改冲突，再提交    
      
      
  
  ```

- 

## 标签管理

- ```java
  //git tag<name>打标签，默认head
  git tag v0.9
      
  //git tag 查看标签
  git tag
  v0.9
  
  //git tag<name><Cid>为某次提交打标签
  git tag v0.5 d1d2d2
  
  //git show<tagname>查看标签的信息
  $ git show v0.9
  commit f52c63349bc3c1593499807e5c8e972b82c8f286 (tag: v0.9)
  Author: Michael Liao <askxuefeng@gmail.com>
  Date:   Fri May 18 21:56:54 2018 +0800
  
      add merge
  
  diff --git a/readme.txt b/readme.txt    
  
  //-a指定标签名 -m说明文字
  $ git tag -a v0.1 -m "version 0.1 released" 1094adb
      
      
      
      
      
  //删除本地标签，删除远程库中标签
  $ git tag -d v0.1
  Deleted tag 'v0.1' (was f15b0dd)
  $ git push origin :refs/tags/v0.9
  To github.com:michaelliao/learngit.git
   - [deleted]         v0.9    
      
  //推送单个标签git push origin <tagname>
  $ git push origin v1.0    
  //推送所有标签
  git push origin master --tags   
      
  //查看远程库标签
  git ls-remote --tags origin    
      
  ```

- 

## 自定义git

### 忽略列表

- 创建.gitignore文件并提交到版本库，https://github.com/github/gitignore中有常用规则

- ```java
  //强行添加
  $ git add -f App.class
      
  //查看有什么问题，再第三行
  $ git check-ignore -v App.class
  .gitignore:3:*.class	App.class    
      
  //排除特定文件!
  !App.class    
  ```




# idea中使用

```java
//启用版本控制
- VCS -> Enable -> Git
    
//以上方法不好用
- 将.git删除掉
- 设置 -> version control -> 删除    
    
//将终端设置为linux的sh.exe
- 设置 -> terminal -> shell path 设置成git中的sh.exe    
```

