---
name: github-publish
description: Push a local git repository to GitHub - create the remote repo if needed, set the remote URL, and push the main branch. Use this when the user wants to upload, publish, push, or share a project folder to GitHub, or when a local git repo has no remote yet.
license: MIT
---

# GitHub 发布技能

把本地项目推到 GitHub。适合：新项目首次上传、已有仓库推更新。

## 什么时候用 / 别用
- 用：用户说「上传 / 发布 / 推到 GitHub」「分享到 GitHub」
- 别用：只写 README / 文案、只生成 token、只改 GitHub 页面设置

## 前置检查（checklist）
- [ ] 项目里有 README.md、LICENSE（建议）
- [ ] 没有密钥 / token 文件（.env、*.pem 等）——先加 .gitignore
- [ ] 已 git init 且有提交（git log 有记录）
- [ ] 分支名 main（git branch -M main）

## 步骤
1. **确认账号**：让用户打开 github.com 看右上角实际账号名（本机是 lib420888-gif，不是 lib420888）
2. **仓库名**：默认小写短横线（harness-skillos）；若用户已建仓库，尊重原名字（大小写敏感！）
3. **建仓库**（二选一）：
   - 浏览器：github.com/new → 填名字 → Public → 不勾 README/.gitignore/license → Create
   - 命令行：gh repo create <name> --public --source=. --remote=origin --push（装了 gh 且已登录）
4. **设远程 + 推送**：
   - git remote add origin https://github.com/<账号>/<仓库名>.git
   - git branch -M main
   - git push -u origin main
5. **验证**：git ls-remote origin 看到 refs/heads/main；浏览器打开仓库页确认文件在

## Gotchas（陷阱清单）
- 账号名可能和口头说的不一样 → 以浏览器右上角实际账号为准（踩过：lib420888 vs lib420888-gif）
- 仓库名大小写敏感：Harness-SKILLOS ≠ harness-skillos
- push 需要网络 + 登录：命令行会弹浏览器登录，或要求 Personal Access Token（不是登录密码）
- 沙箱环境 push 要先批准联网
- 推送前确认没把 .git 或密钥一起传上去

## 验证（怎么算成功）
- git ls-remote origin 返回 refs/heads/main
- 浏览器打开 https://github.com/<账号>/<仓库名> 能看到文件列表和最新提交
