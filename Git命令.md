# 常用命令：
- git init 
    + 初始化创建仓库
- git status 
    + 查看当前仓库目录所在位置、查看文件状态
- git add 文件名 
    + 给文件添加git管理权限、追踪文件
- git commit 
    + 提交到仓库记录
- git config --global user.email "123456@qq.com"
    + 设置全局用户名
- git config --global user.name "Youer Name"
    + 设置全局密码
- git config --global -l
    + 验证用户配置信息
- git log
    + 查看已经提交的内容（打印日志）

---

# git文件的三种状态
- 已修改
    + 被修改的文件
- 已暂存
    + 等待被提交的文件
- 已提交
    + 提交到本地仓库的文件

> 未追踪状态：Untracked 由于未进入git，不被git管理，所以不属于三种状态里的任何一种。

# git的三个工作区域
- 工作目录
    + 已修改(对应修改的文件)
- 暂存区域
    + 已暂存(通过git add添加的文件)
- git仓库
    + 已提交(git仓库中的文件)

---

# git的工作流
- 工作目录
    + 工作目录中修改或者创建文件
- 暂存区域
    + 暂存文件
- git仓库
    + 找到暂存区的文件，提交更新
> 工作目录中创建或修改文件后。通过git add提交到暂存区，最后通过git commit提交到git仓库。

> ps：git仓库读取文件是从暂存区读取，因此要先git add到暂存区！

# git入门命令扩展
- git add a.txt b.txt
    + 同时添加多个文件到暂存区
### 当你需要添加到暂存区的文件过多的时候：
- git add .
    + 添加所有改动文件及未追踪的文件到暂存区
### 每次进入vim模式需要输入描述很麻烦？
- git commit -m '描述'
    + 合并提交和描述，一部完成操作
### 每次都要输入add命令好麻烦？
- git commit -a -m '描述'
    + 从工作目录提交到暂存区后，再直接从暂存区提交到git仓库
>  git commit -a -m '描述'无法操作未被追踪的文件。需要先git add 。添加到暂存区

## 中文乱码
1. 中文乱码
- git config -global core.quotepath false
2. 编辑描述乱码
    + 进入cmder编辑器setting
    + 找到environment
    + 添加：set LANG=zh-CN.UTF-8

---

# git入门操作第二步
## 删除文件
1. 命令行删除
    + git rm filename         
        * 删除git区域中记录的文件，并且不保存在工作
        目录中
        * 例：git rm a.txt
    + git rm -f(force) filename
        * 强制删除
2. 手动删除工作目录中的文件
    + git rm filename
3. 删除git仓库中的，保留工作目录中的文件
    + git rm --cache filename

> 手动删除流文件，git仓库中会依然存在，删除后，文件依然处在被追中状态，需要使用git rm filename 取消对被删除文件的追踪

> 修改过的文件，在删除的时候会启动git保护机制，会提示某个文件修改后未提交，编辑修改过的文件无法直接删除。如确定必须删除，可使用强制删除！

---
## 移动文件
### 移动文件的妙用
1. 重命名
    1. 直接在工作目录直接修改文件名称
    2. mv old_filename new_filename
        * 移动文件操作后git会自动识别为这步操作为重命名
2. 移动文件
    + git mv file_from file_to
        * 例：git mv a.txt first/a.txt
    
>以上命令相当于一下三条<br/>
>1. mv file_from file_to<br/>
>2. git rm file_from<br/>
>3. git add file_to

>重命名文件原理是：重命名后，先删除原文件，后重新建立重命名后的新文件，且原文件任然存在git仓库，需要git rm filename从git仓库中删除原文件<br/>重命名后的文件会处于未追踪状态，新文件需要重新追踪再提交。<br/>
>ps：重命名后的新文件处于未追踪状态<br/>
>移动文件的操作。相当于重命名文件

## 查看功能
