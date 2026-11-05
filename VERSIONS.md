# 版本记录

> 规则见 [AGENTS.md](AGENTS.md)。一句话原则：**稳定版负责保底，优化版负责探索，用户验收决定是否升级。**

## 当前稳定版本

**`v1.0-stable`** · 2026-11-05 · 已验收

- 提交：`git rev-list -n1 v1.0-stable`
- 分支：`stable`（永远指向最近一次验收通过的版本）
- 标签：`v1.0-stable`（annotated tag，永不删除）

### 这一版包含

- 手势控制的 3D 圣诞树（Three.js r160 + MediaPipe Hands 0.10）
- 11 张照片，**按原比例显示**，无拉伸 / 无压扁 / 无裁切
- 三档图片：`thumb` 512px(q90) / `mid` 1024px(q88) / `full` 1920px(q86)，共 3.6MB
- 原始照片（58.5MB）保留在 `assets/photos/orig/`，**只有按 O 才下载**
- 标题「你的名字，璀璨如星」+ 署名「really luv u」
- 手势教程、翻页、O 看原图、缓存 v4

> 注：本 tag 打在「已验收代码 + 规则文档」这一提交上，代码与该次验收时完全一致。

### 恢复这一版

```bash
git reset --hard v1.0-stable
git push --force origin main
```

---

## 版本表

| 版本 | 日期 | 状态 | 主要内容 | 回滚点 |
|---|---|---|---|---|
| v1.0-stable | 2026-11-05 | ✅ 已验收 | 手势 3D 树 + 11 张照片；比例修复；三档图片加载；O 看原图 | tag `v1.0-stable` / 分支 `stable` |

<!-- 新版本往上加一行，不要把旧的删掉 -->

---

## 升级流程（摘要）

1. `git describe --tags --abbrev=0` 确认基准
2. `git switch -c iter/<主题> v1.0-stable`
3. 在分支上改 → 跑《AGENTS.md》第五节的回归清单 → 记录实测数据
4. **停下等验收**，main 不动
5. 验收通过：合入 `main` → `git tag -a v1.1-stable -m "..."` → 更新本文件 → 推送
6. 不通过：`git branch -D iter/<主题>`，main 一动不动

版本号：小优化 `v1.x`，重大升级 `v2.0`，纯修 bug `v1.x.y`。
