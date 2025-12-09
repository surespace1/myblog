---
title: Git基本用法
date: 2025-10-16 10:02:39Z
lastmod: 2025-10-26 09:15:18Z
tags: [git]
categories: 开发
---

拉取所有远程分支

```bash
git fetch origin
```

将当前分支移动到另一个

```bash
git reset --hard origin/main
```

清理已经被git跟踪过的文件

```bash
git clean -fd
```

**检查本地 Git 配置**

在终端运行 `git remote -v`，查看当前远程 URL 是否正确匹配 GitHub 上的仓库。

如果 URL 错误，移除并重新添加：

```
git remote remove origin
git remote add origin https://github.com/username/repo-name.git  # 替换为您的 URL
```

**处理权限或认证问题**

如果仓库存在但仍报错，可能是认证失败：

- 使用 HTTPS 时，确保有个人访问令牌（PAT）：在 GitHub 设置 > Developer settings > Personal access tokens > Tokens (classic) 生成一个（Scopes: repo），然后在推送时输入用户名和 Token（而非密码）。
- 推荐切换到 SSH：生成 SSH 密钥（`ssh-keygen -t ed25519 -C "your@email.com"`），将公钥（~/.ssh/id_ed25519.pub）添加到 GitHub 设置 > SSH and GPG keys。
- 测试 SSH：`ssh -T git@github.com`（应显示 "Hi username! You've successfully authenticated..."）。

如果是私有仓库，确保您有访问权限（如果是他人仓库，需要被添加为协作者）。

**重新推送**

先拉取远程内容（如果仓库非空）：`git pull origin main --rebase`（假设分支是 main）。

然后推送：`git push -u origin main`。

如果首次推送空仓库，GitHub 可能会提示初始化，但通常直接 push 即可。
