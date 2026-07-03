# Git 项目初始化与 GitHub 推送指南

## 背景

你已经完成了以下步骤（本地）：
- ✅ Git 仓库已初始化（`git init`）
- ✅ 用户名/邮箱已配置
- ✅ 初始提交已完成（包含 `.gitignore`）
- ❌ **还未推送到 GitHub**

接下来教你怎么把本地仓库推送到 GitHub 上。

---

## 第一步：生成 GitHub Personal Access Token

由于当前网络环境 SSH 端口被限制，我们需要用 **HTTPS + Token** 的方式推送。

1. 打开 https://github.com/settings/tokens
2. 点击右上角 **"Generate new token (classic)"**
3. 填写一个描述，比如：`local-workbuddy`
4. **权限勾选**：
   - ✅ `repo`（完全控制私有和公开仓库）
   - 其他可以不选
5. 点击页面底部的 **"Generate token"**
6. **立即复制 Token**（关闭页面后就再也看不到了！）

> 💡 这个 Token 相当于你的密码，请妥善保管。

---

## 第二步：创建 GitHub 仓库

1. 打开 https://github.com/new
2. **Repository name** 填写：`git`
3. 选择 **Public**（公开）或 **Private**（私有）
4. ⚠️ **不要勾选** "Initialize this repository with a README"
5. 点击 **"Create repository"**

---

## 第三步：绑定远程仓库并推送

打开终端，依次执行下面的命令（把 `YOUR_USERNAME` 换成你的 GitHub 用户名）：

```bash
git remote add origin https://github.com/YOUR_USERNAME/git.git
git branch -M main
git push -u origin main
```

### 输入认证信息

运行 `git push` 时，会提示你输入：
- **Username**: 你的 GitHub 用户名
- **Password**: 粘贴你刚才生成的 **Token**（不是你的 GitHub 登录密码！）

---

## 验证推送成功

执行以下命令查看远程仓库状态：

```bash
git remote -v
```

如果显示类似下面的内容，说明绑定成功：

```
origin  https://github.com/YOUR_USERNAME/git.git (fetch)
origin  https://github.com/YOUR_USERNAME/git.git (push)
```

---

## 常用后续操作

| 操作 | 命令 |
|------|------|
| 查看状态 | `git status` |
| 添加文件到暂存区 | `git add .` |
| 提交更改 | `git commit -m "描述信息"` |
| 推送到 GitHub | `git push` |
| 拉取最新代码 | `git pull` |
| 查看提交历史 | `git log --oneline` |

---

## 常见问题

**Q: 提示 "remote origin already exists"**
```bash
git remote remove origin
git remote add origin https://github.com/YOUR_USERNAME/git.git
```

**Q: 每次 push 都要输入 Token，太麻烦？**
可以配置 Git 记住凭证：
```bash
git config --global credential.helper cache       # 临时记住（15分钟）
git config --global credential.helper store        # 永久记住（明文存储）
```

> ⚠️ `store` 方式会将凭证明文保存在本地，请在个人电脑上使用。

**Q: 以后想改用 SSH 怎么办？**
```bash
git remote set-url origin git@github.com:YOUR_USERNAME/git.git
```

---

有任何问题随时问我！

