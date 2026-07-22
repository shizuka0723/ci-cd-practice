## CI/CD Pipeline 說明

這個 repo 用來練習 GitHub Actions 的完整 CI/CD 流程,包含:

- Lint 檢查(flake8)
- Matrix 測試(Python 3.10 / 3.11 / 3.12)
- Composite Action(自訂 `.github/actions/setup-python-env`)
- Secrets 管理示範
- 部署到 GitHub Pages(僅 push 到 main 時觸發)
- Container-based 測試環境對照練習

## Pipeline 架構
lint → test(matrix) → deploy
