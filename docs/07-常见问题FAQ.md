# 第 7 章 · 常见问题 FAQ

## push 时要求登录，输密码报错？

GitHub 早已**不支持账号密码方式推送**。解决方法二选一：

1. **HTTPS + 浏览器授权（推荐新手）**：push 时弹出的登录窗口选「Sign in with your browser」，浏览器里授权即可
2. **Personal Access Token**：GitHub → Settings → Developer settings → Personal access tokens → 生成 token，push 时密码栏填 token。记得设过期时间并保存好

## push 报错 `rejected (fetch first)`？

说明远端有更新而你没有先拉取。先拉再推：

```bash
git pull
# 如果提示冲突，解决冲突文件后：
git add .
git commit -m "解决合并冲突"
git push
```

## push 报错 `Authentication failed`？

- 检查邮箱用户名是否和 GitHub 一致：`git config --global --list`
- 用 token 的话检查 token 是否过期
- Windows 上可以在「控制面板 → 凭据管理器」删掉旧的 GitHub 凭据，重新 push 触发登录

## 不小心 commit 了不该提交的文件（比如密码、密钥）？

**还没 push**：撤销最后一次提交（改动会保留）：

```bash
git reset --soft HEAD~1
```

**已经 push 了**：改密码/换密钥是第一优先级，历史是删不干净的（别人可能已经拉取）。

## 文件删错了想恢复？

```bash
# 查看所有操作记录（包括被撤销的）
git reflog

# 回到指定的某一步（abcdef 换成 reflog 里显示的编号）
git reset --hard abcdef
```

## clone 下来的项目运行报错？

常见原因按顺序排查：

1. **没看 README** —— 90% 的答案在里面（需要先装依赖、需要什么运行环境）
2. **依赖没装** —— 看项目语言：Python 找 `requirements.txt`，Node 找 `package.json`
3. **版本不对** —— 项目要求 Python 3.10 你装的是 3.7，这类问题很常见

## 提交的作者显示成一个陌生名字（不是我）？

说明你电脑上的 Git 配置里残留了别人的身份。先查：

```bash
git config --list --show-origin | grep user
```

如果显示的是 `laoxu`、`admin` 之类，说明全局配置被写死了。改成你自己：

```bash
git config --global user.name "你的用户名"
git config --global user.email "你的GitHub隐私邮箱"
```

**已经推上去的提交不会自动变**，需要重写历史（只适合个人仓库，别人也在用的仓库别这么干）：

```bash
# 重写当前分支所有提交的作者
git rebase --root --exec 'git commit --amend --no-edit --reset-author'
git push --force-with-lease
```

## 怎么同步原作者的更新到我的 Fork？

```bash
# 在你 fork 的本地仓库里
git remote add upstream https://github.com/原作者/仓库.git
git fetch upstream
git merge upstream/main
git push
```

也可以直接在 GitHub 上点 fork 仓库页面的 **Sync fork → Update branch**，更简单。

## Star 和 Fork 到底哪个是收藏？

- **Star** = 收藏 + 点赞（进入你的 Stars 列表，随时找回）
- **Fork** = 复制一份到自己账号（想改代码才需要）

新手收藏项目用 Star 就够了。

## 下一章

[第 8 章 · 术语表 →](08-术语表.md)
