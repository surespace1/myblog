---
title: Git 基本用法与常见问题排查
date: 2025-10-16 10:02:39Z
lastmod: 2025-10-26 09:15:18Z
tags: [git]
categories: 开发
---

介绍了 Git 的日常基础操作、强制同步技巧以及常见的远程仓库权限问题解决方案。都是我遇到的问题，所以讲得可能不算是很详细。
<!--more-->

## 基础配置与日常工作流

在使用 Git 之前，首先需要配置用户信息。

1. 初始化配置

```bash
# 设置提交时的用户名和邮箱
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

# 检查配置信息
git config --list
```

2. 提交代码 (Daily Workflow)

```bash
# 1. 查看当前状态（哪些文件被修改了）
git status

# 2. 将修改添加到暂存区 (Staging Area)
git add . 

# 3. 提交到本地仓库
git commit -m "feat: 描述你的修改内容"

# 4. 推送到远程仓库
git push origin main
```

## 同步与清理

1. 拉取所有远程分支

此操作不同步到本地。

```bash
git fetch origin
```

2. 强制覆盖本地代码

将当前分支移动到另一个

```bash
git reset --hard origin/main
```

3. 清理未跟踪文件

注意：此命令用于清理未被 Git 跟踪的文件（Untracked files），而不是已跟踪的文件。通常用于删除编译生成的文件或误添加的临时文件。

-f: 强制删除
-d: 同时删除未被跟踪的空目录

```bash
git clean -fd
```

## 远程仓库配置与权限排查

1. 检查本地 Git 配置

在终端运行 `git remote -v`，查看当前远程 URL 是否正确匹配 GitHub 上的仓库。

如果 URL 错误，移除并重新添加：

```
git remote remove origin
git remote add origin https://github.com/username/repo-name.git  # 替换为您的 URL
```

2. 处理权限或认证问题

如果仓库存在但仍报错，可能是认证失败：

- 使用 HTTPS 时，确保有个人访问令牌（PAT）：在 GitHub 设置 > Developer settings > Personal access tokens > Tokens (classic) 生成一个（Scopes: repo），然后在推送时输入用户名和 Token（而非密码）。
- 推荐切换到 SSH：生成 SSH 密钥（`ssh-keygen -t ed25519 -C "your@email.com"`），将公钥（~/.ssh/id_ed25519.pub）添加到 GitHub 设置 > SSH and GPG keys。
- 测试 SSH：`ssh -T git@github.com`（应显示 "Hi username! You've successfully authenticated..."）。

如果是私有仓库，确保有访问权限（如果是他人仓库，需要被添加为协作者）。

3. 首次推送与冲突解决

如果远程仓库非空（例如在网页端创建时勾选了 README），而本地是新建的仓库，推送时可能会报错。

先拉取远程内容（如果仓库非空）：`git pull origin main --rebase`（假设分支是 main）。

然后推送：`git push -u origin main`。

如果首次推送空仓库，GitHub 可能会提示初始化，但通常直接 push 即可。
