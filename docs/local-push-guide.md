# 本地推送到 GitHub 指南

## 当前状态确认

你的本地仓库已经是就绪状态：
- ✅ 用户名已配置 (`ao-syz`)
- ✅ 邮箱已配置 (`1614357426@qq.com`)
- ✅ 远程仓库已绑定 (`https://github.com/ao-syz/git.git`)
- ✅ 2 条提交记录已经准备好推送

---

## 第一步：确认 GitHub 仓库已创建

在浏览器打开：https://github.com/ao-syz/git

如果看到仓库页面，说明仓库已存在。

如果看到 **404** 页面，说明仓库还不存在，需要你先手动创建：
1. 打开 https://github.com/new
2. **Repository name** 填 `git`
3. **Description** 可填可不填
4. 选择 **Public**（公开）或 **Private**（私有）
5. ⚠️ **不要勾选** "Initialize this repository with a README"
6. 点击 **"Create repository"**

---

## 第二步：在本机命令行推送

打开 PowerShell 或 Git Bash，执行以下命令：

```powershell
cd C:\Users\16143\Desktop\git
git push -u origin main
```

系统会提示你输入用户名和密码：

```
Username for 'https://github.com': ao-syz
Password for 'https://ao-syz@github.com':
```

### 输入说明
- **Username**: 输入 `ao-syz`
- **Password**: **不要输入你的 GitHub 登录密码！** 而应该输入你的 **Personal Access Token**

---

## 第三步：获取 Personal Access Token

如果你还没有 Token，按下面步骤生成：

1. 打开 https://github.com/settings/tokens
2. 点击右上角 **"Generate new token (classic)"**
3. **Note** 填一个描述，比如 `local-push`
4. **Expiration** 选择有效期（建议选 30 天或更长）
5. **权限勾选**：
   - ✅ **repo** — 用于推送仓库代码
6. 点击页面底部 **"Generate token"**
7. ⚠️ **立即复制 Token**（关闭页面后就再也看不到了！）

然后回到命令行，把 Token 粘贴到 Password 提示处。

> 💡 **注意**：Token 粘贴时不会显示任何字符，这是正常的，直接按回车即可。

---

## 完整示例对话

```
PS C:\Users\16143\Desktop\git> git push -u origin main
info: please complete authentication in your browser...
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 7 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/ao-syz/git.git
 * [new branch]      main -> main
Branch 'main' set up to track 'origin/main'.

PS C:\Users\16143\Desktop\git>
```

推送成功！🎉

---

## 推送后验证

打开以下链接查看你的代码：

**苹果文档**：https://github.com/ao-syz/git/blob/main/apple.md

**所有文件**：https://github.com/ao-syz/git

---

## 以后日常推送流程

有新增或修改时：

```bash
# 1. 查看修改了哪些文件
git status

# 2. 把所有修改加入暂存区
git add .

# 3. 提交（写清楚改了什么）
git commit -m "这里是本次修改的描述"

# 4. 推送到 GitHub
git push
```

---

## 常见问题

### ❓ "remote origin already exists" 怎么办？
不用管它，说明远程已经绑定了，直接执行 `git push -u origin main` 即可。

### ❓ 提示 "could not resolve host github.com"
说明你的网络无法访问 GitHub。**用代理/VPN**，或者换个网络环境再试。

### ❓ 提示 "Authentication failed"
- 确认你输入的是 **Token**，不是 GitHub 登录密码
- Token 可能过期了，去 GitHub 重新生成一个

### ❓ 每次 push 都要输入用户名和 Token？
可以配置 Git 记住凭证：

```bash
# 方式一：临时记忆（15分钟）
git config --global credential.helper cache

# 方式二：永久存储（明文保存在本地，个人电脑用）
git config --global credential.helper store
```

> ⚠️ `store` 方式会将凭证明文保存在 `~/.git-credentials` 文件中，只在个人电脑上使用。

### ❓ 忘记 Token 了怎么办？
去 https://github.com/settings/tokens 重新生成一个。旧 Token 看不了，只能重新生成。

---

如果你成功推送了，告诉我一声！如果遇到其他问题也可以发给我看看。

