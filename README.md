# Antigravity-AutoAccept

> 🚀 一键开启 Antigravity 客户端的“全自动无人值守”模式 (YOLO Mode)

这是一个用于 **Antigravity** 客户端的自定义配置文件。通过修改全局权限和执行策略，它可以彻底关闭 AI 代理在执行命令、读写文件时的确认弹窗，实现真正的全自动运行。

## ✨ 特性 (Features)

* **🚫 零弹窗打断**：开启 `CASCADE_COMMANDS_AUTO_EXECUTION_ON`，多步任务连续执行。
* **🔓 终极文件权限**：配置通配符 `read_file(*)` 和 `write_file(*)`，允许跨系统无缝读取和修改文件。
* **💻 终端免审批**：支持 `command(*)` 和 `unsandboxed(*)`，自动运行所有脚本和命令。
* **⚡ 加速执行**：浏览器和产物审查均开启 Turbo 模式，提升整体响应和执行速度。

## ⚙️ 配置文件 (config.json)

你可以直接使用以下配置来覆盖默认设置。

```json
{
  "userSettings": {
    "artifactReviewMode": "ARTIFACT_REVIEW_MODE_TURBO",
    "autoExecutionPolicy": "CASCADE_COMMANDS_AUTO_EXECUTION_ON",
    "browserJsExecutionPolicy": "BROWSER_JS_EXECUTION_POLICY_TURBO",
    "enableTerminalSandbox": false,
    "globalPermissionGrants": {
      "allow": [
        "read_file(*)",
        "write_file(*)",
        "command(*)",
        "unsandboxed(*)"
      ]
    },
    "nonWorkspaceFileAccessPolicy": "AGENT_SETTING_POLICY_ALLOW",
    "queuedMessageDeliveryStrategy": "MESSAGE_DELIVERY_STRATEGY_WHEN_IDLE",
    "remoteControlHostname": "YOUR_HOSTNAME_HERE",
    "useAiCredits": false
  }
}
