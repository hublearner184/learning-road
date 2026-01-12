# git的理解及使用

## 管理版本

---



记录文件变更

不适合单独管理二进制文件比如word.doc、临时文件、大体积文件。

cd进入某一个文件下，git init创建出.git隐藏文件，管理同级目录下的所有内容

## 基础理解

---

### 文件三种区域

1.工作目录(Working Directory)

2.暂存区(Staging Area)

3.本地仓库(.git directory,Repository)

这里暂存区的作用是让更新更细节，比如修改了三个模块，而只“拍照”一次，可能就会混乱，暂存区就每个模块或修改都存下。

### 文件四种状态

1.Untracked

2.Unmodified

3.Modified

4.Staged

Untracked-->Staged-->Unmodified

Unmodified-->Modified

## 基础命令

---

 在一个工作目录下创建git代理

cd进入工作目录后 git init

git status 查看目录状态

git commit -m “注释” 提交

git log 查看日志

git reset <commitID> 三种模式  但不常用

git reset --hard 不保存所有变更

git reset --soft  保存变更且变更内容处于staged

git reset --mixed 保留变更且变更内容处于modified

## 远程仓库(repository)

---

### 

gitlab常用于内网

github常用于公网开源社区

### 如何在github上提交

1.前置准备：github账号，本地git要配置好用户名和邮箱

2.在目标github项目右上角点击Fork，勾选只要Master分支，将仓库复制到自己的账号下

3.克隆自己Fork的仓库到本地

```
cd
git clone https://github.com/hublearner184/learning-road.git
cd
```

4.创建新分支，避免直接修改主分支

git checkout

5.定位并修复问题

6.特殊项目特殊构建

7.做测试

8.回到本地仓库提交，然后推送到远程仓库

```
git add .
git commit -m "fix:"
git push origin fix-logic-issue
```

![image-20260112144319771](C:\Users\nickname\AppData\Roaming\Typora\typora-user-images\image-20260112144319771.png)

## 配置

1.下载安装

2.配置环境变量 Path

3.修改配置文件

## 链接远程仓库

要将本地代码推送到你创建的 GitHub 远程仓库（`https://github.com/hublearner184/learning-road.git`），按照以下步骤操作：

------

### **步骤 1：初始化本地仓库（如果尚未初始化）**

如果你的项目目录还不是 Git 仓库，先初始化：

```
cd /path/to/your/local/project  # 进入你的项目目录
git init                        # 初始化本地仓库
```

------

### **步骤 2：关联远程仓库**

将本地仓库与你的 GitHub 远程仓库关联：

```
git remote add origin https://github.com/hublearner184/learning-road.git
```

- 

  `origin`是远程仓库的默认名称（可自定义）

- 

  验证是否关联成功：

  ```
  git remote -v
  ```

  应显示：

  ```
  origin  https://github.com/hublearner184/learning-road.git (fetch)
  origin  https://github.com/hublearner184/learning-road.git (push)
  ```

------

### **步骤 3：添加文件到暂存区**

```
git add .                       # 添加所有文件
# 或指定文件
git add file1.txt file2.js      # 添加特定文件
```

------

### **步骤 4：提交更改**

```
git commit -m "Initial commit"  # 提交并添加描述
```

------

### **步骤 5：推送代码到远程仓库**

如果是首次推送（且远程仓库为空）：

```
git push -u origin main         # 推送并设置上游分支
```

- 

  `-u`表示将本地 `main`分支与远程 `main`分支关联，后续可直接用 `git push`

如果遇到错误（如远程仓库有 `README.md`而本地没有）：

```
git pull origin main --allow-unrelated-histories  # 先拉取远程内容
git push origin main                              # 再推送
```

------

### **常见问题解决**

#### 1. 如果 GitHub 仓库非空（如包含 `README`）

```
git pull origin main --allow-unrelated-histories  # 合并远程历史
git push origin main
```

#### 2. 如果提示权限不足

- 

  确保 GitHub 账号已正确配置 SSH 或 HTTPS 认证：

  - 

    **HTTPS**：输入 GitHub 用户名和密码（推荐使用 [Personal Access Token](https://github.com/settings/tokens)替代密码）

  - 

    **SSH**：

    ```
    git remote set-url origin git@github.com:hublearner184/learning-road.git
    git push origin main
    ```

#### 3. 如果分支名称不是 `main`

```
git branch -M main    # 重命名当前分支为 main（如果默认是 master）
git push -u origin main
```

------

### **完整流程示例**

```
# 进入项目目录
cd ~/projects/learning-road

# 初始化仓库
git init

# 关联远程仓库
git remote add origin https://github.com/hublearner184/learning-road.git

# 添加文件并提交
git add .
git commit -m "Initial commit"

# 首次推送
git push -u origin main
```

------

### **验证是否成功**

1. 

   刷新你的 GitHub 仓库页面（https://github.com/hublearner184/learning-road）

2. 

   应该能看到你推送的文件。

