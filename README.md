# Cron Studio

一个纯静态的中文 Cron 表达式生成器。无需框架、依赖、后端或环境变量，可直接部署到 Cloudflare Pages。

## 功能

- 可视化配置分钟、小时、日期、月份、星期字段
- 常用计划预设：每分钟、每 5 分钟、每小时、每天、工作日、每周、每月
- 实时生成标准五段 Cron 表达式
- 支持手动输入 Cron 并进行字段范围校验
- 预览未来 5 次执行时间（使用浏览器本地时区）
- 一键复制，响应式布局
- 所有逻辑在浏览器本地运行，不上传用户输入

## 部署到 Cloudflare Pages

### 方式一：连接 GitHub（推荐）

1. 登录 [Cloudflare Dashboard](https://dash.cloudflare.com/)。
2. 进入 **Workers & Pages → Create → Pages → Connect to Git**。
3. 选择 GitHub 仓库 `Xiong-China/cron2generate` 和 `main` 分支。
4. 配置构建设置：
   - Framework preset：**None**
   - Build command：留空
   - Build output directory：`/`
   - Root directory：留空（仓库根目录）
5. 点击 **Save and Deploy**。

后续推送到 `main` 分支会自动触发部署。

### 方式二：直接上传

在 Cloudflare Dashboard 的 Workers & Pages 中创建 Pages 项目，选择 Direct Upload，将本项目根目录（至少包含 `index.html`）上传即可。

## 本地预览

直接用浏览器打开 `index.html`，或在项目根目录运行：

```bash
python3 -m http.server 8080
```

然后访问 http://localhost:8080。

## Cron 格式说明

本工具生成标准五字段格式：

```text
分 时 日 月 星期
```

星期使用 0–6（周日为 0）。不同调度平台可能采用不同的 Cron 方言（例如是否支持秒字段、星期编号或特殊字符），部署到具体平台前请核对该平台文档。
