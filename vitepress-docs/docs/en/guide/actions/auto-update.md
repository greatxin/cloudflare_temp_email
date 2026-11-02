# How to Configure Auto-Update for GitHub Actions Deployment

::: warning Notice
If you encounter any issues, please report them via `GitHub Issues`. Thank you.
Auto-update will not execute SQL files for the D1 database. When the database schema changes, you need to execute them manually.
:::

1. Open the `Actions` page of the repository, find `Upstream Sync`, and click `enable workflow` to enable the `workflow`
2. If `Upstream Sync` fails, go to the repository homepage and click `Sync` to synchronize manually
3. You can customize the update interval by modifying the `schedule` configuration in `Upstream Sync`, refer to [cron expressions](https://crontab.guru/)

## Sync token

This fork uses the repository Actions secret `UPSTREAM_SYNC_TOKEN` for `Upstream Sync`. Create a fine-grained personal access token restricted to this fork, with `Contents: Read and write` and `Workflows: Read and write` (`Metadata: Read-only` is added automatically), then save it as that secret. These permissions allow syncing upstream changes to `.github/workflows/`.

Renew the token and update the secret before expiration. After configuration, open Upstream Sync in Actions, select main, and click Run workflow to verify. Never commit the token.
