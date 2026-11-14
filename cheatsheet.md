# Git 常用命令速查

## 一、日常循环（90% 的时间就干这 5 件事）

```bash
git status                          # 1. 我现在改了啥？
git add .                           # 2. 把改动放进暂存区
git commit -m "做了什么改动"         # 3. 存档（commit message 写清楚"为什么"更好）
git pull                            # 4. 推送前先拉取，避免冲突
git push                            # 5. 上传到 GitHub
```

## 二、查看与对比

| 命令 | 作用 |
| --- | --- |
| `git status` | 工作区状态：哪些文件改了、暂存了 |
| `git diff` | 看具体改了哪几行（还没 add 的） |
| `git diff --staged` | 看已经 add、还没 commit 的改动 |
| `git log --oneline --graph` | 图形化提交历史 |
| `git log -p 文件名` | 看某个文件的修改历史 |
| `git show 提交ID` | 看某一次提交改了什么 |

## 三、撤销与后悔药

```bash
git restore 文件名              # 丢弃工作区改动（危险：改动会丢）
git restore --staged 文件名      # 从暂存区撤出（文件本身不变）
git commit --amend -m "新说明"   # 修改最后一次提交的说明
git reset --soft HEAD~1         # 撤销上一次提交，改动保留在暂存区
git revert 提交ID               # 生成一个"反向提交"来抵消某次提交（安全，推荐）
```

## 四、分支

```bash
git switch -c feat/login     # 新建并切换到 feat/login 分支
git switch main              # 切回 main
git branch                   # 列出本地分支（* 是当前分支）
git merge feat/login         # 把 feat/login 合并进当前分支
git branch -d feat/login     # 删除已合并的分支
```

## 五、远程协作

```bash
git clone 地址               # 克隆到本地
git remote -v                # 查看远程地址
git remote add origin 地址   # 给已有本地仓库添加远程
git pull                     # 拉取 + 合并
git fetch                    # 只拉取不合并（更安全，可以先看 diff）
git push -u origin main      # 第一次推送并建立跟踪关系
```

## 六、场景速查

**提交信息写错了怎么办？**
→ `git commit --amend -m "正确说明"`（还没 push 时用）

**不小心提交了密码 / token？**
→ 立刻去对应平台**吊销**该密钥；然后 `git rm --cached 文件`，提交，再考虑用 `git filter-repo` 清理历史。改历史很麻烦，**预防靠 `.gitignore`**。

**push 被拒绝（rejected）？**
→ 远程有你本地没有的提交，先 `git pull`（必要时解决冲突），再 `git push`。**不要**无脑用 `--force`。

**改完发现想回退到某个旧版本？**
→ `git log` 找到提交 ID → `git checkout 提交ID -- 文件` 只回退某个文件，或 `git revert` 安全回退整个提交。

**什么是冲突（conflict）？**
→ 同一行代码两个人改了不同内容，Git 不知道该用谁的，会在文件里插入 `<<<<<<<` 标记，手动改成最终想要的样子，`git add` 后继续 `commit`。

## 七、配置（一次性）

```bash
git config --global user.name "你的名字"
git config --global user.email "邮箱"
git config --global init.defaultBranch main
git config --global --list        # 查看所有配置
```

## 八、GitHub 网页操作

| 功能 | 在哪 |
| --- | --- |
| 新建仓库 | 右上角 `+` → New repository |
| 提 Pull Request | 仓库页 → Pull requests → New pull request |
| 建 Issue | 仓库页 → Issues → New issue |
| 改个人资料 | 右上角头像 → Settings |
| 管理 SSH 密钥 | Settings → SSH and GPG keys |
| 免费建站 | 仓库 Settings → Pages |

---

> 记不住没关系，用几次就熟了。卡住的时候先跑 `git status`，它会告诉你下一步能干什么。
