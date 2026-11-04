# 第 2 章 · 注册账号与安装 Git

## 注册 GitHub 账号（5 分钟）

1. 打开 [github.com](https://github.com)，点击右上角 **Sign up**
2. 填写邮箱（建议用能长期收件的邮箱）、密码、用户名
3. 邮箱里收一封验证邮件，点确认链接

**用户名要认真取**：它会出现在你所有仓库的网址里（`github.com/你的用户名/仓库名`），以后可能印在简历上。建议用拼音或英文，别用数字串。

**强烈建议做的两件事**：

- 去 [Settings → Emails](https://github.com/settings/emails) 确认邮箱已验证，否则后面的很多操作会受限
- 开启两步验证（2FA）：Settings → Password and authentication，用手机验证器 App 扫码绑定。现在 GitHub 强制要求开发者账号开启 2FA，早晚都要弄

## 安装 Git

Git 是你电脑上管理代码版本的软件，推代码必须装。

### Windows

去 [git-scm.com/downloads](https://git-scm.com/downloads) 下载 Windows 版，一路点 Next 即可。默认选项就够了，唯一建议勾上的是 **"Add Git Bash to context menu"**（右键菜单里有 Git Bash，以后会用得爽）。

### macOS

打开「终端」执行：

```bash
git --version
```

如果没装过，系统会弹窗引导你安装。装过就会显示版本号，说明已经有了。

### 验证安装成功

打开终端（Windows 上是 Git Bash）：

```bash
git --version
# 显示 git version 2.x.x 就是成功了
```

## 首次配置：告诉 Git 你是谁

每次提交代码，Git 都要记录「这是谁提交的」。先设置你的名字和邮箱（**邮箱要和 GitHub 注册邮箱一致**，这样提交才会关联到你的 GitHub 头像）：

```bash
git config --global user.name "你的英文名或拼音"
git config --global user.email "你的GitHub注册邮箱"
```

验证配置：

```bash
git config --global --list
```

**这一步千万别跳过。** 很多人的电脑上早就有别人（或某个教程）留下的 `user.name`，比如 `laoxu`、`admin`、`user`，配置一次都没检查过。后果是：你以后所有的提交，作者都显示成那个陌生的名字，GitHub 上不会有你的头像，贡献图也不会变绿——白干了。

看到名字不对就重新执行上面两条 `git config --global` 命令覆盖即可。

### 邮箱该填哪个？

GitHub 现在默认隐藏真实邮箱，推荐用它给你的隐私邮箱：打开 [Settings → Emails](https://github.com/settings/emails)，找到形如 `12345678+你的用户名@users.noreply.github.com` 的那串地址，填这个就行。既能把提交关联到你账号，又不会暴露真实邮箱。

想知道自己现在的提交到底是谁？在仓库目录执行：

```bash
git log -3 --pretty="%h | %an <%ae> | %s"
```


## 【国内用户】先解决访问问题

GitHub 在国内的访问速度不稳定，如果你打开 github.com 很慢或图片加载不出来，先看 [第 6 章 · 国内加速与实用插件](06-国内加速与实用插件.md)，装好插件再回来继续。

## 下一章

[第 3 章 · 看懂仓库页面 →](03-看懂仓库页面.md)
