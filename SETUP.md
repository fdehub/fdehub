# 主页维护

主页与贡献动画已发布。当前 Git 凭据没有 `workflow` 权限，因此自动更新配置暂存于 [setup/profile-art.yml](setup/profile-art.yml)。

## 启用每日贡献图更新

1. 登录 `fdehub` 后，[打开已填好内容的工作流创建页](https://github.com/fdehub/fdehub/new/main?filename=.github%2Fworkflows%2Fprofile-art.yml&value=name%3A+Update+contribution+artwork%0A%0Aon%3A%0A++schedule%3A%0A++++%23+Daily+at+04%3A23+in+Asia%2FShanghai.%0A++++-+cron%3A+%2723+20+%2A+%2A+%2A%27%0A++workflow_dispatch%3A%0A++push%3A%0A++++branches%3A+%5Bmain%5D%0A++++paths%3A+%5B%27.github%2Fworkflows%2Fprofile-art.yml%27%5D%0A%0Apermissions%3A%0A++contents%3A+write%0A%0Aconcurrency%3A%0A++group%3A+profile-art%0A++cancel-in-progress%3A+false%0A%0Ajobs%3A%0A++generate%3A%0A++++runs-on%3A+ubuntu-latest%0A++++timeout-minutes%3A+15%0A++++steps%3A%0A++++++-+name%3A+Check+out+profile%0A++++++++uses%3A+actions%2Fcheckout%40v7.0.1%0A%0A++++++-+name%3A+Generate+contribution+snakes%0A++++++++uses%3A+Platane%2Fsnk%2Fsvg-only%40v3.5.0%0A++++++++with%3A%0A++++++++++github_user_name%3A+%24%7B%7B+github.repository_owner+%7D%7D%0A++++++++++outputs%3A+%7C%0A++++++++++++assets%2Fgenerated%2Fsnake.svg%0A++++++++++++assets%2Fgenerated%2Fsnake-dark.svg%3Fpalette%3Dgithub-dark%0A++++++++env%3A%0A++++++++++GITHUB_TOKEN%3A+%24%7B%7B+secrets.GITHUB_TOKEN+%7D%7D%0A%0A++++++-+name%3A+Generate+3D+contribution+calendars%0A++++++++uses%3A+yoshi389111%2Fgithub-profile-3d-contrib%40v0.9.3%0A++++++++env%3A%0A++++++++++GITHUB_TOKEN%3A+%24%7B%7B+secrets.GITHUB_TOKEN+%7D%7D%0A++++++++++USERNAME%3A+%24%7B%7B+github.repository_owner+%7D%7D%0A%0A++++++-+name%3A+Publish+contribution+artwork%0A++++++++run%3A+%7C%0A++++++++++mkdir+-p+assets%2Fgenerated%0A++++++++++cp+profile-3d-contrib%2Fprofile-green-animate.svg+assets%2Fgenerated%2Fcalendar.svg%0A++++++++++cp+profile-3d-contrib%2Fprofile-night-green.svg+assets%2Fgenerated%2Fcalendar-dark.svg%0A++++++++++git+config+user.name+%22github-actions%5Bbot%5D%22%0A++++++++++git+config+user.email+%2241898282%2Bgithub-actions%5Bbot%5D%40users.noreply.github.com%22%0A++++++++++git+add+assets%2Fgenerated%2F%0A++++++++++if+git+diff+--cached+--quiet%3B+then%0A++++++++++++echo+%22Contribution+artwork+is+already+up+to+date.%22%0A++++++++++++exit+0%0A++++++++++fi%0A++++++++++git+commit+-m+%22chore%3A+update+contribution+artwork%22%0A++++++++++git+pull+--rebase+origin+main%0A++++++++++git+push+origin+HEAD%3Amain%0A)。
2. 文件名应为 `.github/workflows/profile-art.yml`。保留预填内容，点击 **Commit changes** 提交到 `main`。
3. 到仓库的 **Actions** 查看 `Update contribution artwork`；首次提交会自动运行，也可点击 **Run workflow** 手动运行。

启用后每天北京时间 04:23 更新（GitHub 调度可能延迟）。仅使用仓库自动提供的 `GITHUB_TOKEN`，无需另填令牌。工作流只提交 `assets/generated/` 下的贡献图。

如果预填链接未生效，在仓库创建 `.github/workflows/profile-art.yml`，将 [配置文件](setup/profile-art.yml) 的完整内容粘贴进去后提交即可。

## 修改介绍和项目

编辑根目录的 `README.md`。项目精选只放非 Fork 仓库；新增项目时先检查仓库的 Fork 标记。

本地目录：`D:\FDEHubHome\fdehub`。
