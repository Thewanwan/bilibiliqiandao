# BiliBili自动签到工具

基于 [BiliBiliToolPro](https://github.com/RayWangQvQ/BiliBiliToolPro) 的GitHub Actions自动签到版本。

## 功能

- 每日自动签到（登录、投币、点赞、分享）
- 直播间天选时刻抽奖
- 扫码登录获取Cookie

## 使用方法

### 1. Fork本仓库

### 2. 添加Secrets

进入仓库 Settings → Secrets and variables → Actions，添加以下Secrets：

| Secret名称 | 说明 | 是否必填 |
|-----------|------|---------|
| `COOKIE` | B站Cookie字符串 | 必填 |
| `COOKIE2` | 第二个账号Cookie | 可选 |
| `COOKIE3` | 第三个账号Cookie | 可选 |
| `NUMBER_OF_COINS` | 每日投币数量(0-5) | 可选，默认5 |

### 3. 获取Cookie

1. 登录 bilibili.com
2. F12打开开发者工具
3. 切换到 Application → Storage → Cookies
4. 复制所有cookie值，格式如：`uid=xxx; rpdid=xxx; bili_jct=xxx; ...`

### 4. 启用Actions

进入Actions页面，点击"Enable all workflows"

### 5. 运行测试

- 手动运行 `bilibili-login.yml` 测试登录
- 手动运行 `bilibili-daily-task.yml` 测试每日任务

## 定时任务

| 工作流 | 默认时间(北京时间) | 说明 |
|-------|------------------|------|
| bilibili-daily-task | 每天 0:00 | 每日任务 |
| bilibili-live-lottery | 每天 20:00, 02:00 | 直播抽奖 |

修改cron表达式可调整运行时间，建议错开整点避免IP被封。

## 注意事项

- 本工具仅供学习使用
- 请勿滥用，账号风险自负
- 建议设置随机睡眠避免被检测
