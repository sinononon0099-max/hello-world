# hello-world

> 我的第一个 GitHub 仓库 —— 2026-11-14 创建

## 这个仓库是干嘛的

用来练习 Git 和 GitHub 的基本操作：`clone` → `add` → `commit` → `push`。
仓库里的 [cheatsheet.md](cheatsheet.md) 是我整理的常用命令速查表。

## 学习清单

- [x] 注册 GitHub 账号
- [x] 安装 Git 并配置 `user.name` / `user.email`
- [x] 生成 SSH 密钥并添加到 GitHub
- [x] 克隆仓库到本地
- [x] 完成第一次提交并推送
- [ ] 学会开分支、提 Pull Request
- [ ] 用 GitHub Pages 搭一个个人主页

## 常用命令

```bash
git status             # 看当前状态：改了哪些文件、在哪个分支
git add .              # 把改动放进暂存区（准备存档的文件）
git commit -m "说明"    # 提交：生成一个存档点
git push               # 把本地提交推送到 GitHub
git pull               # 拉取远程最新改动
git log --oneline      # 查看提交历史
```

## 目录说明

| 文件 | 用途 |
| --- | --- |
| `README.md` | 仓库首页展示的说明文档（就是你现在看的这个） |
| `.gitignore` | 告诉 Git 哪些文件不要提交（依赖、密钥、日志等） |
| `cheatsheet.md` | Git 常用命令与场景速查 |

---

*Made with ❤️ by [Sinononon0099-MAX](https://github.com/Sinononon0099-MAX)*
