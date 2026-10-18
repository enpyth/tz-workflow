# GitHub Actions 时区定时测试

工作流文件：[`.github/workflows/timezone-schedule.yml`](.github/workflows/timezone-schedule.yml)

每天按各目标城市的**当地时间**触发三次。以下是 **2026-10-18 Adelaide 时间**的换算：

| Adelaide 时间 | `schedule.timezone` | 目标城市计划时间 |
| --- | --- | --- |
| 11:30 | `Australia/Sydney` | 当天 12:00 |
| 11:35 | `Asia/Tokyo` | 当天 10:05 |
| 11:40 | `America/New_York` | **前一天** 21:10 |

每次运行会打印目标城市计划时间、实际开始时的 Adelaide 时间和目标城市时间。`schedule.timezone` 分别设置为目标城市时区，按照这些城市的夏令时规则触发。Adelaide、东京、纽约的夏令时规则不同，所以东京和纽约的运行时间**不会全年固定在 Adelaide 的 11:35 和 11:40**。纽约当地的计划日期虽然比 Adelaide 早一天，但这三个计划对应的是同一天的 UTC 01:00、01:05、01:10。

将文件放在 GitHub 仓库的**默认分支**后，在 **Actions → Timezone schedule test** 查看运行记录和日志。也可以点击 **Run workflow**，选择 `city` 立即手动验证输出。

GitHub 的定时任务可能排队延迟，极端负载下也可能跳过，因此日志中的实际运行时间不保证恰好是计划分钟。手动运行只验证日志格式，不验证定时触发。
