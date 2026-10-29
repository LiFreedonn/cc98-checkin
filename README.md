# CC98 每日自动签到 (基于 GitHub Actions)

本项目借助 [cc98-autosign-fast](https://github.com/Anchorite-no/cc98-autosign-fast) 实现 CC98 每日自动签到，并通过浙大 WebVPN 通道保证海外 GitHub Actions 服务器顺畅访问校内网络。

## 部署步骤

### 1. 新建 GitHub 私有仓库
1. 打开 GitHub，点击右上角 `+` -> **New repository**。
2. 仓库名填写 `cc98-checkin`（或者任意你喜欢的名字）。
3. 务必选择 **Private**（私有仓库，防止泄露个人运行记录）。
4. 点击 **Create repository**。

### 2. 配置 GitHub Secrets 密钥
进入刚创建的 GitHub 仓库，依次点击：
`Settings` -> `Secrets and variables` -> `Actions` -> `New repository secret`

依次添加以下 4 个 Secret：
- `WEBVPN_USER`: 浙大统一身份认证账号（学号/工号）
- `WEBVPN_PASS`: 浙大统一身份认证密码
- `CC98_USER`: 你的 CC98 论坛账号
- `CC98_PASS`: 你的 CC98 论坛密码

### 3. 上传工作流文件
将本仓库中的 `.github/workflows/checkin.yml` 提交并推送到 GitHub 仓库的 `main` 分支。

或者直接在 GitHub 网页端创建文件：
1. 点击 **Add file** -> **Create new file**
2. 路径输入 `.github/workflows/checkin.yml`
3. 粘贴工作流文件内容并提交。

### 4. 手动测试运行
1. 进入仓库顶部的 **Actions** 标签页。
2. 左侧选择 **CC98 Daily Check-in**。
3. 点击右侧 **Run workflow** -> 选择 `main` 分支 -> 点击绿色 **Run workflow** 按钮。
4. 等待几秒后展开运行记录，若看到类似如下日志则代表配置成功：
   ```text
   账号1(xxx) 签到成功 · xxx财富值 · 连续 x 天
   ```
