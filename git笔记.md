# 1 GIT命令行操作

## 1.1 本地库初始化
## 1.2 设置签名
## 1.3 基本操作
### 1.3.1 状态查看

 `git status`

### 1.3.2 添加 (到暂存区)

`git add <file name>`

### 1.3.3 提交

`git commit -m "日志" `

### 1.3.4 查看历史版本

`git log`

### 1.3.5 前进后退
* 基于索引值操作 **（推荐）**  
   `git reset --hard "hash值"`
* 使用^符号: 一个 "^" 后退一步   
  `git reset --hard HEAD^` 
* 使用~符号：后退n步  
 `git reset --hard HEAD~n`
### 1.3.6 reset 命令的三个参数对比

*   --soft   在本地库移动head指针	![image-20200310125831457](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200310125831457.png)

*   --mixed 在本地库移动head指针，并重置暂存区![image-20200310130014788](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200310130014788.png)

*   --hard 在本地库移动head指针，重置暂存区，并重置工作区

  ​			

### 1.3.7  比较文件差异

* `git diff [文件名] ` 将工作区文件与暂存区文件比较
* 也可以和之前版本进行比较 `git diff [本地库中历史版本] [文件名]`

## 1.4 分支管理

### 1.4.1 什么是分支

​		在版本控制中使用多条线同时推进多个任务

![image-20200310133140197](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200310133140197.png)

### 1.4.2  分支的好处

* 同时并行 推进多个功能开发
* 如果某一个分支开发失败，不会对其他分支产生影响

### 1.4.3 分支操作

* 创建分支   `git branch [分支名]`
* 查看分支 `git branch -v`
* 切换分支 `git checkout [分支名]`

![image-20200310140209234](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200310140209234.png)

* 合并分支  

  1. 切换到接收修改的分支（被合并，增加新内容）上
  2. 执行`git merge [有新内容文件名]`命令

* 解决冲突

  ![image-20200310162322104](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200310162322104.png)

  1. 删除特殊符号
  2. 修改文件至满意
  3. `git add [文件名]`
  4. `git commit -m "日志"`

![image-20200312151307882](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200312151307882.png)

# 2 本地库与远程库交互方式

## 2.1 在本地库创建远程库地址别名

  `git remote add <name> url`

<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200326151648822.png" alt="image-20200326151648822" style="zoom: 67%;" />

## 2.2 推送

本地 - > 远程  `git push <本地库别名> <分支名>`

## 2.3 克隆

远程 -> 本地 `git clone <ssh/https>`

1. 完整的把远程库下载到本地
2. 创建origin远程地址别名
3. 初始化本地库

## 2.4 远程库修改的拉取（pull = fetch + merge）

`git fetch <远程库名> <分支名>`

`git merge <远程库名/分支名>` 

远程 - > 本地    `git pull <远程库名> <分支名>` 
