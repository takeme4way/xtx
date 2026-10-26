---
name: git-commit-push-github
description: 提交当前项目到 GitHub 远程仓库 https://github.com/takeme4way/xtx。Use when the user asks to commit and push to GitHub, 提交并推送到 GitHub, or push to xtx repo.
---

# git-commit-push-github

将当前项目提交并推送到 GitHub 远程仓库 `https://github.com/takeme4way/xtx`。

## Steps

1. **检查远程仓库**：运行 `git remote -v`，确认是否已配置名为 `github` 的远程仓库。令牌不写入本文件，仅保存在 `.git/config` 的远程 URL 中。如远程缺失，运行（把 `<GITHUB_PAT>` 换成你的 fine-grained 令牌，需含 Contents:write 权限）：
   ```
   git remote remove github 2>$null
   git remote add github https://<GITHUB_PAT>@github.com/takeme4way/xtx.git
   ```

2. **暂存所有更改**：
   ```
   git add -A
   ```

3. **提交**：
   ```
   git commit -m "update: sync project to GitHub"
   ```
   如果有 hooks 拒绝提交，修复问题后重新提交，不要使用 `--no-verify` 或 `--force`。

4. **推送**：先用 `git branch --show-current` 获取当前分支名，然后：
   ```
   git push -u github <当前分支名>
   ```
   如果推送被拒绝（远程有新提交），先执行 `git pull --rebase github <当前分支名>`，解决冲突后再推送。

5. **验证**：推送成功后，运行 `git status` 确认工作区干净，并告知用户推送结果。

## Notes

- 远程名固定使用 `github`，与 Gitee 的 `origin` 互不干扰，两者可以并存。
- 如果用户提供了自定义提交信息，使用用户的消息而非默认消息。
- 不要跳过 git hooks，不要 force-push，不要创建空提交。
- 令牌已内置于远程 URL 中（存储在 .git/config，不随项目文件提交）。若推送报 401/403，提示用户令牌可能已过期，需要到 GitHub → Settings → Developer settings → Personal access tokens 重新生成。
