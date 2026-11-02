# Github Actions 部署如何配置自动更新

::: warning 注意
有问题请通过 `Github Issues` 反馈，感谢。
自动更新不会执行 D1 数据库的 sql 文件，当数据库 schema 变动时，需要手动执行。
:::

1. 打开仓库的 `Actions` 页面，找到 `Upstream Sync`，点击 `enable workflow` 启用 `workflow`
2. 如果 `Upstream Sync` 运行失败，到仓库主页点击 `Sync` 手动同步即可
3. 修改 `Upstream Sync` 的 `schedule` 配置可自定义更新间隔，参考 [cron 表达式](https://crontab.guru/)

## 同步令牌

本仓库的 `Upstream Sync` 使用仓库 Actions Secret `UPSTREAM_SYNC_TOKEN`。创建 fine-grained personal access token，仅选择当前 fork 仓库，授予 `Contents: Read and write` 和 `Workflows: Read and write`（`Metadata: Read-only` 自动添加），然后保存到该 Secret。这样才能同步包含 `.github/workflows/` 变更的上游提交。

令牌到期前需要更新令牌及对应 Secret。配置完成后，在 Actions 中打开 Upstream Sync，选择 main 分支并点击 Run workflow 验证。不要将令牌写入代码。
