# Contributing Guide

歡迎！跟住呢份指引，大家嘅工作流程先一致。

## Branch 策略

- `main` 永遠係 **production-ready** — 唔可以直接 push、唔可以 force push
- 所有工作由 `main` 開 short-lived branch，命名規則：

```
feat/JIRA-123-add-payment     # 新功能
fix/JIRA-456-login-timeout    # 修 bug
chore/update-dependencies     # 維護
docs/update-readme            # 文件
```

- Branch 存活期唔超過 **3 個工作天** — 太耐就要拆細 task

## Commit 格式（Conventional Commits）

```
feat: 新功能
fix: 修 bug
chore: 維護
docs: 文件
refactor: 重構（唔改行為）
test: 測試
```

Commit message 要講「點解」，唔好淨係講「做咗乜」。

## PR 流程

1. 完成 branch 後開 PR，用 [PR template](.github/PULL_REQUEST_TEMPLATE.md)
2. PR 要夠細 — **超過 400 行 code 要拆**
3. CI 必須全部通過（lint + test + security scan）
4. 至少 **1 人 review 批准** 先可以 merge
5. Merge 用 **squash merge**，保持 main 歷史乾淨

## 安全要求

- ❌ **永遠唔好 commit secrets**（API key、password、token）
- ✅ Secrets 放 `.env`（已 gitignore），production value 問 admin 攞
- ✅ 開 PR 前用 `git diff` 檢查有冇意外 commit 咗敏感資料

## 測試要求

- 新功能一定要有對應測試
- 開 PR 前 local 跑一次測試確認冇 break
