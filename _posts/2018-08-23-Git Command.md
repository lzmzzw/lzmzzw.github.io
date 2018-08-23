---

layout: post
title:  Git命令整理
date:   2018-08-23 10:45:00 +0800
categories: Git
tag: Git Command

---

* content
{:toc}


---------------------------------------



#### 版本库的创建与配置
```
git init                                                    # 初始化本地git仓库（创建新仓库）
git config --global user.name "xxx"                         # 配置用户名
git config --global user.email "xxx@xxx.com"                # 配置邮件
```

#### 版本库添加与提交文件
```
git add file                                                # 添加file文件至暂存区
git add .                                                   # 添加当前所有修改文件至暂存区
git commit -m 'text'                                        # 提交至本地库
```

#### 工作区与版本库状态
```
git status                                                  # 查看当前版本状态
git ls-files                                                # 列出暂存区包含的文件
git log                                                     # 显示提交日志
git log -n                                                  # 显示n行日志
git show xxxxx  (commit id)                                 # 根据commit id前几位查询该提交的详情
git show HEAD                                               # 显示HEAD提交日志
git reflog                                                  # 查询所有的执行的命令
git tag                                                     # 显示已存在的tag
git diff                                                    # 比较工作区与暂存区
git diff --cached                                           # 比较暂存区与仓库 
git diff HEAD^                                              # 比较该版本与上一个版本
git diff origin/master..master                              # 比较远程分支master与本地分支master
git grep "text"                                             # 文件中搜索文本“text”
```

#### 暂存区、版本库管理
```
git reset --hard HEAD^                                      # 回退到上一版本
git reset --hard HEAD                                       # 将当前版本重置为HEAD
git reset --hard xxxxx                                      # 回退到xxxxx（commit id）版本
git checkout -- file                                        # 撤销文件file的修改
git revert xxxxx                                            # 撤销提交xxxxx（commit id）
git rm file                                                 # 删除暂存区中的文件file
git mv file1 file2                                          # 重命名文件file1为file2
git stash                                                   # 暂存当前修改，将工作区置为HEAD状态
git stash list                                              # 查看所有暂存
git stash clear                                             # 清除所有暂存
```

#### 分支管理
```
git branch                                                  # 显示本地分支
git branch branch1                                          # 创建分支branch1
git checkout branch1                                        # 切换到branch1分支
git checkout -b branch1                                     # 创建新分支branch1并切换到branch1
git branch -a                                               # 显示所有分支（含远程库分支）
git branch --merged                                         # 显示所有已合并到当前分支的分支
git branch --no-merged                                      # 显示所有未合并到当前分支的分支
git branch -m branch1 branch2                               # 更改本地分支branch1名称为branch2
git branch -d branch1                                       # 删除分支branch1
git branch -D branch1                                       # 强制删除分支branch1
git show-branch                                             # 显示当前分支历史
git merge branch1                                           # 将branch1分支合并到当前分支
git rebase branch1                                          # 提取branch1的修改并应用到当前分支
```

#### 远程库使用
```
git remote add origin https://github.com/lzmzzw/lzmzzw.github.io.git        # 添加远程库
git clone https://github.com/lzmzzw/lzmzzw.github.io.git    # clone远程仓库到本地
git fetch                                                   # 获取所有远程分支，未merge到本地分支
git pull origin master                                      # 获取远程分支master并merge到当前分支
git merge origin/master                                     # 合并远程master分支至当前分支
git push origin master                                      # 将当前分支push到远程master分支
git push origin :branch                                     # 删除远程仓库的branch分支
git push --tags                                             # 把所有tag推送到远程仓库
```




