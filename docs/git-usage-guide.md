# Git 日常操作速查手册

> 适用于本机 Git Bash / PowerShell 的日常使用

---

## 📌 常用命令速查表

### 1. 查看状态
```bash
git status
```
红色 = 未暂存，绿色 = 已暂存，白色 = 已提交。

### 2. 把修改加入暂存区
```bash
git add 文件名          # 添加某个文件
git add .               # 添加所有修改
```

### 3. 提交到本地仓库
```bash
git commit -m "描述信息"
```

> 💡 好的描述格式：
> - `feat: 添加新功能 xxx`
> - `fix: 修复 xxx 问题`
> - `docs: 更新文档`
> - `refactor: 重构 xxx 代码`
> - `chore: 调整配置/杂项`

### 4. 推送到 GitHub
```bash
git push                # 已绑定远程后，直接推
git push -u origin main # 首次推送
```

### 5. 拉取最新代码
```bash
git pull
```

> 推之前建议先 pull，避免冲突

### 6. 查看提交历史
```bash
git log --oneline       # 简洁格式
git log --oneline -5    # 只看最近 5 条
```

---

## 🔁 完整日常流程

### 场景一：创建新文件并推送

```bash
# 1. 创建或修改文件
# （用编辑器改代码、写字等）

# 2. 查看改了什么
git status

# 3. 加入暂存区
git add .

# 4. 提交到本地
git commit -m "feat: 添加 xxx 功能"

# 5. 拉取远程最新代码（避免冲突）
git pull

# 6. 推送到 GitHub
git push
```

### 场景二：编辑已有文件并推送

```bash
git add 修改的文件名
git commit -m "fix: 修复 xxx 问题"
git pull
git push
```

### 场景三：删除文件并推送

```bash
rm 文件名               # 删除文件
git add 文件名          # Git 会识别为删除
git commit -m "chore: 删除无用文件 xxx"
git push
```

---

## 🔧 常用进阶操作

### 撤销修改（未暂存）
```bash
git checkout -- 文件名   # 放弃该文件的修改
```

### 撤销暂存
```bash
git reset HEAD 文件名    # 把文件从暂存区撤回
```

### 撤销最近一次提交
```bash
git reset --soft HEAD~1  # 撤回提交但保留修改
```

### 查看某文件的修改历史
```bash
git log -p -- 文件名
```

### 查看远程仓库地址
```bash
git remote -v
```

### 切换分支
```bash
git branch              # 查看所有分支
git checkout 分支名     # 切换到某分支
git checkout -b 新分支   # 创建并切换到新分支
```

---

## ⚠️ 常见问题

### 1. push 时报错 "rejected"，提示先 pull
```bash
git pull origin main
git push
```
如果 pull 后自动合并了，直接 push。如果有冲突，手动编辑冲突文件，然后再 add → commit → push。

### 2. push 时提示 "could not resolve host github.com"
你的网络无法连接 GitHub，挂上代理/VPN 再试。

### 3. 输入 Token 后提示 "Authentication failed"
- 确认用的是 **Personal Access Token**，不是 GitHub 密码
- Token 可能已经过期，重新生成一个

### 4. 每次 push 都要输入用户名和密码？
```bash
git config --global credential.helper store
```
执行一次后，Git 会记住你的凭证（明文存储在本地文件）。个人电脑可以使用。

### 5. 忘记了远程仓库地址
```bash
git remote -v
```

### 6. 上传了不该传的文件怎么办？
```bash
echo "文件名" >> .gitignore
git add .gitignore
git commit -m "chore: 更新 .gitignore"
git push
```
但这不会删除 GitHub 上已经上传的文件。未来不再跟踪该文件即可。

---

## 📂 文件状态示意图

```
工作区 (Working Directory)
     ↓ git add
暂存区 (Staging Area / Index)
     ↓ git commit
本地仓库 (Local Repository)
     ↓ git push
远程仓库 (Remote / GitHub)
```

---

## 💡 小技巧

1. **Git Bash 支持鼠标右键粘贴**，按右键就能粘贴文本
2. **Tab 键补全文件名**，按 Tab 自动补全，再按继续切换
3. **命令历史**，按 `↑` 键快速调用之前输入过的命令
4. **简洁提交**，一次 commit 只做一件事，描述写清楚
5. **勤提交**，改多少就提交多少，不要攒一大堆再提交

---

更多问题随时问我！

