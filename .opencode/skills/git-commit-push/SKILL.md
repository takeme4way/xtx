---
name: git-commit-push
description: 提交当前项目到 Gitee 远程仓库 https://gitee.com/xu-tongxin-yan/gaojiwangye_xutx。Use when the user asks to commit and push, 提交并推送项目, or git push to Gitee.
---

# git-commit-push

将当前项目提交并推送到 Gitee 远程仓库 `https://gitee.com/xu-tongxin-yan/gaojiwangye_xutx`。

## Steps

1. **检查远程仓库**：运行 `git remote -v`，确认是否已配置名为 `origin` 的远程仓库。如果未配置或 URL 不匹配，执行：
   ```
   git remote remove origin 2>$null
   git remote add origin https://gitee.com/xu-tongxin-yan/gaojiwangye_xutx.git
   ```

2. **暂存所有更改**：
   ```
   git add -A
   ```

3. **提交**：
   ```
   git commit -m "update: sync project to Gitee"
   ```
   如果有 hooks 拒绝提交，修复问题后重新提交，不要使用 `--no-verify` 或 `--force`。

4. **推送**：
   ```
   git push -u origin master
   ```
   如果推送被拒绝（远程有新提交），先执行 `git pull --rebase origin master`，解决冲突后再推送。

5. **验证**：推送成功后，运行 `git status` 确认工作区干净，并告知用户推送结果。

## Notes

- 如果用户提供了自定义提交信息，使用用户的消息而非默认消息。
- 不要跳过 git hooks，不要 force-push，不要创建空提交。
