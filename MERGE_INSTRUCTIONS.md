# 合并说明 / Merge Instructions

## 重要信息 (Important Information)

功能实现已完成！代码位于两个分支：
1. **feat/quick-fix-menu** - 主要功能分支（推荐使用）
2. **copilot/add-string-manipulation-entry** - 副本分支

## 推送 feat/quick-fix-menu 分支 (Push feat/quick-fix-menu Branch)

```bash
# 1. 确保在正确的分支上
git checkout feat/quick-fix-menu

# 2. 推送到远程仓库
git push origin feat/quick-fix-menu

# 3. 在 GitHub 上创建 PR
# 访问: https://github.com/DevDengChao/StringManipulation/compare/main...feat/quick-fix-menu
```

## 或者使用 GitHub CLI (Or Use GitHub CLI)

```bash
git checkout feat/quick-fix-menu
gh pr create --base main --head feat/quick-fix-menu \
  --title "feat: 添加 Quick Fix 菜单入口以便快速访问 String Manipulation 功能" \
  --body "$(cat PR_GUIDE.md)"
```

## 验证 (Verification)

在创建 PR 前，验证所有文件都已包含：

```bash
git diff main feat/quick-fix-menu --name-status
```

预期输出应该包括：
- `A` (Added) ShowStringManipulationPopupIntention.java
- `M` (Modified) plugin.xml
- `M` (Modified) StringManipulationBundle.properties
- `A` (Added) intentionDescriptions/ShowStringManipulationPopupIntention/description.html
- `A` (Added) IMPLEMENTATION_NOTES.md
- `A` (Added) PR_GUIDE.md

## 本地测试 (Local Testing)

如果需要本地测试，运行：

```bash
./gradlew buildPlugin
# 然后在 build/distributions/ 中找到生成的插件包
```

## 问题排查 (Troubleshooting)

如果遇到推送权限问题：
1. 确认 GitHub 身份验证已配置
2. 确认对仓库有写入权限
3. 尝试使用 SSH 而不是 HTTPS:
   ```bash
   git remote set-url origin git@github.com:DevDengChao/StringManipulation.git
   ```
