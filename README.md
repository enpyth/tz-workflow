# GitHub Actions 时区定时测试

工作流文件：[`.github/workflows/timezone-schedule.yml`](.github/workflows/timezone-schedule.yml)

每天按 **Australia/Adelaide 当地时间**触发三次：

| Adelaide 计划时间 | 日志中的城市时区 |
| --- | --- |
| 11:30 | Sydney (`Australia/Sydney`) |
| 11:35 | Tokyo (`Asia/Tokyo`) |
| 11:40 | New York (`America/New_York`) |

工作流使用 GitHub Actions `schedule.timezone`，因此 Adelaide 的夏令时切换会自动处理。每次运行会打印计划时间、实际开始时的 Adelaide 时间和对应城市时间。三个城市自身的夏令时也由系统时区数据库处理。

将文件放在 GitHub 仓库的**默认分支**后，在 **Actions → Timezone schedule test** 查看运行记录和日志。也可以点击 **Run workflow**，选择 `city` 立即手动验证输出。

GitHub 的定时任务可能排队延迟，极端负载下也可能跳过，因此日志中的实际运行时间不保证恰好是计划分钟。手动运行只验证日志格式，不验证定时触发。
