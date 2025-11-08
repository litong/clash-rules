# Clash 规则同步项目

这是一个使用 GitHub Actions 自动同步 [ios_rule_script](https://github.com/blackmatrix7/ios_rule_script) 项目中 Clash 规则文件的项目。

## 🎯 功能特点

- 🔄 **自动同步**: 每天自动从上游仓库同步最新的 Clash 规则文件
- 🎯 **选择性同步**: 只同步指定的文件夹，避免不必要的文件
- 📊 **同步报告**: 生成详细的同步报告，包含文件统计信息
- ⚙️ **灵活配置**: 支持通过配置文件或手动触发来指定同步内容
- 🚀 **一键部署**: 简单的设置即可开始使用

## 📁 项目结构

```
clash-rules/
├── .github/
│   └── workflows/
│       └── sync-clash-rules.yml    # GitHub Actions 工作流文件
├── sync-config.json                 # 同步配置文件
└── README.md                       # 项目说明文档
```

## 🚀 快速开始

### 1. Fork 这个项目

点击右上角的 "Fork" 按钮，将这个项目复制到您的 GitHub 账户。

### 2. 启用 GitHub Actions

1. 进入您 fork 的仓库
2. 点击 "Actions" 选项卡
3. 如果看到提示 "Workflow runs will be disabled", 点击 "Enable workflows"

### 3. 配置同步内容（可选）

编辑 `sync-config.json` 文件来自定义要同步的文件夹：

```json
{
  "folders": [
    "YouTube",
    "Netflix",
    "Disney",
    "HBO",
    "AmazonPrimeVideo",
    "Hulu",
    "ViuTV",
    "BiliBili",
    "TikTok",
    "GoogleFCM",
    "OneDrive",
    "Microsoft",
    "Apple",
    "AppleNews",
    "Game",
    "NetEaseMusic",
    "Spotify",
    "Bahamut",
    "Advertising",
    "Cloudflare",
    "OpenAI",
    "Claude",
    "Gemini",
    "China",
    "Proxy",
    "Global"
  ]
}
```

### 4. 手动触发同步（可选）

1. 进入 "Actions" 选项卡
2. 选择 "Sync Clash Rules" 工作流
3. 点击 "Run workflow" 按钮
4. （可选）输入要同步的特定文件夹，用逗号分隔

## 📋 支持的规则类型

项目默认同步以下 Clash 规则文件夹：

| 文件夹 | 说明 |
|--------|------|
| `Advertising` | 广告拦截规则 |
| `AmazonPrimeVideo` | Amazon Prime Video 流媒体规则 |
| `Apple` | Apple 服务规则 |
| `AppleNews` | Apple News 规则 |
| `Bahamut` | 巴哈姆特（动画疯）规则 |
| `BiliBili` | 哔哩哔哩规则 |
| `China` | 国内网站直连规则 |
| `Claude` | Anthropic Claude 相关规则 |
| `Cloudflare` | Cloudflare 相关域名规则 |
| `Disney` | Disney+ 流媒体规则 |
| `Game` | 游戏服务规则 |
| `Gemini` | Google Gemini 相关规则 |
| `Global` | 国际网站代理规则 |
| `GoogleFCM` | Google FCM 推送规则 |
| `HBO` | HBO Max 流媒体规则 |
| `Hulu` | Hulu 流媒体规则 |
| `Microsoft` | Microsoft 服务规则 |
| `NetEaseMusic` | 网易云音乐规则 |
| `Netflix` | Netflix 流媒体规则 |
| `OneDrive` | OneDrive 云存储规则 |
| `OpenAI` | OpenAI / ChatGPT 相关规则 |
| `Proxy` | 通用代理规则 |
| `Spotify` | Spotify 音乐规则 |
| `TikTok` | TikTok 规则 |
| `ViuTV` | ViuTV 流媒体规则 |
| `YouTube` | YouTube 视频规则 |

## ⚙️ 配置说明

### 自动同步

工作流默认每天凌晨 2 点（UTC）自动运行。您可以在 `.github/workflows/sync-clash-rules.yml` 中修改这个时间：

```yaml
schedule:
  - cron: '0 2 * * *'  # 每天凌晨2点
```

### 同步间隔

Cron 表达式格式：
- `0 2 * * *` - 每天凌晨2点
- `0 */6 * * *` - 每6小时
- `0 0 * * 1` - 每周一午夜

### 排除文件

在 `sync-config.json` 中可以设置要排除的文件模式：

```json
{
  "exclude_patterns": [
    "*.md",
    "*.yaml",
    "*.txt",
    ".git*"
  ]
}
```

## 🔍 查看同步结果

### 同步报告

每次同步完成后，您可以在以下位置查看详细信息：

1. **Actions 页面**: 查看工作流运行状态和日志
2. **Artifacts**: 下载同步报告文件
3. **提交历史**: 查看同步提交的详细信息

### 同步报告内容

同步报告包含以下信息：
- 同步时间
- 同步成功的文件夹列表
- 每个文件夹中的文件数量
- 同步失败的文件夹（如果有）
- 源仓库信息

## 🛠️ 故障排除

### 同步失败

如果同步失败，请检查：
1. 源仓库是否可访问
2. 网络连接是否正常
3. 要同步的文件夹路径是否正确

### 权限问题

确保 GitHub Actions 有权限：
1. 在仓库设置中启用 "Actions"
2. 检查 "Workflow permissions" 设置为 "Read and write permissions"

### 文件冲突

如果本地有修改，同步可能会产生冲突。建议：
1. 在同步前备份重要修改
2. 使用不同的分支进行自定义修改

## 📚 相关链接

- [源项目 - ios_rule_script](https://github.com/blackmatrix7/ios_rule_script)
- [Clash 官方文档](https://github.com/Dreamacro/clash/wiki)
- [GitHub Actions 文档](https://docs.github.com/en/actions)

## 🤝 贡献

欢迎提交 Issue 和 Pull Request 来改进这个项目！

## 📄 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件。