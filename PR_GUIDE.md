# 如何创建 PR (How to Create the PR)

## 背景 (Background)
本次实现为 StringManipulation 插件添加了 Quick Fix 菜单入口，使用户可以通过按 Alt+Enter 快速访问 String Manipulation 功能。

## 分支信息 (Branch Information)
- **功能分支 (Feature Branch)**: `feat/quick-fix-menu`
- **基础分支 (Base Branch)**: `main` 或 `master`

## 推送分支 (Push the Branch)
由于环境限制，需要手动推送 feat/quick-fix-menu 分支：

```bash
git push origin feat/quick-fix-menu
```

## 创建 PR 步骤 (Steps to Create PR)

### 方式一：通过 GitHub 网页 (Via GitHub Web)
1. 访问仓库页面: https://github.com/DevDengChao/StringManipulation
2. 点击 "Pull requests" 标签
3. 点击 "New pull request" 按钮
4. 设置:
   - **base**: `main` (或 `master`)
   - **compare**: `feat/quick-fix-menu`
5. 填写 PR 标题和描述:
   - **标题**: 添加 Quick Fix 菜单入口以便快速访问 String Manipulation 功能
   - **描述**: 参考下方的 PR 描述模板

### 方式二：通过 GitHub CLI (Via GitHub CLI)
```bash
gh pr create --base main --head feat/quick-fix-menu \
  --title "添加 Quick Fix 菜单入口以便快速访问 String Manipulation 功能" \
  --body-file PR_TEMPLATE.md
```

## PR 描述模板 (PR Description Template)

```markdown
## 功能描述

为 StringManipulation 插件添加了 Quick Fix（快速修复）菜单入口，用户现在可以通过按下 Alt+Enter 直接访问所有 String Manipulation 功能。

## 实现细节

### 新增文件
1. **ShowStringManipulationPopupIntention.java**
   - 实现了 `IntentionAction` 和 `PriorityAction` 接口
   - 在编辑器有上下文时始终可用
   - 显示完整的 String Manipulation 弹出菜单
   - 使用 NORMAL 优先级以确保合适的菜单位置

2. **intentionDescriptions/ShowStringManipulationPopupIntention/description.html**
   - 提供用户可见的功能描述

### 修改文件
1. **plugin.xml**
   - 在 extensions 部分注册新的 intention action
   - 归类到 "String Manipulation plugin" 类别

2. **StringManipulationBundle.properties**
   - 添加显示文本: "String Manipulation..."

## 使用方式

1. 在 IntelliJ IDEA 编辑器中打开任意文件
2. 按下 **Alt+Enter** 调出 Quick Fix 菜单
3. 在菜单中找到并选择 "String Manipulation..."
4. 在弹出的菜单中选择需要的文本处理操作

## 测试

- [x] 代码编译通过
- [x] 实现遵循现有的 IntentionAction 模式
- [x] 资源文件正确配置
- [x] 文档完整

## 参考

实现参考了 `ObjectiveCConversionToFromRawStringLiteral` intention 的模式，并与插件现有架构无缝集成。
```

## 文件清单 (File List)

### 新增文件
- `src/main/java/osmedile/intellij/stringmanip/intentions/ShowStringManipulationPopupIntention.java`
- `src/main/resources/intentionDescriptions/ShowStringManipulationPopupIntention/description.html`
- `IMPLEMENTATION_NOTES.md`
- `PR_GUIDE.md` (本文件)

### 修改文件
- `src/main/resources/META-INF/plugin.xml`
- `src/main/resources/messages/StringManipulationBundle.properties`

## 验证清单 (Verification Checklist)

在创建 PR 之前，请确认：
- [ ] 所有文件都已提交到 feat/quick-fix-menu 分支
- [ ] 分支已推送到远程仓库
- [ ] 代码遵循项目的编码规范
- [ ] 添加了适当的文档和注释
- [ ] PR 描述清晰完整
